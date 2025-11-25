# Sivun tekeminen responsiiviseksi

Responsiivisuus tarkoittaa, että web-sivun ulkoasu ja sisältö mukautuvat automaattisesti eri laitteiden ja näyttökokojen mukaan.

## Lisää `<meta>`-tagi `<head>`-osioon

Tämä kertoo selaimelle, että sivu skaalautuu laitteen mukaan:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

---

## Käytä suhteellisia mittoja (ei pelkästään px)

Esim. prosentit, `em`, `rem`, `vw`, `vh`:

```css
.container {
  width: 80%; /* skaalautuu näytön koon mukaan */
  margin: 0 auto;
}
```

---

## Media queryt eri kokoisille näytöille

Voit vaihtaa tyylejä suoraan näytön koon mukaan:

```css
/* Puhelimet */
@media (max-width: 600px) {
  .container {
    flex-direction: column;
    padding: 10px;
  }
}

/* Tabletit */
@media (min-width: 601px) and (max-width: 900px) {
  .container {
    flex-direction: row;
  }
}
```

---

## Flexbox tai CSS Grid layout

Ne mukautuvat automaattisesti. Alla kaksi esimerkkiä.

```css
.wrapper {
  display: flex;
  flex-wrap: wrap; /* rivien automaattinen vaihtuminen */
}
```

```html
<div class="grid-container">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
  <div class="item">4</div>
</div>

<style>
  .grid-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 10px;
  }
  .item {
    background-color: lightblue;
    padding: 20px;
    text-align: center;
  }
</style>
```

Selitys:
repeat(auto-fit, minmax(150px, 1fr)) tekee niin, että ruudukko luo niin monta saraketta kuin mahtuu, ja sarakkeet venyvät aina vähintään 150px:iin ja enintään käytettävissä olevan tilan mukaan (1fr).

---

## Kuvat responsiivisiksi

```css
img {
  max-width: 100%;
  height: auto;
}
```

---

## Testaa eri kokoisilla näytöillä ja devtoolsilla

Selaimen kehittäjätyökaluista voi vaihtaa näyttökokoa.
