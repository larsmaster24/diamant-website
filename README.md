# Chinees Restaurant Diamant — website

Eén-pagina website voor Chinees Restaurant Diamant, Slimstraat 29, Udenhout.
Volledige afhaalkaart, menu's & rijsttafels, openingstijden en belknop.

Statische site: `index.html` is volledig zelfstandig (CSS, JS en foto's inline).
Gehost via GitHub Pages.

Herontwerp-voorstel ter vervanging van de oude site diamantudenhout.nl.

## Prijzen zelf aanpassen via Google Sheets

De eigenaar kan prijzen (en gerechtnamen) aanpassen zonder de website-code
aan te raken, via een gekoppeld Google Sheet. Eenmalig instellen:

1. Maak een Google Sheet met kolommen `nummer`, `naam`, `prijs`.
   Importeer `menu-prijzen-sjabloon.csv` uit deze repo als startpunt —
   die bevat het huidige menu (Bestand → Importeren in Google Sheets).
2. Bestand → Delen → Publiceren op internet → kies het tabblad met het
   menu → formaat "Kommagescheiden waarden (.csv)" → Publiceren.
3. Kopieer de gepubliceerde link en plak die bij `MENU_SHEET_CSV_URL`
   bovenaan het `<script>`-blok in `index.html`. Commit & push.

Daarna past de eigenaar alleen nog cellen aan in het Sheet:
- Een prijs wijzigen: cel in de kolom `prijs` aanpassen.
- Een lege cel in `prijs` of `naam` laat de bestaande waarde op de site
  ongewijzigd (dus je hoeft niet elke rij volledig in te vullen).
- Een `nummer` dat niet op de site voorkomt wordt genegeerd; een gerecht
  op de site zonder rij in het Sheet houdt gewoon zijn huidige prijs.

Wijzigingen in het Sheet zijn na een paginaverversing zichtbaar op de
site — geen GitHub, geen code, geen "deploy" nodig. Zolang
`MENU_SHEET_CSV_URL` leeg is (de standaardstand) gebeurt er niets en is
de hardgecodeerde kaart in `index.html` gewoon de bron.

Nieuwe gerechten toevoegen/verwijderen of prijzen van de menu's &
rijsttafels (`#menus`) wijzigen gaat nog altijd via `index.html` zelf —
dat valt buiten deze koppeling.
