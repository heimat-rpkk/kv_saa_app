# Kartan näyttäminen koordinaattien perusteella

Leaflet toimii pelkällä JavaScriptillä, ilman maksua tai API-avainta.

## Lisää Leaflet kirjastot HTML-tiedoston <head>-osaan:

```html
<link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
```

## Lisää div kartalle

```html
<div id="kartta" style="height: 300px; width: 300px;"></div>
```

## Lisää kartta JavaScriptillä

Kun olet saanut säätiedosta koordinaatit (lat ja lon), voit näyttää kartan näin:

```javascript
let map;
function naytaKartta(lat, lon) {
  if (map) {
    map.remove(); // poistaa vanhan kartan
  }
  map = L.map("kartta").setView([lat, lon], 10);

  L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
    attribution: "&copy; OpenStreetMap contributors",
  }).addTo(map);

  L.marker([lat, lon])
    .addTo(map)
    .bindPopup("Sijainti: " + lat.toFixed(2) + ", " + lon.toFixed(2))
    .openPopup();
}
```

## Kutsu kartan näyttöä säädatan haun jälkeen

```javascript
async function haeSaa(kaupunki) {
  const apiKey = "OMA_APIKEY";
  const vastaus = await fetch(
    `https://api.openweathermap.org/data/2.5/weather?q=${kaupunki}&appid=${apiKey}&units=metric`
  );
  const data = await vastaus.json();
  console.log(data);

  // Näytä kartta
  naytaKartta(data.coord.lat, data.coord.lon);
}
```

---

## Useita paikkoja samassa kartassa

```html
<div id="isoKartta" style="height: 600px; width: 600px;"></div>
```

```javascript
// Kaupungit ja niiden koordinaatit
const kaupungit = [
  { nimi: "Raahe", lat: 64.6833, lon: 24.4743 },
  { nimi: "Bryssel", lat: 50.8503, lon: 4.3517 },
  { nimi: "Sevilla", lat: 37.3886, lon: -5.9823 },
  { nimi: "Praha", lat: 50.0755, lon: 14.4378 },
];

let bMap;
function isoKartta(kaupungit) {
  // Alustetaan kartta keskelle Eurooppaa
  if (bMap) {
    bMap.remove(); // poistaa vanhan kartan
  }
  bMap = L.map("isoKartta").setView([50, 10], 4);

  // Automaattinen kartan sovitus kaupunkien mukaan
  const rajat = L.latLngBounds(kaupungit.map((k) => [k.lat, k.lon]));

  bMap.fitBounds(rajat, {
    // Lisää vähän tilaa ylhäälle ja sivuille
    paddingTopLeft: [0, 70], // ylhäälle 70px
    paddingBottomRight: [0, 0], // alas ja oikea 0
  });
  // Lisätään taustakartta OpenStreetMapista
  L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
    attribution: "&copy; OpenStreetMap contributors",
  }).addTo(bMap);

  // Lisätään kaikki kaupungit kartalle
  kaupungit.forEach((kaupunki) => {
    L.marker([kaupunki.lat, kaupunki.lon])
      .addTo(bMap)
      .bindTooltip(`📍 ${kaupunki.nimi}`, {
        permanent: true,
        direction: "top",
        offset: [0, -10],
      });
  });
}
isoKartta(kaupungit);
```
