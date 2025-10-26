# Ohjeita ja vinkkejä

## Hae sää heti kun sivu ladataan

```javascript
window.addEventListener("load", () => {
  const oletus = "Raahe";
  haeSaa(oletus);
});
```

## Aika UTC → paikallinen aika

- UTC-aika sekunteina ja paikallisen aikavyöhykkeen offset:

```javascript
// Lasketaan ajankohta, jolloin säätieto on luotu
const aika = new Date(data.dt * 1000);

// Muotoilu: "keskiviikko 22. lokakuuta 2025 klo 15.00"
console.log(
  aika.toLocaleString("fi-FI", {
    weekday: "long",
    day: "numeric",
    month: "long",
    hour: "2-digit",
    minute: "2-digit",
  })
);
```

## Enter-näppäimen painalluksen tuki

```javascript
document.querySelector("#kaupunki").addEventListener("keypress", (e) => {
  if (e.key === "Enter") naytaSaa();
});
```

## Virheilmoitus tyhjälle kentälle

```javascript
if (!kaupunki.trim()) {
  tulos.textContent = "Anna kaupungin nimi.";
  return;
}
```

## Tee 5 päivän ennuste

käyttämällä endpointtia:

https://api.openweathermap.org/data/2.5/forecast?q=Kaupunki&appid=APIKEY&units=metric

API-docs:

https://openweathermap.org/forecast5
