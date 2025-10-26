# Tavoite

Tee sääsivu, joka näyttää muutaman kaupungin ajankohtaisen sään.  
Säätiedot haetaan **OpenWeatherMapin API:n** avulla.  
Sivu hakee säätiedot **JavaScriptillä** ja näyttää ne käyttäjälle selkeässä muodossa.

---

# Tehtävän vaiheet

## 1. Rekisteröidy OpenWeatherMapiin

- Mene osoitteeseen [https://home.openweathermap.org/users/sign_up](https://home.openweathermap.org/users/sign_up)
- Luo ilmainen käyttäjätili ja löydä oma API-avain
- API-dokumentaatio: [https://openweathermap.org/current](https://openweathermap.org/current)

## 2. Testaa esimerkki HTML-sivu, jossa on:

- **input** kaupungin nimelle
- **nappi** "Hae sää"
- **alue** (esim. `<div>`), johon säätiedot tulostetaan

## 3. Suunnittele oma sivu suunnittelutyökalulla

- Käytä esimerkiksi **Figmaa**
- Sivun latautuessa näkyvät säätilat kaupungeille: _Raahe, Girona, Bryssel, Zlin_
- Huomioi suunnittelussa **hyvän käyttöliittymän periaatteet**, katso ui.md

## 4. Käytä JavaScriptiä datan hakemiseen

- Käytä `fetch()`-funktiota hakeaksesi dataa OpenWeatherMapin API:sta
- Poimi JSON-datasta lämpötila, sään kuvaus, ikoni jne.

## 5. Näytä seuraavat tiedot html-sivulla:

- Kaupungin nimi
- Lämpötila (°C)
- Sään kuvaus (esim. _“Pilvinen”_)
- Ikoni (OpenWeatherMapin kuvakkeista)

## 6. Lisätehtävä - Näytä myös:

- Tuulen nopeus
- Ilmanpaine
- Kosteus
- Auringon nousu- ja laskuaika
- 5 päivän ennuste

---

# Esimerkkikoodi

```html
<!DOCTYPE html>
<html lang="fi">
  <head>
    <meta charset="UTF-8" />
    <title>Sääsivu</title>
  </head>
  <body>
    <h1>Sääsovellus</h1>
    <input id="kaupunki" placeholder="Anna kaupungin nimi" />
    <button id="hae">Hae sää</button>

    <div id="tulos"></div>

    <script>
      async function haeSaa(kaupunki) {
        const apiKey = "OMA_API_AVAIN"; // lisää oma avain
        const url = `https://api.openweathermap.org/data/2.5/weather?q=${kaupunki}&appid=${apiKey}&units=metric&lang=fi`;
        try {
          const vastaus = await fetch(url);
          if (!vastaus.ok) throw new Error("Kaupunkia ei löytynyt");

          const data = await vastaus.json();
          console.log(data);
          return data;
        } catch (error) {
          console.error("Virhe haussa:", error);
          return null;
        }
      }

      async function naytaSaa() {
        const kaupunki = document.querySelector("#kaupunki").value;
        const tulos = document.querySelector("#tulos");

        const data = await haeSaa(kaupunki);
        if (!data) {
          tulos.textContent = "Säätietoja ei voitu hakea.";
          return;
        }

        const kuvaus = data.weather[0].description;
        const lampo = data.main.temp;
        const ikoni = data.weather[0].icon;

        tulos.innerHTML = `
          <h2>${data.name}</h2>
          <img src="https://openweathermap.org/img/wn/${ikoni}@2x.png">
          <p>${kuvaus}, ${lampo} °C</p>
        `;
      }

      document.querySelector("#hae").addEventListener("click", naytaSaa);
    </script>
  </body>
</html>
```
