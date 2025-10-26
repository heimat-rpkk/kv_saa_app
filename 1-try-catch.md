# try/catch

- `try/catch` on JavaScriptin tapa käsitellä virheitä
- Estää sovelluksen kaatumisen virhetilanteessa
- `try`-lohkoon laitetaan koodi, joka voi aiheuttaa virheen
- `catch`-lohko suoritetaan, jos virhe tapahtuu, ja virhe voidaan tallentaa ja käsitellä

**Perusrakenne:**

```javascript
try {
  // koodia, joka saattaa heittää virheen
  let tulos = riskyFunction();
  console.log("Tulos:", tulos);
} catch (virhe) {
  // käsitellään virhe
  console.error("Tapahtui virhe:", virhe);
}
```

- Jos `riskyFunction()` onnistuu → `catch` ei suoriteta
- Jos `riskyFunction()` heittää virheen → suoritetaan `catch`-lohko, eikä ohjelma kaadu
