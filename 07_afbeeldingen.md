# 7. Afbeeldingen

In hoofdstuk 2 maakte je al kennis met het **img**-element, waarmee je een afbeelding kunt invoegen:

```
<img src="images/logo.png" alt="bedrijfslogo"/>
```

De inhoud van het src-attribuut bepaalt welke afbeelding er geplaatst zal worden, en de inhoud van het alt-attribuut bepaalt de tekst die als alternatief weergegeven kan worden in plaats van de afbeelding.

In het voorbeeld zal de afbeelding `logo.png` (in een submap genaamd `images`) ingevoegd worden en zal als alternatieve tekst `bedrijfslogo` gebruikt worden.

De afbeelding zal ook weergegeven worden als je het alt-attribuut zou weglaten, maar een alt-attribuut is erg belangrijk voor de toegankelijkheid (bijvoorbeeld via voorleessoftware) en helpt daarnaast ook zoekmachines om te begrijpen wat er op de afbeelding te zien is. Gebruik daarom altijd een alt-attribuut bij een illustratieve afbeelding; bij een louter decoratieve afbeelding mag je het alt-attribuut weglaten.

In het voorbeeld hierboven werd verwezen naar een afbeelding in een submap. De afbeelding die je invoegt, kan echter om het even waar staan, zelfs op een andere webserver. Bij `src` kun je een relatief of een absoluut pad opgeven (dat verwijst naar een afbeelding op dezelfde webserver als het HTML-document), maar je kunt ook een URL opgeven om te verwijzen naar een afbeelding die op een andere webserver staat, bv.:

```
<img src="https://swing.eu/style/custom/swing/images/swing-beeldmerk.svg" alt="Swing logo"/>
```

> *Let echter op met afbeeldingen die elders op het internet staan: daar heb je immers geen controle over. Op zekere dag kan de afbeelding verdwenen zijn, of vervangen zijn door een compleet andere afbeelding. Daarom beperken we ons beter tot afbeeldingen die we zelf hosten (d.w.z. die we zelf op onze eigen webserver plaatsen en waar we dus altijd zelf de controle over behouden).*

Door een `width`- en/of een `height`-attribuut op te geven, kun je de afbeelding schalen (vergroten of verkleinen). Geef je deze attributen niet op, dan wordt de afbeelding op de oorspronkelijke grootte getoond. Stel dat je de afbeelding te groot vindt en dat je ze wilt verkleinen, dan kun je een kleinere afmeting opgeven, uitgedrukt in pixels.

> *N.B.: browsers accepteren doorgaans ook relatieve afmetingen, opgegeven als percentages, maar strikt genomen is dat geen geldige HTML. Je kunt percentages wel geldig opgeven met CSS. Maar let op: een breedte van 50% betekent niet de helft van de oorspronkelijke afbeeldingsbreedte, maar de helft van de beschikbare ruimte tussen linker- en rechtermarge.*

Als je de afbeelding wilt schalen tot een breedte van 600 pixels, dan kan dat als volgt:

```
<img src="images/statbel_loop_schema.png" width="600" alt="loop van de bevolking – schema"/>
```

De afbeelding wordt hiermee weergegeven met een breedte van 600 pixels. Als de afbeelding oorspronkelijk groter of kleiner was, dan wordt de afbeelding verkleind of vergroot. De beeldverhoudingen blijven daarbij gelijk: ook de hoogte wordt met eenzelfde factor aangepast. Door zowel een waarde op te geven voor `width` als voor `height` kun je een afbeelding in principe vervormen (samendrukken of uitrekken), maar dat raden we ten sterkste af.

Los daarvan kunnen de afmetingen ook beïnvloed worden door de CSS-stijl die wordt toegepast. Met CSS kun je bijvoorbeeld ook een _maximale_ breedte en/of hoogte opgeven. Als de afbeelding kleiner is dan de opgegeven waarde, wordt de afbeelding op haar normale grootte weergegeven; is de afbeelding groter, dan wordt ze verkleind.

## Afbeeldingen in HTML-bijlagen op PinC

Voor wat betreft de HTML-bijlagen op PinC hebben we voorzien dat je eventuele afbeeldingen op twee manieren kunt plaatsen, namelijk:

- zonder kader, tegen de linkermarge;
- in een kader over de volledige breedte van de bijlage.

Wil je een afbeelding tegen de linkermarge plaatsen, plaats het img-element dan gewoon tussen twee tekstblokken (alinea’s, kopjes, lijstitems, ...) in:

```
<p>...</p>

<img src="images/statbel_loop_schema.png" width="600" alt="loop van de bevolking – schema"/>

<p>...</p>
```

Wil je een afbeelding centreren tussen linker- en rechtermarge, plaats het img-element dan (tussen twee alinea’s) binnen een **div**-element met een `class="image"`-attribuut.

Door `class="border"` toe te voegen aan het img-element, krijgt de afbeelding een kader.

```
<div class="image">
	<img src="images/verharding_schema.png" class="border" alt="verharding – schema"/>
</div>
```

Voorlopig zijn dat de twee manieren die we voorzien hebben om (grotere) afbeeldingen te plaatsen. Mocht er behoefte zijn aan andere manieren om afbeeldingen te plaatsen, dan zullen we op aanvraag de nodige CSS-stijl voorzien en de instructies hier toevoegen.

N.B.: div (_division_) is een element dat voor heel wat verschillende doeleinden gebruikt kan worden. Doorgaans wordt het voorzien van een class- of een id-attribuut om een onderscheid te maken tussen de verschillende soorten div-elementen, en wordt daaraan een CSS-stijl gekoppeld. In tegenstelling tot p-elementen kun je div-elementen binnen elkaar nesten, m.a.w. binnen een div-element kun je weer andere div-elementen creëren. Complexe webpagina’s zijn vaak opgebouwd uit heel veel verschillende div-elementen.

## Bestandsformaten voor afbeeldingen

Verder moet je nog het volgende weten over afbeeldingen: bepaalde afbeeldingsformaten, zoals bijvoorbeeld PNG of GIF, laten toe om delen van de afbeelding transparant te maken, zodat de achtergrondkleur van de webpagina zichtbaar wordt. Andere afbeeldingsformaten, zoals bijvoorbeeld JPG of BMP, hebben die eigenschap niet.

Ook is er een belangrijk onderscheid tussen enerzijds bitmap- of rasterafbeeldingen, zoals bijvoorbeeld PNG of JPG, en anderzijds en vectorafbeeldingen, zoals bijvoorbeeld SVG of EPS. Bitmapafbeeldingen bestaan uit pixels en zijn uitermate geschikt voor foto’s. Wanneer je een bitmapafbeelding vergroot of erop inzoomt, dan worden die pixels uitvergroot en wordt het beeld waziger. Vectorafbeeldingen daarentegen bestaan uit meetkundige objecten en zijn uitermate geschikt voor afbeeldingen die uit lijntekeningen en tekst bestaan. Wanneer je een vectorafbeelding vergroot of erop inzoomt, blijft de afbeelding er haarscherp uitzien!

Dat staat volledig los van HTML en CSS, maar het is iets waar je rekening mee moet houden wanneer je een afbeelding ontwerpt of laat ontwerpen voor gebruik in een webpagina.

## Samenvatting

- Een afbeelding wordt ingevoegd aan de hand van een **img**-element.
- Het `src`-attribuut bepaalt welke afbeelding er ingevoegd wordt.
- Met het `alt`-attribuut kun je een alternatieve tekst opgeven die de afbeelding kort beschrijft.
- Door de breedte (in pixels) op te geven met een `width`-attribuut kun je de afbeelding vergroten of verkleinen.<br/><br/>
- In de HTML-bijlagen voorzien we de afbeelding van een kader met een `class="border"`-attribuut.
- In de HTML-bijlagen voegen we een afbeelding in tussen twee tekstblokken.
- In de HTML-bijlagen plaatsen we afbeeldingen die we willen centreren binnen een **div**-element met een `class="image"`-attribuut.

### HTML-elementen in dit hoofdstuk

`div`: divisie (algemeen blok-element) – attribuut: `class`: classnaam

`img`: afbeelding – attributen: `alt` (alternatieve tekst), `class`: classnaam, `src` (URL of pad naar de afbeelding)

___
Volgend hoofdstuk: [Titels en tussenkopjes](08_koppen.md)
