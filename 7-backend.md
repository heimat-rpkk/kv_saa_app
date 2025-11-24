# Backend

Jos haluat piilottaa API-avaimen, se onnistuu (vain) käyttämällä backendiä ja ympäristömuuttujaa.
Se onnistuu seuraavasti.

## Lisää api

Luo projektin juureen kansio ja tiedosto `/api/weather.js`.

```js
export default async function handler(req, res) {
  const apiKey = process.env.OPENWEATHER_API_KEY;
  const city = "Raahe"; // Voit myöhemmin kenraalisoida tämän req.query.city avulla

  const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&lang=fi&appid=${apiKey}`;

  try {
    const response = await fetch(url);
    if (!response.ok) {
      return res.status(response.status).json({ error: "API error" });
    }

    const data = await response.json();
    res.status(200).json(data);
  } catch (err) {
    res.status(500).json({ error: "Server error" });
  }
}
```

## Kutsu backendia frontendissä

Korvaa js-koodissa alkuperäinen fetch:

```js
const response = await fetch("/api/weather");
const data = await response.json();
// console.log(data);
```

## Lisää Verceliin ympäristömuuttuja

- Avaa projektisi Vercelissä

- Siirry Settings → Environment Variables

- Lisää uusi muuttuja:

`Name: OPENWEATHER_API_KEY`

`Value: oma-api-avain`

- Paina Save
