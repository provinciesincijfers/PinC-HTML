# 11. HTML in Stories

## Inleiding

In tegenstelling tot Swing-rapporten, die een combinatie zijn van HTML en SRL (Swing Report Language), heb je voor het werken met Swing Stories in principe geen HTML-kennis meer nodig. Een Story maak je door allerlei soorten tegels te creëren in een grafische gebruikersomgeving. Sommige van die tegels bevatten gegevens uit de databank in de vorm van tabellen, grafieken of kaarten; andere tegels bevatten een stukje tekst.

In een teksttegel kun je een stukje tekst plaatsen, waarbij je gebruik kunt maken van verschillende soorten opmaak als vet, cursief, genummerde of ongenummerde lijsten, hyperlinks, enz. Je kunt de tekst opmaken als een alinea met platte tekst (Paragraph) of als tussenkopje (Heading 1, Heading 2 of Heading 3). Je kunt kleuren gebruiken, een ander lettertype kiezen of zelfs een eenvoudige tabel invoegen.

Dat alles gebeurt door de tekst in het Content-vak van de tegelinstellingen (Settings) van de teksttegel te plaatsen.

Je kunt de tekst rechtstreeks in dat vak typen, maar je kunt natuurlijk ook tekst plakken die je uit een ander document (bijvoorbeeld een Word-document) hebt gekopieerd.

Wanneer je tekst plakt, worden samen met de tekst ook opmaakkenmerken mee gekopieerd. Zo blijven vet en cursief bijvoorbeeld behouden.

_N.B.: wil je niet dat de opmaak mee gekopieerd wordt, gebruik dan ‘plakken als platte tekst’ (Shift+Ctrl+V)._

## Source

### HTML ‘onder de motorkap’

In de werkbalk van het Content-vak vind je een knop _Source_. Via die knop kun je wisselen tussen de normale weergave (zoals de tekst in de Story weergegeven wordt) en de onderliggende HTML-code.

Je kunt hiermee dus als het ware ‘onder de motorkap’ kijken en zien hoe de tekst gecodeerd is. Dit kan je helpen om ongewenste opmaak uit de tekst te halen, of om specifieke, gewenste opmaak toe te voegen.

Je ziet: ook al kun je in principe met Stories werken zonder je ook maar iets van HTML aan te trekken, je HTML-kennis kan hier toch weer van pas komen. In de praktijk is de kans overigens bijzonder groot dat je vroeg of laat aan de onderliggende HTML-code zult moeten sleutelen.

### Kopiëren en plakken uit Word (of een andere toepassing)

Als je bijvoorbeeld een stukje tekst uit een Word-document gekopieerd hebt en je gaat via de _Source_-knop eens naar de onderliggende HMTL-code kijken, dan kun je daar zowel vertrouwde als minder vertrouwde HTML-tags zien staan.

Een voorbeeld:

```
<h1>
    Kop 1<o:p></o:p>
</h1>
<h2>
    Kop 2<o:p></o:p>
</h2>
<h3>
    Kop 3<o:p></o:p>
</h3>
```

De elementen **h1**, **h2** en **h3** herken je meteen als kopjes van niveaus 1, 2 en 3. Je weet ook dat de optionele whitespace (regeleinden, spaties en/of tabs) na de begintags en voor de eindtags door de webbrowser genegeerd zal worden.

Maar wat zijn die vreemde `<o:p></o:p>` tags aan het einde van elk kopje?

Die tags mag je gerust verwijderen, maar als je ze toch laat staan, hebben ze verder geen effect op de Story. Ze zorgen er wel voor dat de HTML-broncode vervuild en dus minder goed leesbaar wordt.

Het zijn Microsoft Office-specifieke of Word-specifieke HTML-tags. Het is wellicht de eerste keer dat je tags van deze vorm ziet: de naam van het element (p) wordt zowel in de begintag als in de eindtag voorafgegaan door een o en een dubbele punt.

Zonder hier gedetailleerd op in te gaan, kunnen we verklappen dat dit de aanduiding is van een _namespace_. De naam van een X(HT)ML-element of ‑attribuut kan voorafgegaan worden door de naam van een namespace en een dubbele punt. De ‘o’-namespace staat hier voor ‘office’. Elementen en attributen uit die namespace volgen niet noodzakelijk dezelfde regels als elementen en attributen in standaard HTML.

Binnen Microsoft-toepassingen is de namespace ‘o’ gedefinieerd; de Microsoft-software past er zijn eigen regels op toe. Binnen Swing is die namespace niet gedefinieerd. Bij het weergeven van de Story zal de webbrowser dit daarom gewoon negeren: het is met andere alsof de betreffende tags of attributen er niet staan.

De HTML-code uit bovenstaand voorbeeld is met andere woorden volledig gelijkwaardig aan deze, veel compactere code:

```
<h1>Kop 1</h1>
<h2>Kop 2</h2>
<h3>Kop 3</h3>
```

Nog een voorbeeld:

```
<p class="MsoQuote">
    Citaat<o:p></o:p>
</p>
<p class="MsoNormal">
    <o:p> </o:p>
</p>
```

Hier zie je dat er een `class`-attribuut gebruikt wordt. De classnamen zijn weer Office-specifiek: `MsoQuote` en `MsoNormal` staan respectievelijk voor de ingebouwde Word-stijlen _Citaat_ (in het Engels: _Quote_) en _Standaard_ (in het Engels: _Normal_). Het prefix _Mso_ staat voor _Microsoft Office_.

Aangezien er binnen Swing geen CSS-classes met die namen gedefinieerd zijn, hebben ze binnen Stories geen effect. Daardoor wordt de bijbehorende opmaak ook niet overgenomen wanneer je dit stukje Word-tekst kopieert en in Stories plakt.

Bij de tweede alinea in het voorbeeld hierboven merk je nu ook dat er (in tegenstelling tot eerdere voorbeelden) een spatie staat tussen `<o:p>` en `</o:p>`. Er kan ook een vaste spatie staan (`&nbsp;`). Dat is de (oneigenlijke) manier waarop een blanco regel gecreëerd wordt in Microsoft Office-applicaties.

Samengevat is de HTML-code uit bovenstaand voorbeeld binnen Stories volledig gelijkwaardig aan deze code:

```
<p>Citaat</p>
<p> </p>
```

Een ander voorbeeld:

```
<p class="MsoNormal">
    <span style="font-size:16.0pt;line-height:116%;" lang="NL"><strong>Vereenvoudigen gebiedsrelaties<o:p></o:p></strong></span>
</p>
<p class="MsoNormal">
    <span lang="NL"><u>Visueel voorgesteld<o:p></o:p></u></span>
</p>
<p class="MsoNormal">
    <i><span style="font-family:&quot;Calibri&quot;,sans-serif;font-size:11.0pt;line-height:116%;mso-fareast-font-family:
    Calibri;" lang="NL"><strong>Meer uitleg<o:p></o:p></strong></span></i>
</p>
```

Bij deze voorbeelden werd in Word _directe opmaak_ toegepast. D.w.z. in het Word-document werd geen specifieke Word-stijl gebruikt – je krijgt dan de default-stijl _Standaard_ (`class="MsoNormal"`) –, maar werd de tekst bijvoorbeeld vet of cursief geplaatst, of werd de tekengrootte of het lettertype aangepast.

In de eerste alinea zie je dat een stukje vette tekst met **strong** gecodeerd is; in de tweede alinea is de tekst onderstreept met **u**, en in de derde alinea is de tekst gecursiveerd met **i**.

Je ziet ook **span**-elementen staan: bij het span-element in de eerste alinea is de tekengrootte ingesteld op 16 punt, met een regelafstand van 116%, en in de derde alinea is het lettertype Calibri gebruikt. In tegenstelling tot de stijlen _Citaat_ en _Standaard_ uit het eerdere voorbeeld wordt deze directe opmaak wél overgenomen in Stories, aangezien de bijbehorende CSS-opmaak nu rechtstreeks in de broncode staat (in het `style`-attribuut).

De span-elementen hebben in deze voorbeelden ook allemaal een `lang="NL"`-attribuut, waarmee aangegeven wordt dat het om een stukje tekst in het Nederlands gaat.

Uit bovenstaande voorbeelden wordt duidelijk dat de HTML-broncode van een teksttegel in Stories al snel heel onoverzichtelijk kan worden wanneer je tekst uit een Word-document kopieert. Door de vele tags en attributen en de afwezigheid van syntax highlighting zie je nauwelijks nog welke tekst er eigenlijk staat.

Als je dan ook nog eens een hoop get-statements aan de tekst toevoegt, wordt het helemaal een soep... Maar dat is een ander verhaal. Get-statements in Stories vallen buiten het bestek van deze HTML-handleiding.

> _Toch kunnen we alvast deze tip meegeven: als een get-statement niet het verwachte resultaat maar een foutmelding oplevert, bekijk dan zeker eens de onderliggende HTML-code. Zorg ervoor dat er binnen het get-statement geen enkele HTML-tag staat!_

### Tekst opschonen

Wanneer je in Stories tekst plakt die je uit een andere toepassing zoals bijvoorbeeld Microsoft Word hebt gekopieerd, dan zie je aan de onderliggende HTML-code dat er behalve de tekst allerlei zaken mee gekopieerd worden. Soms is dat gewenst, soms ongewenst. Als je de HTML-code in Stories aanpast, kun je proberen de broncode overzichtelijk te houden door de tekst op te schonen en ongewenste tags of attributen te verwijderen.

> _Let daarbij echter goed op dat je geen ongeldige HTML-code produceert. Zorg bijvoorbeeld dat elk element dat geopend wordt, ook weer netjes gesloten wordt. Stories gebruikt geen ingebouwde HTML-validator om de HTML-code te valideren._

Een andere aanpak is deze: in plaats van de tekst te **plakken** (met **Ctrl+V**) kun je er ook voor kiezen de tekst te **plakken als platte tekst** met **Shift+Ctrl+V**.

Kies je voor dat laatste, dan wordt enkel de eigenlijke tekst geplakt en wordt de oorspronkelijke opmaak _niet_ mee gekopieerd. De enige HTML-elementen die daarbij overblijven, zijn **p** en **br**. Je bent dan verlost van namespaces, classes, span-elementen, style-attributen, etc.

Je krijgt daardoor geen ongewenste veranderingen van tekengrootte, regelafstand of lettertype (wat een ongetwijfeld voordeel is), maar je bent dan helaas ook vet en cursief, subscript en superscript kwijt (wat weer een nadeel is). Bekijk eens de onderliggende HTML-code en ontdek het verschil. Aan jou om te oordelen wat het handigst werkt, naargelang de situatie.

## Samenvatting

- In Stories wordt tekst onderliggend gecodeerd als **HTML**.
- Je kunt wisselen tussen de normale weergave en de HTML-weergave via de _**Source**_-knop.
- Wanneer je tekst kopieert en plakt uit Word, bevat de HTML-broncode mogelijks **Word-specifieke elementen en attributen**.
- Die elementen en attributen hebben vaak geen enkel effect in Stories, maar ze vervuilen wel de HTML-broncode.
- Bepaalde soorten opmaak (zoals koppen en direct toegepaste opmaak als vet, cursief, tekengrootte en regelafstand) worden in Stories overgenomen.
- Andere soorten opmaak (zoals Word-stijlen, met uitzondering van koppen 1 t.e.m. 6) wordt niet in Stories overgenomen.
- Door te kiezen voor **plakken als platte tekst** in plaats van gewoon plakken gaat alle opmaak verloren en houd je enkel de tekst (en schone, niet-vervuilde HTML-code) over. Let op: herstel hier zelf vet en cursief, subscript en superscript waar nodig.<br/><br/>
- HTML-tags kunnen de werking van **get-statements** verstoren. Zorg ervoor dat er binnen een get-statement geen enkele HTML-tag staat.
