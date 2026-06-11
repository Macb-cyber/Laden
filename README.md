# EV Bespaarcheck

EV Bespaarcheck is een moderne, responsive Nederlandse calculator-website waarmee bezoekers snel inzicht krijgen in de energiekosten van elektrisch rijden.

De website berekent live:

- laadkosten per maand, per jaar en per 100 km;
- benzinekosten per jaar;
- besparing ten opzichte van benzine;
- jaarlijks stroomverbruik inclusief laadverlies;
- een schatting van het aantal laadbeurten per jaar.
- het effect van laden met zonne-overschot;
- werkelijke bankkosten en gemiste terugleververgoeding;
- het verschil tussen 2026 met salderen en 2027 zonder salderen.
- hoeveel kilometer de auto op de jaarlijkse opbrengst van zonnepanelen kan rijden;
- het verschil tussen werkelijke uitgaven en economische kosten van zonneladen.

Bezoekers kunnen een elektrische auto uit de ingebouwde lokale autodatabase kiezen. Merk,
model en uitvoering worden stap voor stap geselecteerd, waarna verbruik en accucapaciteit
automatisch worden ingevuld. Deze waarden blijven handmatig aanpasbaar.

Staat een auto niet in de lijst, dan kan de bezoeker de autonaam, het model, de uitvoering,
het verbruik en de accucapaciteit zelf invoeren.

De website gebruikt alleen HTML, CSS en JavaScript. Er is geen backend, framework of externe API nodig.
De autodatabase staat als de array `evDatabase` bovenaan in `app.js` en kan daar eenvoudig
worden uitgebreid.

## Nieuwe auto's toevoegen

Nieuwe auto's voeg je bovenaan in `app.js` toe aan de array `evDatabase`. Voeg voor iedere
uitvoering een nieuw object toe:

```js
{
  brand: "Merknaam",
  model: "Modelnaam",
  version: "Uitvoering",
  consumption: 16.5,
  battery: 60
}
```

- `consumption` is het verbruik in kWh per 100 km.
- `battery` is de accucapaciteit in kWh.

De merk-, model- en uitvoeringdropdowns worden daarna automatisch vanuit de database gevuld.

## Laadverdeling

De hoofdcalculator gebruikt een eenvoudige verdeling tussen thuisladen en snelladen. De
bezoeker kan een herkenbare voorkeuze gebruiken of de schuif aanpassen. Snelladen wordt
automatisch aangevuld, waardoor de laadverdeling altijd 100% is.

Zonne-overschot en salderen staan bewust in aparte calculators, zodat de hoofdcalculator
overzichtelijk blijft.

De website bevat ook een aparte zonnepanelen-naar-rijbereikcalculator.

De rijbereikcalculator is bewust eenvoudig gehouden: de bezoeker vult het aantal panelen en
het vermogen per paneel in en kiest met een schuif hoeveel zonnestroom naar de auto gaat.
Het totale geïnstalleerde paneelvermogen wordt automatisch in kWp getoond. De gemiddelde
opbrengst en het autoverbruik worden als rustige aannames weergegeven.

### Standaardtarieven aanpassen

De standaardwaarde voor de thuisstroomprijs staat in `app.js` in het object `defaults`.
Pas `homePrice` aan voor de standaard stroomprijs. De terugleververgoeding staat alleen in
de aparte zonne- en salderingscalculators; pas daarvoor de bijbehorende `value`-attributen
in `index.html` aan.

## Lokaal openen

De eenvoudigste manier is om `index.html` rechtstreeks in een browser te openen.

Voor lokaal testen via een eenvoudige webserver kun je in deze map bijvoorbeeld uitvoeren:

```powershell
python -m http.server 8000
```

Open daarna `http://localhost:8000` in je browser.

## Op GitHub zetten

1. Maak op GitHub een nieuwe lege repository.
2. Open een terminal in de projectmap.
3. Voer de volgende opdrachten uit:

```powershell
git init
git add .
git commit -m "Eerste versie EV Bespaarcheck"
git branch -M main
git remote add origin https://github.com/JOUW-GEBRUIKERSNAAM/ev-bespaarcheck.git
git push -u origin main
```

Vervang de voorbeeld-URL door de URL van je eigen repository.

## Publiceren op Vercel

1. Log in op [Vercel](https://vercel.com).
2. Kies **Add New Project**.
3. Importeer de GitHub-repository.
4. Laat de frameworkkeuze op **Other** staan.
5. Er is geen build command nodig.
6. Klik op **Deploy**.

Vercel publiceert de statische bestanden automatisch. Elke nieuwe push naar de hoofdbranch kan daarna automatisch worden uitgerold.
