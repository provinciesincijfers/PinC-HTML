# 5. Opsommingen (lijsten)

Een **opsomming** of **lijst** bestaat uit een aantal **items** die onder elkaar weergegeven worden.

We maken een onderscheid tussen **genummerde** en **ongenummerde** lijsten. Bij een genummerde opsomming krijgt elk item automatisch een **volgnummer**; bij een ongenummerde lijst verschijnt vóór elk item een **bullet**.

Je kunt lijsten met meerdere niveaus maken, waarbij elk volgend niveau wat verder inspringt. Je doet dat door _binnen een lijstitem_ weer een nieuwe lijst op te nemen.

## Genummerde lijst

Een genummerde lijst zetten we binnen een **ol**-element (_ordered list_). Binnen het ol-element zetten we één of meerdere **li**-elementen (_list items_).

```
<ol>
	<li>Instellingen voor kinderopvang</li>
	<li>Instellingen voor kleuter-, lager- en buitengewoon onderwijs</li>
	<li>Ziekenhuizen en verzorgingstehuizen</li>
</ol>
```

Dit wordt als volgt weergegeven in de browser:

 1. Instellingen voor kinderopvang
 2. Instellingen voor kleuter-, lager- en buitengewoon onderwijs
 3. Ziekenhuizen en verzorgingstehuizen

## Ongenummerde lijst

Een ongenummerde lijst zetten we binnen een **ul**-element (_unordered list_). Binnen het ul-element zetten we weer één of meerdere **li**-elementen (_list items_).

```
<ul>
	<li>Instellingen voor kinderopvang</li>
	<li>Instellingen voor kleuter-, lager- en buitengewoon onderwijs</li>
	<li>Ziekenhuizen en verzorgingstehuizen</li>
</ul>
```

Dit wordt als volgt weergegeven in de browser:

- Instellingen voor kinderopvang
- Instellingen voor kleuter-, lager- en buitengewoon onderwijs
- Ziekenhuizen en verzorgingstehuizen

## Lijsten met meerdere niveaus

Je kunt een lijst met meerdere niveaus maken door binnen een li-element weer andere ul- of ol-elementen op te nemen.

Elk lijstniveau wordt automatisch iets verder ingesprongen.

```
<ul>
	<li>Ziekenhuizen en verzorgingstehuizen
		<ul>
			<li>Brugge</li>
			<li>Oostende</li>
		</ul>
	</li>
</ul>
```

Dit wordt als volgt weergegeven in de browser:

- Ziekenhuizen en verzorgingstehuizen
  - Brugge
  - Oostende

> *Let op: plaats het ul- of ol-element van het volgende niveau altijd **binnen een li-element**. Sluit dat li-element pas af ná het ondergeschikte ul- of ol-element.*

Je kunt nog diepere niveaus maken. De webbrowser gebruikt voor elk ongenummerd niveau een ander type bullet. Het bullettype kan ook gewijzigd worden met CSS naar om het even welk Unicode-karakter of zelfs naar een (kleine) afbeelding. Met een **type**-attribuut kun je een bullettype kiezen uit een aantal voorgedefinieerde types. We spreken echter af dat we binnen PinC gewoon de standaard bullets gebruiken.

```
<ol>
	<li>Ziekenhuizen en verzorgingstehuizen
		<ol>
			<li>Brugge</li>
			<li>Oostende</li>
		</ol>
	</li>
</ol>
```

Dit wordt als volgt weergegeven in de browser:

<ol>
	<li>Ziekenhuizen en verzorgingstehuizen
		<ol type="1"><!-- nodig voor correcte weergave op GitHub -->
			<li>Brugge</li>
			<li>Oostende</li>
		</ol>
	</li>
</ol>

Standaard zal je webbrowser de lijstitems van een genummerde lijst op elk niveau nummeren met Arabische cijfers, maar je kunt er ook voor kiezen om kleine letters, hoofdletters of Romeinse cijfers te gebruiken. Dit kan via CSS of via een type-attribuut.

```
<ol type="a">
	<li>Instellingen voor kinderopvang</li>
	<li>Instellingen voor kleuter-, lager- en buitengewoon onderwijs</li>
	<li>Ziekenhuizen en verzorgingstehuizen
		<ol type="I">
			<li>Brugge</li>
			<li>Oostende</li>
		</ol>
	</li>
</ol>
```

Dit wordt als volgt weergegeven in de browser:

<ol type="a">
	<li>Instellingen voor kinderopvang</li>
	<li>Instellingen voor kleuter-, lager- en buitengewoon onderwijs</li>
	<li>Ziekenhuizen en verzorgingstehuizen
		<ol type="I">
			<li>Brugge</li>
			<li>Oostende</li>
		</ol>
	</li>
</ol>

Je kunt natuurlijk ook naar believen genummerde en ongenummerde lijsten mengen: binnen een li-element binnen een ul-element kun je voor het volgende lijstniveau een ol-element gebruiken en vice versa.

## Complexe lijsten

De voorbeelden hierboven laten eenvoudige lijsten zien, waarbij elk lijstitem uit een kort stukje tekst bestaat. Een lijst kan echter ook vrij complex woorden, met name als je een lange lijst wilt maken met meerdere niveaus, waarbij lijstitems uit meerdere alinea’s bestaan of zelfs afbeeldingen of tabellen bevatten.

We zagen al dat een li-element behalve een stukje tekst ook weer een ul- of ol-element kan bevatten. Maar een li-element kan nog veel meer bevatten. Wil een lijstitem maken dat uit meerdere alinea’s bestaat, dan kun je **p**-elementen gebruiken binnen li. Of je kunt een kleine tabel opnemen in een lijst door een **table**-element binnen een li-element te plaatsen. (Hoe je een tabel maakt, leer je in het volgende hoofdstuk.)

In dergelijke lange, complexe lijsten kan het handig zijn om bijvoorbeeld extra witruimte toe te voegen tussen de items of bij de overgang naar een volgend niveau.

Daar is standaard niets speciaals voor voorzien in HTML, maar met CSS kunnen we dat zelf helemaal sturen. Om het je makkelijk te maken, hebben we via CSS al enkele mogelijkheden voorzien. Het enige wat je daarvoor moet doen, is een **class**-attribuut toevoegen bij de elementen **ul**, **ol** of **li**. Hieronder zie je welke attribuutwaarden je daarbij kunt gebruiken. De waarde van een class-attribuut is de **classnaam**, zoals die gedefinieerd is in CSS.

| element/class         | omschrijving                                                |
| --------------------- | ----------------------------------------------------------- |
| `<ul class="open">`   | ongenummerde lijst extra ruimte tussen de items             |
| `<ol class="open">`   | genummerde lijst extra ruimte tussen de items               |
| `<li class="open">`   | lijstitem met extra ruimte tussen de alinea’s (p-elementen) |
| `<li class="bold">`   | lijstitem met vet lijstnummer                               |
| `<li class="italic">` | lijstitem met cursief lijstnummer                           |

Wanneer een lijstitem uit meerdere alinea’s tekst bestaat, dan gebruik je meerdere **p**-elementen binnen het li-item. In tegenstelling tot alinea’s buiten een lijst zal er tussen de alinea’s binnen een lijst geen extra witruimte komen, tenzij je `class="open"` gebruikt hebt bij het li-element.

We hebben ook de mogelijkheid voorzien om het lijstnummer vet of cursief te zetten. Lijstnummers verschijnen normaal gezien niet vet en niet cursief, ook niet wanneer je de tekst van het lijstitem vet of cursief hebt gezet. Om ervoor te zorgen dat het lijstnummer vet of cursief verschijnt, gebruik je `class="bold"` of `class="italic"` bij het li-element.

> _Let op:_ de classes die we hier gebruiken (`open`, `bold` en `italic`) maken standaard geen deel uit van HTML. Ze werken alleen maar omdat we ze vooraf gedefinieerd hebben in het **CSS**-bestand (`moreinfo.css`) dat we gebruiken in de HTML-bijlagen bij de metadata in PinC. Dat betekent dat je er ook alleen maar in die bijlagen gebruik van kunt maken. Je kunt dit dus niet gebruiken in de velden van de bronnentabel! Het is overigens sowieso geen goed idee om lange, complexe lijsten in de bronnentabel zelf te plaatsen. Je werkt daarvoor beter met een bijlage.

Nog een weetje: wanneer er voor een element meerdere classes gedefinieerd zijn, dan kun je ze combineren! Wil je bijvoorbeeld een lijstitem met een vet lijstnummer én extra ruimte tussen de alinea’s, dan geef je als attribuutwaarde beide classnamen op, gescheiden door een spatie: `<li class="bold open">`. De onderlinge volgorde van de classnamen speelt daarbij geen rol.

## Samenvatting

- We maken een onderscheid tusssen twee soorten opsommingen of lijsten: een **ongenummerde** lijst (**ul**) en een **genummerde** lijst (**ol**).
- Lijsten bevatten **lijstitems**.
- Binnen een lijstitem kun je weer een andere lijst opnemen om zo een opsomming met **meerdere niveaus** te maken. Elk niveau wordt automatisch iets verder **ingesprongen**.
- Lijstitems van een ongenummerde lijst worden voorafgegaan door een **bullet**.
- Lijstitems van een genummerde lijst worden voorafgegaan door een **doorlopend nummer**.
- Je kunt het type van de nummering aanpassen: standaard krijg je **Arabische cijfers**, maar je kunt ook kiezen voor **Romeinse cijfers** of **letters** door een `type`-attribuut op te geven.<br/><br/>
- Je kunt de opmaak van een lijst of een lijstitem aanpassen door een `class`-attribuut te gebruiken dat op voorhand is gedefinieerd via **CSS**.
- Binnen een lijstitem kun je **p**-elementen gebruiken wanneer het lijstitem uit meerdere alinea’s bestaat.

### HTML-elementen in dit hoofdstuk

`li`: lijstitem – attribuut: `class` (classnaam)

`ol`: genummerde lijst – attributen: `class` (classnaam), `type` (soort nummer)

`ul`: ongenummerde lijst – attributen: `class` (classnaam), `type` (soort bullet)

___
Volgend hoofdstuk: [Tabellen](06_tabellen.md)
