# 9. Whitespace

Tot slot willen we je nog iets vertellen over _whitespace_ in HTML-documenten. In een typische HTML-cursus of ‑tutorial zul je daar maar weinig over lezen, maar we vinden het toch belangrijk genoeg om er hier iets over te vermelden, zeker omdat Swing die whitespace in bepaalde gevallen niet correct behandelt (zie verder).

Whitespace betekent letterlijk ‘witruimte’. Met die term worden alle vormen van spaties bedoeld. Je weet dat spaties in een tekst gebruikt worden om de woorden van elkaar te scheiden, en dat spaties in een HTML-begintag gebruikt worden om de attributen van elkaar en van de elementnaam te scheiden.

Een webbrowser zal alle opeenvolgingen van één of meer spaties, tabs en regeleinden herleiden tot één spatie. Een regeleinde kan, afhankelijk van het gebruikte besturingssysteem of afhankelijk van de instelling van de gebruikte teksteditor, zowel een _carriage return_ (U+000D) als een _line feed_ (U+000A) zijn, of een combinatie van beide.

## Whitespace in tags of tussen elementen

Op een aantal plaatsen is whitespace optioneel. Of er whitespace staat of niet, maakt in dat geval geen verschil uit. De optionele whitespace wordt door een webbrowser gewoon genegeerd. Whitespace is bijvoorbeeld optioneel aan het begin of het einde van (de meeste) elementen of tussen de (meeste) elementen onderling. In een HTML-tag is whitespace ook optioneel na de elementnaam of na het laatste attribuut.

Dat betekent bijvoorbeeld dat deze twee HTML-tags volledig equivalent zijn:

```
<img src="images/statbel_loop_schema.png" width="75%" alt="loop van de bevolking – schema"/>
```

```
<img
	src="images/statbel_loop_schema.png"
	width="75%"
	alt="loop van de bevolking – schema"
/>
```

In de eerste img-tag hierboven hebben we telkens één spatie gebruikt vóór elk attribuut, zoals we het in deze handleiding consequent hebben toegepast. In de tweede img-tag hebben we die spaties vervangen door een regeleinde en een tab, en hebben we ook een regeleinde ingevoegd na het laatste attribuut.

Wat je beslist _niet_ mag doen, is whitespace plaatsen aan het begin van een tag, meteen na het kleiner-dan-teken (dus bijvoorbeeld `< p>` mag _niet_).

Doordat whitespace tussen elementen op de meeste plaatsen optioneel is, kun je het HTML-document overzichtelijker maken. Je kunt bijvoorbeeld blanco regels invoegen tussen elementen of je kunt ondergeschikte elementen telkens wat verder laten inspringen door er spaties of tabs voor te plaatsen.

Deze twee HTML-fragmenten zijn volledig equivalent:

```
<p>Op basis van Rijksregistergegevens krijgen we zicht op:</p><ul><li>het aantal private
huishoudens en hun type</li><li>het aantal personen in private huishoudens en hun positie
in het huishouden</li><li>het aantal personen in collectieve huishoudens</li></ul>
```

```
<p>Op basis van Rijksregistergegevens krijgen we zicht op:</p>

<ul>
	<li>het aantal private huishoudens en hun type</li>
	<li>het aantal personen in private huishoudens en hun positie in het huishouden</li>
	<li>het aantal personen in collectieve huishoudens</li>
</ul>
```

In het eerste fragment hebben we alle optionele whitespace weggelaten; in het tweede hebben we regeleinden en tabs toegevoegd om het geheel overzichtelijk te maken.

Het resultaat is in beide gevallen identiek:

> <p>Op basis van Rijksregistergegevens krijgen we zicht op:</p>
>
> <ul>
> 	<li>het aantal private huishoudens en hun type</li>
> 	<li>het aantal personen in private huishoudens en hun positie in het huishouden</li>
> 	<li>het aantal personen in collectieve huishoudens</li>
> </ul>

## Whitespace in de tekst

Zoals gezegd worden opeenvolgende spaties of andere whitespace-karakters zoals tabs en regeleinden door de browser gereduceerd tot één enkele spatie. Dat betekent dat je dus bijvoorbeeld geen dubbele spatie tussen de zinnen kunt plaatsen, als je dat zou willen.

Je kunt dit echter omzeilen door het gebruik van vaste spaties (U+00A0, Alt+0160 of `&nbsp;`). Elke vaste spatie binnen een tekstblok zal door de browser weergegeven worden, ook wanneer je meerdere vaste spaties na elkaar gebruikt. Al wordt het ten sterkste afgeraden om op die manier extra ruimte te creëren. Een beter alternatief is het gebruik van CSS.

Daarnaast kun je ook gebruikmaken van een aantal speciale soorten spaties (elk met een verschillende breedte):

| Unicode | Omschrijving                                    |
| ------- | ----------------------------------------------- |
| U+2002  | en space                                        |
| U+2003  | em space                                        |
| U+2004  | ⅓ em space                                      |
| U+2005  | ¼ em space                                      |
| U+2006  | ⅙ em space                                      |
| U+2007  | figure space                                    |
| U+2008  | punctuation space                               |
| U+2009  | thin space                                      |
| U+200A  | hair space                                      |
| U+200B  | zero width space                                |

Een _em space_ (em-spatie) is een extra brede spatie waarvan de breedte overeenkomt met de tekengrootte. Bij een tekstgrootte van 10 punt is zo’n spatie dus ook 10 punt breed. Dat komt in de meeste lettertypen overeen met ruwweg de breedte van een hoofdletter M, vandaar de naam _em space_. Een _en space_ (en-spatie) is half zo breed.

Een _figure space_ heeft de breedte van een cijfer, een _punctuation space_ heeft de breedte van een punt of een komma.

De _thin space_ is een dunne spatie, de _hair space_ is extra dun, doorgaans iets meer en iets minder dan de helft van een gewone spatie, maar dat kan per lettertype verschillen.

De _zero width space_ tenslotte is een spatie met een breedte van 0. Je vraagt je wellicht af waar dat goed voor is, maar de zero width space heeft wel degelijk een bestaansreden. Je kunt haar bijvoorbeeld gebruiken op plaatsen waar een regel afgebroken mag worden zonder dat er een afbreekstreepje mag verschijnen. Net zoals bij elke gewone spatie kan er op die plaats een overgang naar een nieuwe regel plaatsvinden als het volgende woord niet meer op de regel past, maar voor de rest is de zero width space onzichtbaar.

Niet alle spaties uit bovenstaande tabel zijn in elk lettertype beschikbaar, maar je kunt ze wel probleemloos gebruiken in PinC.

Je al deze speciale spaties invoegen als een character reference, bv. `&#x2003;` voor een em-spatie.

## Whitespace in PinC

De Swing-software heeft een vervelende eigenschap: bij het weergeven van de HTML-velden van de bronnentabel zal Swing alle regeleinden ongevraagd vervangen door een `<br/>`-tag. De makers van Swing zijn uitgegaan van de veronderstelling dat dit het de gebruiker (in dit geval de PinC-beheerder) eenvoudiger maakt.

In de praktijk maakt dit het ons echter knap lastiger. Stel dat we het stukje HTML uit ons eerdere voorbeeld, netjes voorzien van regeleinden en insprongen, gebruiken in het Description-veld van de bronnentabel, dan is het niet onze code, maar wel onderstaand stukje code, dat uiteindelijk door de webbrowser getoond zal worden:

```
<p>Op basis van Rijksregistergegevens krijgen we zicht op:</p><br/>
<br/>
<ul><br/>
	<li>het aantal private huishoudens en hun type</li><br/>
	<li>het aantal personen in private huishoudens en hun positie in het huishouden</li><br/>
	<li>het aantal personen in collectieve huishoudens</li><br/>
</ul>
```

Los van het feit dat bovenstaande code nooit zonder kleerscheuren door een validator raakt (zie volgend hoofdstuk), levert het ook volgend belabberd resultaat op, met veel ongewenste blanco regels:

> <p>Op basis van Rijksregistergegevens krijgen we zicht op:</p><br/>
> <br/>
> <ul><br/>
> 	<li>het aantal private huishoudens en hun type</li><br/>
> 	<li>het aantal personen in private huishoudens en hun positie in het huishouden</li><br/>
> 	<li>het aantal personen in collectieve huishoudens</li><br/>
> </ul>

De enige manier om dit ongewenste resultaat te vermijden, is alle regeleinden (en tabs) uit ons HTML-fragment te verwijderen. Swing voegt dan geen extra br-tags in.

In de HTML-velden van de bronnentabel kunnen we dus jammer genoeg geen overzichtelijk opgemaakte HTML-code gebruiken, maar zijn we gedoemd om er een onoverzichtelijk rommeltje van te maken:

```
<p>Op basis van Rijksregistergegevens krijgen we zicht op:</p><ul><li>het aantal private
huishoudens en hun type</li><li>het aantal personen in private huishoudens en hun positie
in het huishouden</li><li>het aantal personen in collectieve huishoudens</li></ul>
```

Bij langere HTML-fragmenten (zoals vaak in het Description-veld) wordt het daardoor bijzonder lastig om achteraf de tekst aaan te passen, doordat je door de bomen het bos niet meer ziet.

## Samenvatting

- **Whitespace** is een overkoepelende term voor (gewone) spaties, tabs en regeleinden. Je mag al deze tekens gebruiken of combineren binnen tags en tussen elementen.
- Binnen een tag gebruiken we whitespace om de attributen te scheiden van de elementnaam en van elkaar.
- Tussen elementen gebruiken we optionele whitespace om het HTML-document overzichtelijker te maken.
- De optionele whitespace tussen de elementen wordt door de browser genegeerd.
- Binnen een tekstblok (bv. binnen een alinea, een kopje, een lijstitem of een tabelcel) zal de webbrowser alle whitespace reduceren tot één enkele spatie.<br/><br/>
- In de tekst kun je nog andere soorten spaties gebruiken, al naargelang de noden: vaste spaties, em-spaties, en-spaties, etc.<br/><br/>
- In de HTML-velden van de bronnentabel gebruik je beter geen regeleinden en plaats je alle elementen achter elkaar. Anders voegt Swing ongewenste blanco regels in.

___
Volgend hoofdstuk: [HTML-validators](10_validators.md)
