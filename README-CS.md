# Podklady pro zveřejnění soukromí a app-ads.txt

**Stav 11. října 2026:** vlastník nahrál původní soubory do `Damiere/damiere.github.io` a GitHub Pages deployment uspěl. Web, `privacy.html` a `app-ads.txt` byly ověřeny přes HTTPS (HTTP 200). Následně byl místní `privacy.html` upřesněn o stabilní ID instalace a chybovou diagnostiku Expo a o volitelný formát celoobrazovkových reklam; tato nová revize ještě nebyla veřejně ověřena ani publikována agentem. Skutečná privacy URL `https://damiere.github.io/privacy.html` je uložená v EAS prostředích preview i production a ignorovaném `.env.local`. Vlastník oznámil dokončení App Privacy dotazníku včetně odebrání vlastního marketingu; publikování odpovědí zatím nebylo potvrzeno. Schválení reklam Googlem nebylo ověřeno.

Pro tuto aktualizaci stačí v existujícím repozitáři `Damiere/damiere.github.io` nahradit pouze kořenový `privacy.html` stejnojmenným souborem z této složky a potvrdit změnu. Po dokončení GitHub Pages deploymentu zkontrolovat veřejnou URL a nové odstavce o Expo a reklamních formátech. Ostatní soubory webu není potřeba znovu nahrávat.

Před použitím pro vydání potvrď skutečného provozovatele (v textu Jaroslav Pultar podle Apple účtu), kontaktní e-mail, použitá SDK, jejich zpracovatelské podmínky, dobu uchování podpory a soulad s vyplněnými údaji App Privacy v App Store Connect. Text vychází z aktuálního kódu a dokumentace poskytovatelů; dostupnost webu nepředstavuje potvrzení právní úplnosti.

`index.html` je kontakt/podpora, `privacy.html` obsahuje anglické a české zásady. Stránky neobsahují vlastní analytické skripty, formuláře, externí fonty ani herní obrázky. `app-ads.txt` používá publisher ID odvozené z dodaných iOS AdMob ID; jeho řádek porovnej s **AdMob → Apps → View all apps → app-ads.txt → How to set up app-ads.txt**. Pokud web už nějaký app-ads.txt má, přidej náš řádek ke stávajícím.

## GitHub Pages s adresou v kořeni domény

Pro účet **Damiere** použij uživatelský web, tedy samostatný repozitář **`damiere.github.io`**. Jeho web běží v kořeni domény, kam Google hledá `app-ads.txt`. Samotný projektový web pod `/forever-planner/` tento soubor v kořeni domény nezajistí.

1. V GitHubu zvol **New repository**, Owner **Damiere**, Repository name **damiere.github.io**, visibility **Public**, zapni README a vytvoř repozitář. Pokud už tento repozitář používáš pro jiný web, zapracuj soubory do něj se zachováním stávajícího obsahu.
2. Přes **Add file → Upload files** nahraj **obsah** této složky: `index.html`, `privacy.html`, `app-ads.txt`, `.nojekyll`. Soubory musí být přímo v kořeni nového repozitáře, nikoli uvnitř další složky `privacy-site`.
3. **Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: main → /(root) → Save**.
4. Po úspěšném Pages deploymentu otevři skutečně zveřejněné adresy. Pro tento účet budou očekávané adresy `https://damiere.github.io/`, `https://damiere.github.io/privacy.html` a `https://damiere.github.io/app-ads.txt`. Před použitím je ověř v prohlížeči; tento návod netvrdí, že již existují.

Nastavení větve a kořenové složky popisuje [GitHub — zdroj publikování](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

GitHub Pages je dostupné pro veřejné repozitáře v GitHub Free. Zdroj: [GitHub — vytvoření Pages webu](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site). Pokud používáš jiný GitHub účet, název repozitáře i hostitel musí odpovídat jeho přihlašovacímu jménu.

## Zapojení až po zveřejnění

- **Expo:** ověřená HTTPS adresa `https://damiere.github.io/privacy.html` je nastavená do `EXPO_PUBLIC_PRIVACY_POLICY_URL` v EAS prostředích preview a production. Budoucí buildy/aktualizace pak budou obsahovat tento odkaz. Samotné nastavení proměnné nezmění už nainstalovanou aplikaci.
- **App Store Connect:** root webu použij jako **Marketing URL / Developer Website**, `index.html` jako Support URL a `privacy.html` jako Privacy Policy URL. Zkontroluj App Privacy podle použitých SDK, zejména nákupní historii RevenueCat a údaje Google Mobile Ads.
- **AdMob:** **Privacy & messaging → European regulations → Create / Create message**. Vyber iOS aplikaci Forever Planner, nastav jazyky a volbu odmítnutí souhlasu, přidej zveřejněnou privacy URL, zkontroluj návrh a publikuj. V příštím TestFlight buildu bude vlastní iOS AdMob App ID a testovací banner; souhlas je potřeba ověřit na zařízení.
- **app-ads.txt:** ověření Googlu potřebuje veřejný záznam v App Store s developer website. TestFlight odkaz tuto veřejnou stránku nenahrazuje. Po zveřejnění aplikace ji spoj s obchodem v AdMob a ověř stav souboru a app readiness.

Zdroje: [Google — app-ads.txt](https://support.google.com/admob/answer/9363762?hl=en), [formát řádku Google](https://developers.google.com/admob/android/next-gen/app-ads), [Google — consent zpráva](https://support.google.com/admob/answer/10113207?hl=en), [Google — údaje pro App Privacy](https://developers.google.com/admob/ios/privacy/data-disclosure), [RevenueCat — App Privacy](https://www.revenuecat.com/docs/platform-resources/apple-platform-resources/apple-app-privacy), [Expo — soukromí](https://expo.dev/privacy).
