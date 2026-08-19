# Moje nákupy – PWA + Google Drive

Táto verzia obsahuje:

- foldery (napr. Krakow, Praha, Londýn)
- nákupné položky a sumy
- meny EUR, CZK, PLN, GBP, USD
- prepočet na EUR
- export/import jedného foldera cez JSON
- localStorage pre offline lokálne dáta
- pripojenie Google Drive
- manuálne načítanie a uloženie všetkých dát
- po prvom manuálnom načítaní/uložení automatické ukladanie ďalších zmien počas aktívnej Google relácie

## Google Drive

Aplikácia vytvorí na tvojom Google Drive:

    Moje nakupy/
      data.json

Používa OAuth scope:

    https://www.googleapis.com/auth/drive.file

Týmto scope aplikácia pracuje s Drive súbormi/priečinkami, ktoré vytvorila alebo ktoré jej používateľ sprístupnil.

## Nastavenie Google Cloud

1. V Google Cloud Console vytvor alebo vyber projekt.
2. Zapni Google Drive API.
3. V Google Auth Platform nastav Branding.
4. V Audience:
   - pre osobný Gmail vyber External,
   - ak je aplikácia v režime Testing, pridaj svoj Google účet medzi Test users.
5. V Clients vytvor OAuth 2.0 Client:
   - Application type: Web application
   - Authorized JavaScript origins:

         https://martin-magi.github.io

   - Redirect URI pre tento browserový token flow nepotrebuješ.
6. Skopíruj Client ID, napr.:

       1234567890-abc123.apps.googleusercontent.com

## Ako vložiť Client ID

Máš dve možnosti.

### A) Bez úpravy kódu

Po otvorení aplikácie vlož Client ID priamo do poľa v karte Google Drive.
Uloží sa do localStorage tohto zariadenia.

### B) Natrvalo pre všetky zariadenia

Otvor `config.js` a nastav:

    window.APP_CONFIG = {
      GOOGLE_CLIENT_ID: "SEM_VLOZ_CLIENT_ID.apps.googleusercontent.com"
    };

Potom commitni zmenu na GitHub.

## GitHub Pages

Nahraj obsah ZIP-u do rootu repozitára `List`.

GitHub Pages:

- Settings
- Pages
- Deploy from a branch
- main
- /(root)

Aplikácia:

    https://martin-magi.github.io/List/

## Synchronizácia

Po pripojení Google Drive:

- `Načítať z Disku` prepíše lokálne dáta obsahom `data.json`.
- `Uložiť na Disk` prepíše `data.json` aktuálnymi lokálnymi dátami.
- po prvom manuálnom načítaní alebo uložení sa ďalšie lokálne zmeny v aktuálnej Google relácii ukladajú automaticky.
- ak Google access token vyprší, aplikácia požiada o nové pripojenie.

Export/import jednotlivého foldera zostáva zachovaný ako záloha a manuálny prenos.
