# 10. HTML-validators

Een HTML-validator is een stukje software dat een HTML-document controleert en eventuele problemen rapporteert. Er wordt dan gecontroleerd of het HTML-document voldoet aan de regels.

Een veel gebruikte HTML-validator is de validator van het World Wide Web Consortium (W3C). Je kunt de software downloaden en op je eigen computer runnen, maar als je maar af en toe een document wilt valideren, is het handiger om de online service te gebruiken.

Deze service is beschikbaar op **https://validator.w3.org** en kan verschillende soorten documenten valideren, met inbegrip van HTML5 en XHTML.

Je kunt je HTML-document uploaden op https://validator.w3.org/#validate_by_upload.

De validator geeft verschilldende soorten boodschappen: foutboodschappen (rood), waarschuwingen (geel) en informatieve boodschappen (groen).

De fouten moet je zeker oplossen als je een HTML-document wilt maken dat aan de standaarden voldoet.

De waarschuwingen zijn niet per se fout, maar bij voorkeur probeer je ze toch best te vermijden.

De informatieve boodschappen mag je negeren. Eventueel kun je de boodschappen filteren (met de knop _Message Filtering_), zodat de informatieve boodschappen verborgen worden.

De validator geeft telkens het regel- en kolomnummer aan waar de fout werd vastgesteld. Maar let op: dat betekent niet noodzakelijk dat de fout zich op die plaats bevindt. Het probleem kan zich ook eerder in het document hebben voorgedaan. Als je bijvoorbeeld ergens een begintag vergeten bent, dan zal de validator dat mogelijks pas kunnen vaststellen op de plaats waar de eindtag staat.

**We raden je ten sterkste aan om je HTML-documenten te valideren. Zeker als beginnend HTML-gebruiker zul je bijna onvermijdelijk fouten maken. Een validator helpt je om die fouten op te sporen en te corrigeren.**

> *N.B.: het internet staat vol met HTML-documenten die niet volgens de regels gemaakt zijn en die een hele resem foutmeldingen zullen opleveren wanneer je ze door een validator haalt. Moderne webbrowsers zijn echter bijzonder tolerant en zien heel veel fouten door de vingers, waardoor documenten met fouten tóch goed weergegeven worden. Maar fouten en slordigheden kunnen er wel voor zorgen dat je in bepaalde gevallen niet het bedoelde resultaat krijgt. Zo kunnen CSS-regels vaak niet goed toegepast worden wanneer je HTML-document niet correct gestructureerd is.*

Let op: een validator is een bijzonder handig hulpmiddel voor het vinden van fouten in HTML-documenten, maar een validator ontdekt mogelijks niet alle foutsituaties. Wanneer je bijvoorbeeld een entity reference zou gebruiken terwijl de betreffende entity niet (voor)gedefinieerd is (bv. `&PinC;`), dan wordt dat niet door de W3C-validator gemeld. Een webbrowser zal hier ook geen foutmelding geven, maar de betreffende entity reference letterlijk weergeven (dus: &PinC;).

## Enkele mogelijke foutboodschappen

### Element ul not allowed as child element of ul

Een foutmelding die je eventueel kunt tegenkomen, is deze:

> Error Element ul not allowed as child of element ul in this context.

Deze foutmelding betekent dat je binnen een ongenummerde lijst (ul) opnieuw een ongenummerde lijst hebt gebruikt. Wellicht wou je een lijst met meerdere niveaus creëren, maar op deze manier mag dat niet. De lijst van het tweede niveau mag niet rechtstreeks binnen een ul- of ol-element staan, maar moet binnen een lijstitem (li-element) staan.

Met ‘child element’ wordt bedoeld een element dat direct ondergeschikt is aan een ander element. Zo is een li-element altijd een child element van een ul- of ol-element.

Analoog wordt met de term ‘parent element’ het omgekeerde bedoeld: het ul- of ol-element is het parent element van het li-element.

### No p element in scope but a p end tag seen

Een andere mogelijke foutmelding is deze:

> Error No p element in scope but a p end tag seen.

Hier heb je een grote fout gemaakt: je hebt een eindtag gebruikt (`</p>`) zonder bijbehorende begintag (`<p>`).

Dit kan twee dingen betekenen: óf de eindtag is correct, en je bent de begintag vergeten (voeg in dat geval op de juiste plaats de begintag toe), óf de eindtag mag daar inderdaad niet staan (verwijder hem in dat geval).

## Een veel voorkomende informatieve boodschap

### Trailing slash on void elements

Wanneer je de voorbeelden in deze handleiding nauwgezet hebt gevolgd en een HTML-document valideert met de W3C-validator, dan zul je ongetwijfeld deze informatieve melding enkele keren zien terugkomen:

> Info Trailing slash on void elements has no effect and interacts badly with unquoted attribute values.

Wat betekent dit precies?

Het gaat over de schuine streep aan het einde (_trailing slash_) van elementen zonder inhoud (_void elements_), bijvoorbeeld bij `<br/>`, `<meta charset="utf-8"/>` of `<link type="text/css" rel="stylesheet" href="style/moreinfo.css"/>`.

De validator informeert ons dat deze schuine streep:

- geen effect heeft (_has no effect_);
- slecht interageert met attribuutwaarden zonder aanhalingstekens (_unquoted attribute values_).

De schuine streep heeft inderdaad geen effect, in die zin dat het voor een moderne webbrowser niet uitmaakt of de schuine streep er wel of niet staat. Een webbrowser zal `<br>` op dezelfde manier interpreteren als `<br/>`.

Maar we hebben uitgelegd waarom we die schuine streep tóch plaatsen, namelijk:

- daardoor maken we van ons HTML-document een XHTML-document: in XML is de schuine streep immers verplicht bij inhoudloze elementen;
- een XHTML-document is veel beter gestructureerd en daardoor veel overzichtelijker dan een ‘gewoon’ HTML-document dat niet aan de strengere vormvereisten van XML voldoet;
- door de schuine streep zie je in één oogopslag dat het om een element zonder inhoud gaat (je weet dan dat je niet naar een bijbehorende eindtag op zoek moet gaan).

Attribuutwaarden zonder aanhalingstekens? Mag dat dan?

In ‘gewone’ HTML mag dat inderdaad, maar enkel voor attribuutwaarden die geen spaties bevatten. We hanteren echter de principes van XHTML en plaatsen daarom attribuutwaarden _altijd_ tussen aanhalingstekens. Omdat we altijd aanhalingstekens gebruiken, moeten we ons ook geen zorgen maken over het feit dat de schuine streep aan het einde van elementen zonder inhoud slecht interageert met attribuutwaarden zonder aanhalingstekens.

Als je een attribuutwaarde niet tussen aanhalingstekens plaatst, dan zou de webbrowser de schuine streep kunnen zien als behorend tot de attribuutwaarde.

Nu je dit allemaal weet, begrijp je dat je deze informatieve boodschap van de validator met een gerust hart mag negeren. Schenk er dus verder geen aandacht aan.

## Een mogelijke waarschuwing

### Empty heading

Een mogelijke waarschuwing is deze:

> Warning Empty heading.

Hier heb je een tussenkopje gebruikt zonder inhoud, bv. `<h3></h3>`. Dit is niet zinvol. Je verwijdert dit dus beter.

## Samenvatting

- Gebruik een **HTML-validator** om te controleren of je HTML-document correct gestructureerd is en aan de regels voldoet.
- Een veel gebruikte validator is die van het World Wide Web Consortium op **[https://validator.w3.org](https://validator.w3.org/#validate_by_upload)**.
- Corrigeer de eventuele fouten (en waarschuwingen) die door de validator ontdekt worden.
- Informatieve boodschappen mag je negeren (maar je kunt er wel iets uit leren).<br/><br/>
- Let op: wanneer de validator geen enkele foutmelding geeft, is dat nog altijd geen garantie dat je HTML-document in orde is. Zo kan het document misschien nog ongeldige entity references bevatten.

___
Volgend hoofdstuk: [HTML in Stories](11_stories.md)
