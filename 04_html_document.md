# 4. De structuur van een HTML-document

## Root element

Elk HTML-document volgt in grote lijnen eenzelfde structuur: het ganse document zit vervat in een **html**-element. Omdat alles begint bij dat ene element, noemen we dit het _root element_. Root is het Engels voor wortel (het beginpunt van een boomstructuur).

## Doctype

Vóór het root element kan er nog een _document type declaration_ staan. Een document type declaration lijkt wat op een HTML-tag, maar is het niet. De functie ervan is om aan de browser (en eventueel aan andere software) kenbaar te maken om welk soort document het gaat (bijvoorbeeld welk ‘dialect’ van HTML).

## Head en body

Het html-element bevat twee subelementen: een **head**-element gevolgd door een **body**-element. Het head-element bevat allerlei info over het document; het body-element bevat de eigenlijke inhoud van het document, zoals tekst en afbeeldingen.

```
<!DOCTYPE html>
<html lang="nl-NL">

	<head>
		<meta charset="utf-8"/>
		<title>Loop van de bevolking – Statbel</title>
		<link type="text/css" rel="stylesheet" href="style/moreinfo.css"/>
	</head>

	<body>

		<h1>Inleiding</h1>

		<p>Tekst</p>

	</body>

</html>
```

Het voorbeeld hierboven maakt de algemene structuur van een HTML-document duidelijk. Binnen het html-element zie je duidelijk twee afgescheiden delen: de head en de body.

De insprongen en de blanco regels zijn er om de structuur visueel duidelijk te maken, maar ze zijn niet echt noodzakelijk. We raden je echter aan om ieder niveau wat verder in te springen en om telkens een blanco regel te laten tussen de grote onderdelen van het document. Op die manier behoud je makkelijker het overzicht.

We bekijken het document wat nader:

```
<!DOCTYPE html>
```

Helemaal bovenaan zie je de document type declaration. Let wel: het eigenlijke document begint pas met het root element op de volgende regel. Eerdere versies van HTML gebruikten een veel langere en complexere doctype declaration, maar in HTML5 is het vrij simpel. Als je wat rondkijkt op het internet zul je ongetwijfeld heel wat HTML-documenten aantreffen zonder doctype declaration. De kans is bijzonder groot dat een browser het document ook zonder doctype declaration correct zal weergeven, maar in principe moet bovenstaande doctype declaration aanwezig zijn aan het begin van elk HTML5-document.

```
<html lang="nl-NL">
```

Bij het root element, het html-element, zie je een **lang**-attribuut staan. Een lang-attribuut vertelt aan de webbrowser in welke taal de tekst binnen het element geschreven is. Als attribuutwaarde gebruik je hier een ISO-taalcode, eventueel aangevuld met een koppelteken en een ISO-land- of ‑regiocode. In het voorbeeld hierboven zie je `nl-NL`, waarmee standaard Nederlands bedoeld wordt.

De land- en taalcodes zijn gedefinieerd in twee ISO standaarden: [ISO 639-1](https://nl.wikipedia.org/wiki/Lijst_van_ISO_639-codes) voor de taalcodes (twee kleine letters) en [ISO 3166-1](https://nl.wikipedia.org/wiki/ISO_3166-1) voor de landcodes (twee hoofdletters).

Het lang-attribuut bij het html-element bepaalt de taal voor het ganse document. In het geval enkele delen van het document in een andere taal geschreven zouden zijn, dan zou je bij de betreffende elementen weer een lang-attribuut met een andere taalcode kunnen plaatsen.

De aanwezigheid van een lang-attribuut kan er bijvoorbeeld voor zorgen dat voorleessoftware de tekst op de juiste manier uitspreekt, dat vertaalsoftware de tekst correct vertaalt, of dat woorden op een correcte manier worden afgebroken aan het einde van een regel.

```
<head>
  <meta charset="utf-8"/>
  <title>Loop van de bevolking – Statbel</title>
  <link type="text/css" rel="stylesheet" href="style/moreinfo.css"/>
</head>
```

Binnen het **head**-element in het voorbeeld hierboven vinden we drie andere elementen.

Met het **meta**-element maakten we al eerder kennis. Het meta-element in dit voorbeeld vertelt de webbrowser dat het document UTF-8-geëncodeerd is. Op webpagina’s worden meta-elementen ook voor heel wat andere zaken gebruikt, met andere attributen. De meest voorkomende attributen zijn dan `name` en `content`, maar voor de PinC-bijlagen hebben we die attributen voorlopig niet nodig.

Het **title**-element bevat de titel van het document. Hier plaats je een (voldoende korte) tekst, die in de titelbalk van de webbrowser weergegeven zal worden. Een webbrowser kan deze titel ook gebruiken als bestandsnaam wanneer je de webpagina vanuit de browser opslaat of exporteert naar PDF.

Het **link**-element koppelt een externe CSS-stylesheet aan het HTML-document. De stijldefinities in dat CSS-bestand (`moreinfo.css` in de submap `style`) zullen gebruikt worden om het HTML-document vorm te geven (lettertype, tekengrootte, marges, kleuren, etc.).

Binnen de head kunnen nog meer meta- en link-elementen staan en kunnen ook nog CSS-stijlen gedefinieerd worden met een **style**-element. De head kan ook JavaScript-code bevatten in een **script**-element. Het voorbeeld hierboven is een eenvoudig head-element zoals in de HTML-bijlagen die we in PinC gebruiken.

```
<body>

  <h1>Inleiding</h1>

  <p>Tekst</p>

</body>
```

Binnen het **body**-element staat de eigenlijke inhoud die in het browservenster wordt weergegeven. In het voorbeeld hierboven bestaat die inhoud uit een kopje van niveau 1 en een alinea met platte tekst.

## Commentaar

Behalve een doctype declaration, HTML-elementen en inhoud kan een HTML-document ook nog **commentaar** bevatten.

Commentaar zal niet door de webbrowser weergegeven worden en zal ook niet afgedrukt worden of in de PDF-export verschijnen.

Door commentaar in de broncode van een HTML-document te plaatsen, kun je voor jezelf of voor anderen extra informatie toevoegen als toelichting bij bepaalde delen van het document, of kun je bepaalde delen van het document verbergen zonder ze uit de broncode te halen.

Een stukje commentaar begint altijd met `<!--` en eindigt altijd met `-->`. Daarbinnen plaats je wat je wilt: zowel tekst als HTML-tags zijn toegelaten, eventueel op meerdere regels. Het enige wat niet toegestaan is, zijn twee opeenvolgende koppeltekens (`--`).

```
<!-- Dit is een stukje commentaar. -->

<!-- Commentaar kan eventueel
uit meerdere regels bestaan. -->

<!--<h1>Inleiding</h1>-->
```

Commentaren worden niet door de webbrowser weergegeven, maar houd er rekening mee dat een gebruiker de commentaren wel kan zien door de broncode van de pagina te bekijken. Houd de commentaarteksten dus relevant en plaats er geen gevoelige of geheime informatie (zoals wachtwoorden) in.

## Samenvatting

- Een HTML-element bestaat uit een **root-element** (html) met daarbinnen twee grote delen: de **head** en de **body**.
- Vóór het root element daat mogelijks nog een **document type declaration** die aangeeft om welk soort document het gaat.
- Binnen het **head**-element staat informatie die betrekking heeft op het ganse document en kan een koppeling gemaakt worden met externe bestanden (bv. CSS of Javascript).
- Binnen het **body**-element staat de eigenlijke inhoud van het document (tekst en afbeeldingen).
- Om het even waar in het document kan er ook **commentaar** staan, die niet door de browser wordt weergegeven (maar die wel zichtbaar is wanneer je de broncode bekijkt).

### HTML-elementen in dit hoofdstuk

`body`: document body: de eigenlijke inhoud van het document

`head`: document head: informatie die betrekking heeft op het volledige document, en eventuele (links naar) CSS-stijlen en Javascript

`html`: root element (dit element bevat het volledige HTML-document) – attribuut: `lang` (taalcode)

`link`: koppeling naar extern bestand – attributen: `href` (locatie van het extern bestand), `rel`, `type`

`meta`: meta-informatie – attributen: `charset` (tekenset, codering), `content`, `name`

`title`: titel van het document

___
Volgend hoofdstuk: [Opsommingen (lijsten)](05_opsommingen.md)
