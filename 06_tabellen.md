# 6. Tabellen

Een HTML-tabel zit vervat in een **table**-element. Binnen een tabel kunnen we twee delen onderscheiden, elk binnen hun eigen element: de **thead** (_table head_) en de **tbody** (_table body_). Binnen het thead-element vind je de kolomhoofden, die doorgaans een andere opmaak krijgen dan de rest van de tabel; binnen het tbody-element vind je de eigenlijke tabelgegevens.

Zowel de thead als de tbody bestaan uit één of meer rijen. Elke rij is weer een afzonderlijk element: **tr** (_table row_). Een tabelrij bestaat op zijn beurt weer uit cellen. Voor cellen zijn er twee verschillende elementen: **td** (_table data_) en **th** (_table heading_). Binnen de thead bestaat een rij normaal gezien th-elementen; binnen de tbody bestaat een rij normaal gezien uit td-elementen. Standaard verschijnt de inhoud van een th-element gecentreerd binnen de cel en in het vet (maar dat kan uiteraard weer aangepast worden met CSS). De inhoud van een td-element verschijnt links/bovenaan uitgelijnd in de cel en niet vet.

Hieronder zie je een eenvoudige tabel waarin al deze elementen gebruikt worden. De tabel telt drie rijen en vier kolommen.

```
<table>
	<thead>
		<tr>
			<th>Nace 2 digits</th>
			<th>Hoofdsector</th>
			<th>Nace 1 digit</th>
			<th>Technologie- en kennisintensiteit</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>01 Teelt van gewassen, veeteelt, jacht en diensten in verband met deze activiteiten</td>
			<td>Landbouw</td>
			<td>A Landbouw, bosbouw en visserij</td>
			<td>Andere sectoren</td>
		</tr>
		<tr>
			<td>02 Bosbouw en de exploitatie van bossen</td>
			<td>Landbouw</td>
			<td>A Landbouw, bosbouw en visserij</td>
			<td>Andere sectoren</td>
		</tr>
	</tbody>
</table>
```

Een th-element zul je voornamelijk bovenaan de tabel aantreffen, in de kolomkoppen of kolomlabels binnen de rijen van het thead-element. Maar daarnaast kan een tabel ook nog een kolom met rijlabels hebben. In dat geval kun je th-elementen ook aantreffen in de eerste kolom van de tabel, in de rijen die binnnen het tbody-element staan.

Een th-element binnen de tbody hoeft er niet noodzakelijk hetzelfde uit te zien als een th-element binnen de thead: via CSS kunnen ze een andere opmaak krijgen.

Bij lange tabellen, die over meerdere pagina’s lopen wanneer het HTML-bestand afgedrukt of naar PDF geëxporteerd wordt, zal de thead automatisch herhaald worden bovenaan elke pagina. Gebruik daarom altijd thead en tbody bij grote tabellen.

Bij korte tabellen kun je eventueel de thead en tbody-elementen weglaten en de tr-elementen rechtstreeks in het table-element plaatsen.

```
<table>
	<tr>
		<th>Mediaan van twee<br/>bouwjaarintervallen</th>
		<th>Bouwjaar-<br/>interval 1</th>
		<th>Bouwjaar-<br/>interval 2</th>
		<th>Bouwjaar-<br/>interval 3</th>
		<th>Bouwjaar-<br/>interval 4</th>
		<th>Bouwjaar-<br/>interval 5</th>
	</tr>
	<tr>
		<th>Bouwjaarinterval 1</th>
		<td></td>
		<td>1856</td>
		<td>1868</td>
		<td>1879</td>
		<td>1887</td>
	</tr>
	<tr>
		<th>Bouwjaarinterval 2</th>
		<td></td>
		<td></td>
		<td>1875</td>
		<td>1886</td>
		<td>1894</td>
	</tr>
</table>
```

Verder kun je bij td en th nog deze twee attributen gebruiken: `colspan` om een cel te maken die twee of meer kolommen breed is, en `rowspan` om een cel te maken die twee of meer rijen hoog is. Als attribuutwaarde geef je het aantal kolommen of het aantal rijen op, bv. `<td colspan="2">` voor een cel die over twee kolommen loopt.

Wanneer een tabelcel uit een kort stukje tekst bestaat, zoals in de voorbeelden hierboven, dan heb je binnen td of th geen andere elementen nodig. Maar binnen een cel zou je ook weer p-elementen, ol-elementen of ul-elementen kunnen gebruiken om alinea’s en lijsten te maken. Eventueel kan er via CSS voor gezorgd worden dat die elementen, wanneer ze binnen een tabel gebruikt worden, een andere opmaak krijgen dan buiten een tabel (bijvoorbeeld met minder witruimte tussen de alinea’s, in een kleiner lettertype, etc.).

Tabellen kunnen ook lege cellen bevatten. In dat geval laat je de begintag onmiddellijk volgen door de eindtag, zonder content ertussen, bv. `<td></td>` of `<th></th>`.

> *N.B.: gebruik niet `<td/>` of `<th/>` voor lege cellen! Die notatie mag je alleen maar gebruiken bij elementen die nooit inhoud **kunnen** bevatten, zoals bv. `<br/>`.*

Hoe de tabel er exact uitziet, kan gedefinieerd worden met CSS. Door een class-attribuut toe te voegen bij het table-element en de classes te definiëren in CSS, kun je een onderscheid maken tussen verschillende soorten tabellen, die elk hun eigen stijl krijgen. Met CSS kun je tabellen voorzien van lijnen tussen de rijen, tussen de kolommen en rondom de tabel, kun je de thead en de tbody een verschillende opmaak geven, de witruimte tussen rijen en kolommen of tussen de tekst en de lijnen instellen, kun je cellen een achtergrondkleur geven, etc.

Mommenteel hebben we maar één tabelstijl voorzien. Mocht je nood hebben aan andere tabelstijlen in HTML-bijlagen, dan kunnen we op aanvraag zorgen voor een uitbreiding van ons CSS-bestand (`moreinfo.css`).

## Samenvatting

- Een HTML-tabel zit in een **table**-element en bestaat doorgaans uit een **thead** en een **tbody**.
- Het **thead**-element bevat de kolomkoppen en kan uit één of meer rijen bestaan.
- Het **tbody**-element bevat de tabelgegevens en bestaat vrijwel altijd uit meerdere rijen.
- Elke rij, zowel binnen de thead als binnen de tbody, zit vervat binnen een **tr**-element.
- Binnen een rij zitten de cellen van de tabel. Je gebruikt daarvoor een **td**-element als het een cel met data betreft, of een **th**-element als het een rij- of kolomlabel betreft.
- Je kunt een cel over meerdere kolommen laten lopen door een `colspan`-attribuut te gebruiken.
- Je kunt een cel over meerdere rijen laten lopen door een `rowspan`-attribuut te gebruiken.
- Een lege cel geef je aan met `<td></td>` of `<th></th>` (eventueel met een `colspan`- en/of `rowspan`-attribuut).

### HTML-elementen in dit hooofdstuk

`table`: tabel

`tbody`: tabelinhoud

`td`: tabelcel met data – attributen: `colspan` (aantal kolommen), `rowspan` (aantal rijen)

`th`: tabelcel met rij- of kolomkop – attributen: `colspan` (aantal kolommen), `rowspan` (aantal rijen)

`thead`: tabelkop

`tr`: tabelrij

___
Volgend hoofdstuk: [Afbeeldingen](07_afbeeldingen.md)
