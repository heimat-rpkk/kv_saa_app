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
