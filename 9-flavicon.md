# Flavicon

Favicon on pieni kuvake (yleensä 16×16 px tai 32×32 px), joka näkyy selaimen välilehdessä, kirjanmerkeissä ja selaimen osoitepalkissa ja auttaa tunnistamaan verkkosivun visuaalisesti.

Faviconille voi käyttää useita tiedostomuotoja, mutta yleisimmät ovat `.ico` (perinteinen), `.png` 32x32px ja 16x16px (parempi laatu) ja `.svg` (skaalautuva).

## Lisäys HTML-koodiin head-elementtiin

Lisää yksi tai useampi seuraavista. Selain valitsee sopivan, jota tukee.

```js
  <!-- Perinteinen favicon -->
  <link rel="icon" type="image/x-icon" href="favicon.ico">

  <!-- PNG favicon -->
  <link rel="icon" type="image/png" sizes="16x16" href="favicon-16x16.png">
  <link rel="icon" type="image/png" sizes="32x32" href="favicon-32x32.png">

  <!-- SVG favicon (nykyiset selaimet) -->
  <link rel="icon" type="image/svg+xml" href="favicon.svg">
```

## Oma flavicon

Mene sivulle `https://favicon.io/` ja luo oma flavicon. Lataa oman projektisi hakemistoon ja liitä html-koodiin (kts. linkki-esimerkit edellisessä luvussa).

Jos favicon ei näy heti selaimessa, se johtuu yleensä välimuistista. Päivitä sivu kovalla päivityksellä

`Ctrl + F5` tai `Cmd+Shift+R` (Windows/Linux).
