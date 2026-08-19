# Moje nákupy – PWA

Jednoduchá PWA pre GitHub Pages.

## Funkcie

- vytváranie folderov (napr. `Krakow`)
- pridávanie a odoberanie nákupov
- meny: EUR, CZK, PLN, GBP, USD
- súčet podľa jednotlivých mien
- celkový prepočet do EUR
- automatické načítanie najnovšieho dostupného referenčného kurzu
- posledný kurz sa uloží do localStorage pre offline použitie
- všetky nákupy sa ukladajú lokálne v zariadení cez localStorage

## Nasadenie do existujúceho GitHub Pages repozitára `List`

Nahraď obsah repozitára týmito súbormi:

- `index.html`
- `manifest.json`
- `service-worker.js`
- `icon-192.png`
- `icon-512.png`
- `.nojekyll`

GitHub Pages:
- Settings → Pages
- Source: Deploy from a branch
- Branch: main
- Folder: /(root)

Potom otvor:
`https://martin-magi.github.io/List/`

## Poznámka ku kurzom

Aplikácia používa verejné API Frankfurter v2. Ide o najnovšie dostupné referenčné kurzy, nie garantovaný kurz tvojej banky alebo platobnej karty.
