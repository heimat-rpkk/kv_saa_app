# async/await

- `async/await` on JavaScriptin tapa kirjoittaa asynkronista koodia.
- Asynkronisuus mahdollistaa odottamisen ilman, että koko sovellus jää jumiin.
- Kaikki pitkään kestävät toiminnot, jotka eivät valmistu heti, kannattaa käsitellä asynkronisesti, esim. verkko- ja API-kutsu, tiedoston lukeminen, jne.
- `async` määrittää, että funktio on asynkroninen ja palauttaa aina Promise-olion.
- `await` pysäyttää funktion suorituksen, kunnes Promise on ratkaistu, ja palauttaa sen tuloksen.

**Perusidea:**

```javascript
async function omaFunktio() {
  const tulos = await jokinAsynkroninenFunktio();
  console.log(tulos);
}
```

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
