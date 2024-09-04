# 8. Titels en tussenkopjes

## Titelniveaus

HTML kent 6 niveaus van koppen (in het Engels: headings), waarvoor de elementen **h1** t.e.m. **h6** worden gebruikt. Standaard worden alle koppen in het vet weergegeven, met een steeds kleiner wordende tekengrootte: koppen van het hoogste niveau (h1) worden het grootst weergegeven, koppen van het laagste niveau (h6) het kleinst.

Hoe de verschillende niveaus van kopjes er precies uitzien (tekengrootte, witruimte boven en onder, vet of cursief, etc.) wordt verder bepaald via CSS.

Probeer het aantal niveaus te beperken. Momenteel hebben we in de CSS-stijl voor de HTML-bijlagen maximaal vier niveaus gedefinieerd (h1 t.e.m. h4). Een HTML-bijlage heeft normaal gezien slechts één **h1**-kop met de titel van de bijlage, helemaal bovenaan het document.

## Description-veld (bronnentabel)

In het Description-veld van de bronnentabel beginnen we met een algemene omschrijving, gevolgd door een opsomming van de indicatoren. De indicatoren worden voorafgegaan door een tussenkopje ‘Indicatoren’. We spreken af dat we daarvoor een **h3**-kopje gebruiken. Het kopje krijgt daardoor dezelfde opmaak als de andere kopjes in het dialoogvenster met de metadata (bv. het kopje ‘Beschrijving’).

In de HTML-velden van de bronnentabel kunnen we zelf geen CSS gebruiken. We zijn dus gebonden aan de standaard opmaak van Swing. Een h3-kopje komt hier best overeen met de opmaak die we willen zien.

## HTML-bijlagen

Gebruik voor de hoofdtitel van een HTML-bijlage altijd een **h1**-element. Voor verdere onderverdelingen kun je **h2**, **h3** en **h4** gebruiken.

Houd daarbij de logische koppenstructuur aan: het eerstvolgende koppenniveau onder een h1-kop moet altijd h2 zijn, nooit h3 of h4. Onder een h2-kop kun je een verdere onderverdeling maken met h3, niet met h4, en een h4-kopje kun je alleen gebruiken als onderverdeling binnen h3.

### Voorkom verweesde tussenkopjes

Codeer alles wat op een kopje lijkt als een kopje. Een h3-kop ziet er misschien exact hetzelfde uit als een korte alinea met vette tekst, maar toch is het belangrijk dat je zo’n kopje codeert met `<h3>...</h3>` en niet met `<p><b>...</b></p>`. Ook al zijn lettertype, tekengrootte en witruimte boven/onder exact gelijk en zie je dus geen verschil, toch kan dit een verschillend resultaat geven wanneer je het HTML-bestand afdrukt of exporteert naar een PDF-bestand!

Stel dat zo’n kopje onderaan de pagina komt. We willen niet dat een tussenkopje verweesd helemaal onderaan de pagina blijft staan, terwijl de bijbehorende tekst pas op de volgende pagina komt. Dat is het resultaat dat je kunt krijgen als je  `<p><b>...</b></p>` gebruikt hebt. Door `<h3>...</h3>` te gebruiken, zorgt de browser ervoor dat het kopje altijd samenblijft met de erop volgende alinea. Een dergelijk kopje zal dus nooit onderaan de pagina staan. Als de eerste regels van de alinea niet meer op de pagina passen en dus op de volgende pagina komen, zal ook het kopje dat eraan voorafgaat, mee naar de volgende pagina verhuizen.

Dit lijkt misschien een detail, maar het is wel degelijk van belang om een kwaliteitsvolle output te genereren. Een document waar kopjes zonder tekst onderaan een pagina staan, komt niet professioneel over.

### Niet-vette tekst in vette tussenkopjes

Je weet al hoe je in een gewone alinea enkele woorden in het vet kunt zetten: namelijk door `<b>...</b>` te gebruiken. Maar hoe kun je in een tussenkopje, dat automatisch in het vet weergegeven wordt, een of meer woorden niet-vet zetten?

Daar is in HTML geen standaard oplossing voor, maar we hebben een oplossing geïmplementeerd in het CSS-bestand dat gebruikt wordt voor de HTML-bijlagen.

Om in een kopje een fragment niet-vet te maken, gebruik je een **span**-element met een `class="roman"`-attribuut, bv.:

```
<h3>Bouwvorm <span class="roman">van woongelegenheden op percelen met 1 woongelegenheid:</span></h3>
```

In het voorbeeld hierboven wordt de tekst van het h3-kopje automatisch vet weergegeven. De inhoud van het span-element zal echter niet-vet weergegeven worden.

N.B.: span is een inline-element dat voor heel wat verschillende doeleinden gebruikt kan worden. Doorgaans wordt het voorzien van een class-attribuut om een onderscheid te maken tussen de verschillende soorten span-elementen, en wordt daaraan een CSS-stijl gekoppeld. Inline-elementen zijn elementen die je alleen binnen een tekstblok (alinea, kopje, lijstitem, tabelcel, ...) kunt gebruiken.

### Lijstitems met tussenkopjes

In complexe lijsten, waarin een lijstitem bestaat uit meerdere alinea’s, kan het goed zijn dat je de eerste alinea van een lijstitem wilt opmaken als een tussenkopje, om ervoor te zorgen dat dit samenblijft met de volgende alinea wanneer het bestand wordt afgedrukt of naar PDF geëxporteerd wordt.

We spreken af dat we daar in zo’n geval een **h3**-kopje voor gebruiken, bv.:

```
<li class="bold open">
	<h3>Identificatie personen niet-Belgische herkomst</h3>
	<p>Hoe verder we teruggaan in het leven van de personen, hoe hoger de graad van waarschijnlijkheid van de waarschijnlijke informatie en hoe meer kans we iemand nog aantreffen in een huishouden waarin ook één of beide van de ouders aanwezig zijn. Pas nadat we zo ver mogelijk teruggegaan zijn in de tijd, bepalen we de herkomst van een persoon op basis van volgende criteria:</p>
	<ol type="a">
		<li>Als de persoon bij geboorte niet de Belgische nationaliteit had </li>
		<li>of als vader van de persoon bij zijn geboorte niet de Belgische nationaliteit had </li>
		<li>of als de moeder van de persoon bij haar geboorte niet de Belgische nationaliteit had</li>
	</ol>
	<p>Als er aan geen enkele van deze drie criteria wordt voldaan, of als de informatie drie maal ontbreekt, dan blijft herkomst Belgisch.</p>
</li>
```

## Samenvatting

- HTML kent zes niveaus van (tussen)koppen: **h1**, **h2**, **h3**, **h4**, **h5** en **h6**.
- De tekengrootte neemt af voor elk volgend niveau.
- De koppen worden automatisch vet weergegeven.<br/><br/>
- In het Description-veld van de bronnentabel gebruiken we **h3** voor het kopje ‘Indicatoren’.
- In de HTML-bijlagen gebruiken we **h1** voor de titel van de bijlage en gebruiken we **h2**, **h3** en **h4** voor de volgende niveaus.
- In de HTML-bijlagen kun je een **span**-element met een `class="roman"`-attribuut gebruiken wanneer je uitzonderlijk een deel van een tussenkop niet-vet wilt weergeven.
- In de HTML-bijlagen kun je een **h3**-kopje gebruiken binnen een lijstitem (li-element).

### HTML-elementen in dit hoofdstuk

`h1`: kopje van niveau 1

`h2`: kopje van niveau 2

`h3`: kopje van niveau 3

`h4`: kopje van niveau 4

`h5`: kopje van niveau 5

`h6`: kopje van niveau 6

`span`: algemeen inline-element – attribuut: `class`: classnaam

___
Volgend hoofdstuk: [Whitespace](09_whitespace.md)
