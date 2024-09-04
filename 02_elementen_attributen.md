# 2. Elementen en attributen

HTML werkt met elementen en attributen. Wat elementen en attributen zijn, maken we duidelijk aan de hand van enkele voorbeelden:

## Elementen

```
<h1>Inleiding</h1>

<p>Hier komt de inleidende tekst van dit hoofdstuk.</p>
```

Bovenstaand HTML-fragment bestaat uit twee **elementen**: een **h1**-element (een kopje van niveau 1) en een **p**-element (een alinea met platte tekst).

Om een HTML-element te creëren, maken we gebruik van **tags**. De meeste elementen hebben een **begintag** en een **eindtag**, met daartussen een stukje tekst. Zowel de begintag als de eindtag herken je aan de **kleiner-dan-** en **groter-dan-tekens** (`<` en `>`).

In de begintag en de eindtag zie je de naam van het betreffende element staan, in de voorbeelden hierboven `h1` en `p`. De eindtag herken je aan de **schuine streep** (`/`) na het kleiner-dan-teken.

In het HTML-fragment hierboven zie je dus twee begintags staan: `<h1>` en `<p>`, met even verderop de bijbehorende eindtags: `</h1>` en `</p>`.

Wat tussen de begin- en de bijbehorende eindtag staat, is de **inhoud** van het element (in het Engels: de **content**).

Die inhoud bestaat vaak uit tekst, maar de inhoud van een element kan op zijn beurt ook weer andere elementen bevatten.

In een alinea kun je bijvoorbeeld met een **i**-element een stukje cursieve tekst opnemen, of met een **b**-element een stukje vette tekst. Je kunt cursief en vet ook combineren om vet-cursieve tekst te maken, bv.:

```
<p>Deze alinea bevat een stukje <i>cursieve tekst</i>, een stukje <b>vette tekst</b>,
en een stukje <b><i>vet-cursieve tekst</i></b>.</p>

<p>De <i><b>vet-cursieve tekst</b></i> zouden we ook op deze manier kunnen coderen.</p>
```

Wanneer je een element gebruikt binnen een ander element, zorg er dan voor dat het element dat je het eerst hebt geopend, het laatst afsluit.

Dit is dus fout:

```
<b><i>fout!</b></i>
```

Omdat we eerst een b-element hebben geopend en meteen daarna een i-element, moeten we straks (aan het einde van de vet-cursieve tekst) eerst het i-element afsluiten en pas daarna het b-element.

Zo moet het dus:

```
<b><i>goed!</i></b>
```

Niet alle elementen hebben een begin- én een eindtag. Sommige elementen kunnen namelijk geen inhoud hebben die je tussen de begin- en de eindtag zou plaatsen. Enkele veel voorkomende voorbeelden zijn het **br**-element (om binnen een kopje of een alinea naar een nieuwe regel over te gaan), het **img**-element (om een afbeelding in te voegen), of het **meta**-element (waarmee je aan het begin van een HTML-document allerlei metagegevens kunt opnemen).

Voor dergelijke elementen heb je maar één tag nodig, die tegelijkertijd als begin- en eindtag fungeert. Bij dergelijke elementen zet je een schuine streep aan het einde van de tag, net vóór het groter-dan-teken, bv.:

```
<h2>Dit is een kopje van niveau 2<br/>dat over 2 regels loopt.</h2>

<h2>Dit is een kopje van niveau 2<br/>
dat over 2 regels loopt.</h2>
```

De `<br/>`-tag zorgt ervoor dat de inhoud die volgt, op een nieuwe regel terecht komt. Voor de duidelijkheid kun je in de HTML-broncode ook een regeleinde toevoegen (zoals bij het tweede h2-element hierboven), maar dat is niet noodzakelijk. Je kunt evengoed alles achter elkaar zetten (zoals bij het eerste h2-element hierboven).

*N.B.: met de schuine streep net vóór het groter-dan-teken zorgen we ervoor dat het document blijft voldoen aan de regels van XHTML. In ‘gewone’ HTML zul je zien dat die schuine streep bij dergelijke elementen weggelaten wordt. Consequent een schuine streep gebruiken bij inhoudloze elementen heeft echter het voordeel dat je in één oogopslag ziet dat het om een element zonder inhoud gaat en dat je dus niet op zoek moet gaan naar een bijbehorende eindtag.*

### Vet en cursief

Dit moet je ook nog weten over vet en cursief: normaal gezien gebruiken we daar de elementen **b** (bold) en **i** (italic) voor. Maar je kunt ook twee alternatieve elementen tegenkomen: **strong** en **em**. Ook deze elementen worden door browsers als vet en cursief weergegeven.

Maar wat is dan het verschil? Het em-element (emphasis) wordt gebruikt om een stukje tekst te benadrukken. Standaard gebeurt dat door de tekst cursief weer te geven. Maar er zijn nog andere manieren denkbaar om tekst te benadrukken, bijvoorbeeld de tekst in een andere kleur of in een ander lettertype plaatsen, de tekst aanspatiëren, een achtergrondkleur gebruiken, etc. Dat effect kan dan bereikt worden door de gewenste stijl te definiëren met CSS. Het strong-element wordt gebruikt om een stukje tekst nog wat sterker te benadrukken. Standaard gebeurt dat door de tekst vet weer te geven, maar ook hier zijn er weer andere manieren denkbaar.

We spreken af dat we binnen PinC gewoon b en i gebruiken voor vet en cursief. Als we andere manieren van benadrukken nodig hebben, dan kunnen we daarvoor em en strong gebruiken en de gewenste opmaak opgeven via CSS.

_N.B.: wanneer je vet en cursief gebruikt in Stories en vervolgens de HTML-broncode bekijkt, zul je merken dat Stories het i-element gebruikt voor cursieve tekst en het strong-element voor vette tekst. Niet echt logisch, maar het werkt natuurlijk wel._

### Onderstrepen

Er is ook een element om tekst te onderstrepen: **u** (underline). We raden het gebruik ervan echter sterk af, omdat de gebruiker gewoon is dat (enkel) hyperlinks onderstreept weergegeven worden in HTML-documenten.

Een stukje onderstreepte tekst dat geen link is, werkt daarom contra-intuïtief. Heel wat gebruikers zullen de neiging hebben om op de tekst te klikken. We beschikken al over minstens twee manieren om tekst te benadrukken: vet en cursief. Tekst onderstrepen is daarom in de meeste gevallen helemaal niet nodig.

### Alinea’s

Eén van de elementen die je het vaakst zult gebruiken, is wellicht het **p**-element (_paragraph_), waarmee je een alinea creëert. Een alinea is een op zichzelf staand blokje tekst, dat doorgaans uit meerdere zinnen bestaat. Boven en onder elke alinea zal de browser automatisch witruimte toevoegen. Daardoor lijkt het alsof er tussen de alinea’s telkens een blanco regel staat. Met CSS kan die ruimte eventueel vergroot of verkleind worden. In Stories krijg je standaard ongeveer een halve witregel tussen de alinea’s.

Als je om een of andere reden een regeleinde wilt toevoegen binnen een alinea, dan kun je daarvoor een **br**-element (_line break_) gebruiken (`<br/>`).

Wat je _niet_ moet doen, is twee opeenvolgende br-elementen gebruiken om een blanco regel te creëren (`<br/><br/>`). In dat geval gebruik je beter gewoon een nieuwe alinea.

Wat je ook niet moet doen, is lege alinea’s gebruiken (`<p></p>` of `<p>&nbsp;</p>`) om extra witruimte te creëren. Houd je aan de voorziene witruimte tussen alinea’s en andere elementen.

## Attributen

Bij zowat elk HTML-element kun je één of meerdere **attributen** meegeven. Met een attribuut voeg je extra informatie toe aan het element. Attributen vertellen iets meer over het element in kwestie, of zorgen ervoor dat het er wat anders uitziet of zich wat anders gedraagt dan zonder het attribuut.

Attributen geef je altijd op bij een begintag, nooit bij een eindtag.

```
<h3 id="bijl">Bijlage</h3>
```

In bovenstaand voorbeeld zie je een kopje van niveau 3. Bij de begintag zie je één attribuut.

Een attribuut geef je aan door na de naam van het element een spatie te plaatsen en daarna de **naam** van het attribuut, een **gelijkheidsteken** en een **attribuutwaarde** tussen aanhalingstekens.

De naam van het attribuut in dit voorbeeld is dus **id** en de waarde ervan is `bijl`.

Een **id**-attribuut kun je bij om het even welk HTML-element plaatsen. De attribuutwaarde van een id-attribuut moet uniek zijn binnen het HTML-document, want de waarde van het id-attribuut wordt gebruikt om vanop een andere plaats naar het betreffende element te kunnen verwijzen.

Een ander voorbeeld:

```
<img src="images/logo.png" alt="bedrijfslogo"/>
```

In dit voorbeeld zie je een img-element met twee attributen (een **src**-attribuut en een **alt**-attribuut). Wanneer een element twee of meer attributen heeft, dan worden ze van elkaar gescheiden door een spatie.

In tegenstelling tot een id-attribuut kun je een src- of een alt-attribuut niet zomaar bij om het even welk element gebruiken. Deze attributen horen specifiek bij het img-element: de inhoud van het src-attribuut bepaalt hier welke afbeelding er geplaatst zal worden, en de inhoud van het alt-attribuut bepaalt de tekst die als alternatief weergegeven kan worden in plaats van de afbeelding (bijvoorbeeld door spraaksoftware voor blinden en slechtzienden, of wanneer de afbeelding om een of andere reden niet geladen kan worden).

In het voorbeeld zal de afbeelding `logo.png` (in een submap genaamd `images`) ingevoegd worden en zal als alternatieve tekst `bedrijfslogo` gebruikt worden.

De afbeelding zal ook weergegeven worden als je het alt-attribuut zou weglaten, maar een alt-attribuut is erg belangrijk voor de toegankelijkheid (bijvoorbeeld via spraaksoftware) en helpt daarnaast ook zoekmachines om te begrijpen wat er op de afbeelding te zien is. Gebruik daarom altijd een alt-attribuut bij een illustratieve afbeelding; bij een louter decoratieve afbeelding mag je het alt-attribuut weglaten.

Nog enkele belangrijke weetjes over attributen:

De volgorde van de attributen is van geen belang. Onderstaande voorbeelden zijn dus gelijkwaardig:

```
<img src="images/logo.png" alt="bedrijfslogo"/>
<img alt="bedrijfslogo" src="images/logo.png"/>
```

Bij eenzelfde element mag elk attribuut maar één keer voorkomen. Bij een img-element mag je dus maar één src-attribuut en één alt-attribuut plaatsen.

We spreken af dat we de attribuutwaarden altijd tussen **dubbele aanhalingstekens** plaatsen (`"..."`). In theorie mag je ook enkele aanhalingstekens gebruiken (`'...'`), maar in de praktijk doen we dat alleen in het uitzonderlijke geval waar we in de attribuutwaarde een dubbel aanhalingsteken nodig zouden hebben.

### Style en class

Naast het id-attribuut zijn er nog enkele ‘universele’ attributen die je bij zowat elk element kunt gebruiken, namelijk het **style**-attribuut en het **class**-attribuut.

Over het style-attribuut kunnen we kort zijn: we spreken af dat we het in de praktijk niet gebruiken, of enkel in héél uitzonderlijke omstandigheden. Met een style-attribuut kun je in de HTML-broncode rechtstreeks CSS-stijlinformatie meegeven (bv. lettertype, tekengrootte, marges, kleuren enz.).

Veel beter is het om die stijlinformatie op een onrechtstreekse manier aan te roepen. Dat doen we via een **class**-attribuut. De stijlinformatie zelf is op voorhand gedefinieerd en zit veilig afgescheiden in een apart CSS-bestand. Het voordeel van deze manier van werken is dat een aanpassing aan de stijlen automatisch toegepast wordt op alle HTML-elementen die van dezelde class gebruikmaken. Op die manier wordt gezorgd voor een uniforme opmaak over de verschillende HTML-documenten heen. Praktische voorbeelden van welke classes je (in HTML-bijlagen) kunt gebruiken, komen verderop in deze handleiding nog uitgebreid aan bod (zie: [Opsommingen (lijsten)](05_opsommingen.md)).

Wanneer je meer dan één class wilt toepassen op een element, dan kan dat! Je kunt maar één class-attribuut gebruiken, maar in plaats van één classnaam op te geven als attribuutwaarde, kun je ook een lijst van meerdere classnamen opgeven met telkens een spatie ertussen, bv.:

```
<li class="bold open">...</li>
```

Bovenstaand voorbeeld zal zowel de class `bold` als de class `open` toepassen op het li-element.

In Stories kun je ongewild style-attributen introduceren wanneer je tekst plakt uit andere toepassingen, bijvoorbeeld uit een Word-document. De eventueel in Word toegepaste tekenopmaak, zoals lettertype of tekengrootte, wordt dan overgenomen via een style-attribuut. Als je dat wilt vermijden, kun je de tekst plakken met Shift+Ctrl+V in plaats van met Ctrl+V (zie: [HTML in Stories](11_stories.md)). Op die manier wordt enkel de platte tekst geplakt, zonder de bijbehorende opmaak.

## Kleine letters of hoofdletters

In XHTML is de afspraak dat we voor namen van elementen en attributen altijd **kleine letters** gebruiken. In ‘gewone’ HTML mag je in principe ook hoofdletters gebruiken, en mag je zelfs hoofd- en kleine letters door elkaar mengen. Maar dat laatste is ontzettend slordig en wordt ten zeerste afgeraden. In deze handleiding gebruiken we XHTML, en dus kleine letters, in alle voorbeelden.

Ook voor attribuutwaarden spreken we af dat we bij voorkeur kleine letters gebruiken (bv. voor id’s of classnamen).

## Samenvatting

- Een **HTML-document** bevat **elementen**, die op hun beurt ook weer andere elementen kunnen bevatten en die het document **structuur** geven.
- De meeste elementen hebben een **begintag** en een **eindtag**.
- Die tags herken je aan de **kleiner-dan-** en **groter-dan-tekens**.
- De eindtag herken je aan de **schuine streep** na het kleiner-dan-teken.
- Tussen de begintag en de eindtag staat de eventuele **inhoud** (**content**) van het element.
- Sommige elementen kunnen geen inhoud hebben en worden voorgesteld door één tag die tegelijkertijd als begin- en eindtag fungeert. Dergelijke elementen herken je in XHTML aan de schuine streep vóór het groter-dan-teken.
- We gebruiken altijd kleine letters in de namen van de elementen.<br/><br/>
- Elk element kan één of meer **attributen** hebben, die **bijkomende informatie** bevatten over het element.
- Bij elk attribuut hoort een **attribuutwaarde**.
- Tussen de naam van het attribuut en de bijbehorende waarde staat een **gelijkheidsteken**.
- De attribuutwaarde staat tussen **dubbele aanhalingstekens**.
- De onderlinge volgorde van de attributen is van geen belang.
- Elk attribuut mag maar één keer per element opgegeven worden.
- Attributen worden van de elementnaam en van elkaar gescheiden door een **spatie**.
- We gebruiken altijd kleine letters in de namen van de attributen, en we gebruiken bij voorkeur kleine letters in de attribuutwaarden.<br/><br/>
- Bij zowat elk element kun je een **id**-attribuut en een **class**-attribuut gebruiken.
- De waarde van een id-attribuut moet **uniek** zijn binnen het HTML-document. Het id-attribuut wordt immers gebruikt om vanop een andere plaats naar het betreffende element te verwijzen.
- Het class-attribuut verwijst naar een voorgedefinieerde **CSS-stijl** die de opmaak van het element bepaalt.
- Je kunt **meerdere classes** combineren door één class-attribuut op te nemen met als attribuutwaarde een lijst van meerdere classnamen met telkens een spatie ertussen.
- Met een **style**-attribuut kun je de CSS-stijl van het betreffende attribuut definiëren, maar we spreken af dat we dat alleen maar doen bij wijze van zeer hoge uitzondering.

### HTML-elementen in dit hoofdstuk

`b`: vet (bold)

`br`: regeleinde binnen een alinea of kopje (break)

`em`: nadruk (emphasis), alternatief voor cursief

`h1`, `h2`, `h3`, ...: tussenkopjes niveau 1, 2, 3, ... Je kunt maximaal zes niveaus van tussenkopjes gebruiken: `h1` t.e.m. `h6`.

`i`: cursief (italic)

`img`: afbeelding – attributen: `alt` (alternatieve tekst), `src` (bestand)

`p`: alinea (platte tekst)

`strong`: sterke nadruk, alternatief voor vet

`u`: onderstreept (underlined)

___
Volgend hoofdstuk: [Speciale tekens](03_speciale_tekens.md)
