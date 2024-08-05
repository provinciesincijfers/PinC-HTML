# 3. Speciale tekens

Vóór we verdergaan met de bespreking van de verschillende HTML-elementen en ‑attributen die je kunt gebruiken in PinC, moeten we eerst iets kwijt over tekensets, accentletters en andere speciale tekens.

## Tekensets: van ASCII naar Unicode

In den beginne was er de **ASCII**-code, waar je misschien ooit nog eens over gehoord hebt. ASCII (_American Standard Code for Information Interchange_) is een manier om letters, cijfers en leestekens voor te stellen in computersystemen. Elk teken wordt daarbij voorgesteld door een getal.

De ASCII-code gebruikt de getallen 0 t.e.m. 127 en bevat daarmee dus 128 verschillende tekens. Dat moet ruimschoots volstaan, dachten de Amerikanen die de code in de jaren 60 van de vorige eeuw ontwierpen. In ASCII krijgt elke hoofdletter, elke kleine letter, elk cijfer, elk leesteken en de spatie een eigen code. Dat zijn samen minder dan 128 tekens. De resterende codes worden voor speciale doeleinden gebruikt. Zo bevat de ASCII-code ook codes voor een tab, een regeleinde, een backspace, een ‘escape’, enz.

Voor andere talen dan Engels volstonden 128 codes echter niet. Daarom kwamen er al gauw meerdere uitbreidingen met 256 in plaats van 128 codes. Maar de ‘standaard’ ontaardde al snel in aparte substandaarden voor verschillende regio’s: één voor West-Europese talen, één voor Oost-Europese talen, één met het Russisch alfabet, enz. Microsoft en Apple gebruikten bovendien hun eigen uitbreidingen, die niet onderling compatibel waren. Daardoor kreeg bijvoorbeeld de é (e met accent aigu) op een Windows-computer een andere code toebedeeld dan op een Apple-computer, waardoor een Franse tekst niet zomaar tussen beide systemen uitgewisseld kon worden. In al deze tekensets werd één byte (8 bits) per karakter gebruikt.

Gelukkig hebben we ondertussen de **Unicode**-standaard, die zowat elk alfabet en elk teken bevat dat ergens op Aarde gebruikt wordt. Unicode is dus een bijzonder uitgebreide tekenset. Unicode is nog steeds gebaseerd op ASCII: de ons vertrouwde letters, cijfers en leestekens hebben nog steeds dezelfde codes als in ASCII (codes 0-127), maar daarnaast bevat Unicode tal van bijkomende accentletters, wiskundige, technische en andere symbolen, en andere alfabetten zoals Grieks, Cyrillisch, Thais, Hiragana en Katakana (Japans), Chinese, Japanse en Koreaanse karakters, etc. Unicode wordt nog steeds verder ontwikkeld en uitgebreid. Daarbij wordt erover gewaakt dat elke nieuwe versie nog steeds backwards compatible is met eerdere versies. Op het ogenblik van dit schrijven (medio 2024) bevat Unicode versie 15.1 zo’n 149.813 verschillende karakters en 161 _scripts_ (alfabetten). Daarbij zitten ook alfabetten die niet van links naar rechts, maar van rechts naar links geschreven worden, zoals Hebreeuws of Arabisch.

Let op: dat de Unicode-tekenset 149.813 verschillende tekens bevat, betekent _niet_ dat je al die tekens ook in de praktijk kunt gebruiken in je HTML- of andere documenten. Welke tekens beschikbaar zijn hangt immers af van welk **lettertype** je gebruikt. Elk lettertype (_font_) bevat slechts een kleine subset van de volledige Unicode-tekenset, omdat het anders onwerkbaar zou worden en omdat je de meeste van die tekens toch nooit nodig hebt.

Wil je meer over Unicode weten of wil je al die rare tekens eens nader bekijken, neem dan een kijkje op de Unicode-website op **https://unicode.org**.

### UTF-8

Vandaag de dag is Unicode de standaard tekenset in Windows, Linux en andere populaire besturingssystemen. Afhankelijk van de noden zijn er verschillende manieren om al die tekens voor te stellen. De meest gebruikte manier is de **UTF-8**-_encoding_. UTF-8 (8-bit _Unicode Transformation Format_) is een tekencodering (_encoding_) met variabele lengte: de 128 vertrouwde ASCII-tekens worden in UTF-8 nog steeds voorgesteld door één byte (8 bits) maar andere, minder vaak gebruikte tekens kunnen door 2, 3 of meer bytes voorgesteld worden (16, 24 of meer bits).

Moderne webbrowsers gaan er doorgaans standaard van uit dat een HTML-document UTF-8-geëncodeerd is, maar dat is een instelling die de gebruiker eventueel kan aanpassen. Om er zeker van te zijn dat de webbrowser ons HTML-document correct interpreteert en dus de accentletters en andere speciale tekens correct weergeeft, plaatsen we bovenaan in het HTML-document deze **meta**-tag:

```
<meta charset="utf-8"/>
```

Alle meta-elementen worden binnen het head-element geplaatst, dat algemene informatie over het HTML-document bevat. Meer daarover leer je in een volgend hoofdstuk.

## Accentletters en andere speciale tekens

Er zijn verschillende manieren om accentletters en andere speciale tekens in een HTML-document op te nemen. Vóór de opkomst van Unicode moest je daarvoor verplicht gebruikmaken van **character entity references** zoals bijvoorbeeld `&eacute;` voor een kleine letter e met een accent aigu (é), of `&copy;` voor een copyright-symbool (©).

Maar tegenwoordig is het veel eenvoudiger: in je HTML-document kun je nu gelijk welk Unicode-teken gebruiken. Dat maakt de HTML-broncode alvast een stuk leesbaarder. Kijk maar naar onderstaande voorbeelden:

```
<p>Slechts &eacute;&eacute;n of twee &lsquo;idee&euml;n&rsquo; worden correct ge&iuml;nterpreteerd!</p>

<p>Slechts één of twee ‘ideeën’ worden correct geïnterpreteerd!</p>
```

Zeg nu zelf, welk van beide versies verkies je? De eerste alinea, die vol staat met character entity references, of de tweede, waarin de references vervangen werden door de overeenkomstige Unicode-karakters?

### Character entity references

Een charcter entity reference is een verwijzing (reference) naar een **character entity**. HTML heeft een hele reeks ingebouwde character entities: entiteiten die een karakter voorstellen. Elke entity heeft een naam, die zodanig gekozen is dat je de betekenis ervan makkelijk kunt onthouden. Zo stelt de entity met de naam `eacute` de kleine letter e met accent aigu voor (in het Engels: acute) en de entity `iuml` de kleine letter i met trema (in het Engels, overgenomen van het Duits: umlaut). De entities `lsquo` en `rsquo` staan dan weer voor _left single quote_ (linker enkel aanhalingsteken) en _right single quote_ (rechter enkel aanhalingsteken).

Een **character entity reference** herken je aan de **ampersand** (`&`) en de **puntkomma** (`;`), met daartussen de naam van de betreffende character entity.

Namen van entities zijn **hoofdlettergevoelig**. Met andere woorden: het verschil tussen kleine letters en hoofdletters is van belang. Zo is bijvoorbeeld `&auml;` de kleine letter a-trema (ä) en is `&Auml;` de hoofdletter A-trema (Ä).

De complete lijst met alle beschikbare entities in HTML5 (de huidige versie van HTML) is veel te uitgebreid om hier op te sommen. Je kunt een kijkje nemen op [www.w3schools.com](https://www.w3schools.com/charsets/ref_html_entities_a.asp) voor een overzicht.

Maar het goede nieuws is dat we hier dus in de praktijk geen gebruik van moeten maken, doordat we evengoed de Unicode-tekens kunnen gebruiken, waardoor de HTML-broncode goed leesbaar blijft.

Er zijn slechts een handjevol uitzonderingen voor karakters waar we tóch verplicht zijn om met een character entity reference te werken, namelijk voor tekens die een speciale betekenis hebben in HTML, zoals het kleiner-dan-teken, dat het begin van een tag markeert, en de ampersand, die het begin van een character entity reference markeert. In de praktijk gebruiken we deze drie character entity references wanneer we de overeenkomstige tekens nodig hebben in de tekst van ons HTML-document:

`&amp;` en-teken, Engels: ampersand (&)\
`&gt;` groter dan, Engels: greater than (>)\
`&lt;` kleiner dan, Engels: less than (<)

Schrijf dus niet: `D&A`, maar wel: `D&amp;A`.\
Schrijf niet: `<100`, maar wel: `&lt;100`.

Verder is er nóg een character entity reference die in de praktijk wel eens van pas kan komen:

`&nbsp;` vaste spatie (Engels: no-break space)

Een vaste spatie gebruik je ter vervanging van een gewone spatie op plaatsen waar je wilt vermijden dat er naar een volgende regel overgegaan wordt, bijvoorbeeld wanneer je een getal en de erbij horende eenheid wilt samenhouden (bv. `150&nbsp;m`). In theorie kun je het ook zonder character entity reference doen en een vaste spatie gewoon als Unicode-teken opnemen (met Alt+0160), maar het nadeel is dat je dan in de broncode geen verschil meer ziet met een gewone spatie (maar in een goede teksteditor zul je tóch op een of andere manier een verschil zien).

### Character references

Behalve met character *entity* references, die aan de hand van een makkelijk te onthouden naam verwijzen naar een voorgedefinieerde character entity, kun je ook gebruikmaken van **character references**. Een character reference verwijst rechtstreeks naar een Unicode-karakter, zonder de omweg via een character entity. De verwijzing kan op twee manieren gebeuren: aan de hand van de **decimale code** van het karakter of aan de hand van de **hexadecimale code** van het karakter.

In de Unicode-tabellen op https://www.unicode.org/charts kun je voor om het even welk teken de bijbehorende code achterhalen. Daar worden de codes in hexadecimale vorm gegeven. Het zou ons hier te ver leiden om daar gedetailleerd op in te gaan, en daarom beperken we ons tot de essentie: de term ‘hexadecimaal’ verwijst naar een talstelsel met niet tien, maar zestien cijfers. De zestien hexadecimale cijfers zijn 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E en F. Hierbij staat de letter A voor de (decimale) waarde 10, de B voor 11, de C voor 12, de D voor 13, de E voor 14 en de F voor 15. In plaats van de hoofdletters A-F worden vaak ook kleine letters (a-f) gebruikt.

Vaak zul je zien dat naar een Unicode-teken verwezen wordt met een hoofdletter U gevolgd door een plusteken en vier of meer hexadecimale cijfers. Zo wordt bijvoorbeeld met `U+00A9` het copyright-symbool bedoeld. Het hexadecimale getal A9 komt overeen met een decimale waarde van 169.

In HTML kun je een character reference herkennen aan een **ampersand** gevolgd door een **hekje** (`&#`), gevolgd door de code van het karakter en een **puntkomma**.

Een character reference lijkt dus een beetje op een character entity reference, maar in plaats van de naam van een entity staat er nu een hekje en een getal met de Unicode-waarde van het betreffende teken. Het getal kan zowel een decimaal getal als een hexadecimaal getal zijn. Om het verschil tussen beide duidelijk te maken, wordt een hexadecimaal getal ook nog eens voorafgegaan door een letter x.

In theorie maakt het niet uit of je bij de hexadecimale getallen hoofdletters of kleine letters gebruikt, maar we spreken af dat we in de praktijk altijd kleine letters gebruiken in character references, zowel voor de x als voor de hexadecimale cijfers.

Samengevat kun je het copyright-symbool in HTML op verschillende manieren coderen:

als Unicode-teken: ©\
als character entity reference: `&copy;`\
als character reference (decimaal): `&#169;`\
als character reference (hexadecimaal, zonder voorloopnullen): `&#xa9;`\
als character reference (hexadecimaal, met voorloopnullen): `&#x00a9;`

Zoals je in de voorbeelden kunt zien, maakt het bij een character reference ook niet uit of je voorloopnullen gebruikt of niet, bijvoorbeeld om een hexadecimaal getal met vier cijfers weer te geven. De character references `&#xa9;` en `&#x00a9;` zijn volkomen gelijkwaardig.

> Als je ooit een dynamisch Swing-rapport hebt geprogrammeerd, dan zul je je vast herinneren dat je daarbij in een character reference niet één, maar twee hekjes moest gebruiken (bv. `&##169;`). Vergeet dat echter zo snel mogelijk, want dat is _geen_ geldige manier om speciale tekens te coderen in HTML; in een rapport was het echter een noodzaak omdat de Swing-software een hekje daar interpreteert als het begin en het einde van een stukje SRL-code (_Swing Report Language_), tenzij je twee hekjes na elkaar gebruikte, in welk geval de twee hekjes door de Swing-software tot één hekje werden herleid en dat ene hekje vervolgens correct werd geïnterpreteerd door de webbrowser. Swing-rapporten worden momenteel uitgefaseerd en vervangen door Swing Stories, waardoor je binnen afzienbare tijd geen dubbele hekjes meer zult tegenkomen.

## Unicode-tekens

Hieronder een ongetwijfeld zeer onvolledige lijst van Unicode-tekens die van pas kunnen komen. Het gaat voornamelijk om tekens die niet op je toetsenbord staan en die je dus niet rechtstreeks kunt intypen.

Er zijn verschillende manieren om deze tekens via een omweg in je HTML-document te krijgen. Ervan uitgaande dat elke PinC-beheerder een Windows-computer gebruikt, geven we hieronder aan hoe je enkele van die tekens kunt intypen via Alt-codes. Een Alt-code werkt als volgt: je houdt de (linker) Alt-toets ingedrukt, terwijl je op het numerieke gedeelte aan de rechterkant van je toetsenbord de bijbehorende numerieke code typt. Wanneer je de Alt-toets weer loslaat, verschijnt het betreffende teken in je document. Op die manier kun je een groot aantal speciale tekens invoegen, maar niet elk denkbaar teken.

Je kunt allerlei speciale tekens ook invoegen in Microsoft Word (via Invoegen > Symbool) en ze vanuit het Word-document kopiëren naar het HTML-document (of je kunt ze natuurlijk ook kopiëren uit onderstaande lijst).

| Teken                           | Unicode | Alt-code | Omschrijving                                    |
| ------------------------------- | ------- | -------- | ----------------------------------------------- |
| <span style="font-family:serif;font-size:200%;line-height:50%">×</span> | U+00D7  | Alt+0215 | maalteken                                       |
| <span style="font-family:serif;font-size:200%;line-height:50%">–</span> | U+2013  | Alt+0150 | gedachtestreep                                  |
| <span style="font-family:serif;font-size:200%;line-height:50%">‘</span> | U+2018  | Alt+0145 | linker enkel aanhalingsteken                    |
| <span style="font-family:serif;font-size:200%;line-height:50%">’</span> | U+2019  | Alt+0146 | rechter enkel aanhalingsteken / weglatingsteken |
| <span style="font-family:serif;font-size:200%;line-height:50%">“</span> | U+201C  | Alt+0147 | linker dubbel aanhalingsteken                   |
| <span style="font-family:serif;font-size:200%;line-height:50%">”</span> | U+201D  | Alt+0148 | rechter dubbel aanhalingsteken                  |
| <span style="font-family:serif;font-size:200%;line-height:50%">‰</span> | U+2030  |          | promille                                        |
| <span style="font-family:serif;font-size:200%;line-height:50%">₂</span> | U+2082  |          | subscript 2                                     |
| <span style="font-family:serif;font-size:200%;line-height:50%">→</span> | U+2192  |          | pijl naar rechts                                |
| <span style="font-family:serif;font-size:200%;line-height:50%">≤</span> | U+2264  |          | kleiner dan of gelijk aan                       |
| <span style="font-family:serif;font-size:200%;line-height:50%">≥</span> | U+2265  |          | groter dan of gelijk aan                        |

In Word heb je nóg een mogelijkheid om speciale tekens in te typen. Als je de hexadecimale code van het teken kent, dan kun je die code gewoon intypen en vervolgens op Alt+X drukken. De code wordt dan vervangen door het overeenkomstige teken. Typ bijvoorbeeld `2265` gevolgd door Alt+X voor een ≥-teken of `D7` gevolgd door Alt+X voor een ×-teken.

## HTML-editors

Om een HTML-document te maken, heb je in principe geen speciale software nodig. In theorie volstaat een simpele teksteditor zoals **Kladblok**. Maar het gaat een stuk handiger met editors die meer mogelijkheden bieden, zoals bijvoorbeeld **[Notepad++](https://notepad-plus-plus.org)**.

In tegenstelling tot Kladblok maakt Notepad++ gebruik van **syntax highlighting** (_syntaxiskleuring_). Dat betekent dat de editor bijvoorbeeld een tag, een attribuutnaam of een attribuutwaarde herkent en in verschillende kleuren weergeeft. Dat maakt het werken met HTML veel overzichtelijker.

Bepaalde editors kunnen je ook helpen met het creëren van HTML-code en zullen bijvoorbeeld een geopend element automatisch afsluiten.

> *Belangrijk: welke editor je ook gebruikt, zorg er altijd voor dat je HTML-bestand opgeslagen wordt in **UTF-8**-codering. Op die manier zorg je ervoor dat alle accentletters en andere speciale tekens straks correct weergegeven worden in een webbrowser.*
>
> In Windows Kladblok gaat dat als volgt: onderaan in het dialoogvenster _Opslaan als_ kies je UTF-8 als codering.
>
> In Notepad++ kies je UTF-8 in het menu Tekenset.

### Let op met HTML-bijlagen editeren in Studio!

Ook de ingebouwde editor van Swing, waarmee je rechtstreeks platte tekst of HTML kunt intypen in bijvoorbeeld de velden van de bronnentabel, ondersteunt het gebruik van UTF-8.

Maar let op wanneer je de ingebouwde HTML-editor van Studio gebruikt om een HTML-bijlage of eender welk ander HTML-bestand te editeren. Die editor heeft namelijk twee erg vervelende eigenschappen:

- De editor herkent UTF-8-tekens (zoals é, ï, “, ” en –), **maar zal deze bij het opslaan vervangen door character (entity) references**! Een e met accent aigu wordt dus vervangen door `&eacute;`, een gedachtestreep wordt vervangen door `&##8211;`, etc. Dit is natuurlijk allerminst bevorderlijk voor de leesbaarheid.
- Bij het vervangen van UTF-8-tekens door character references **plaatst de editor verkeerdelijk twee hekjes in plaats van één**! Dit is een duidelijke bug in Swing, want het resultaat is dat de browser daardoor niet meer het juiste teken weergeeft, maar letterlijk &##8211; in plaats van een gedachtestreep, of &##8217; in plaats van een apostrof. De achterliggende oorzaak van deze bug is dat er wél twee hekjes gebruikt moeten worden in dynamische Swing-rapporten, omdat een hekje in rapporten het begin en einde van een stukje SRL-code markeert. Maar dat mag natuurlijk _alleen maar in dynamische rapporten_; in andere HTML-bestanden mag het beslist niet!

Daarom raden we je ten sterkste af om een HTML-bijlage te editeren in Studio. Veel beter is het om je HTML-document op je lokale computer te editeren met een teksteditor als Notepad++ en vervolgens het HTML-bestand te importeren in PinC.

## Samenvatting

- **Unicode** is een zeer uitgebreide tekenset van bijna 150.000 tekens, die zowat alle denkbare karakters bevat. Unicode bevat meerdere alfabetten, wiskundige, technische en andere symbolen en speciale tekens.
- Elk teken uit de Unicode-tekenset wordt geïdentificeerd aan de hand van een unieke **numerieke code**.
- Unicode is een voortzetting van **ASCII**, en ASCII is nu een subset van Unicode.
- We maken gebruik van **UTF-8** om Unicode-tekens voor te stellen.
- UTF-8 gebruikt één of meerdere bytes om de tekens voor te stellen.
- Welke tekens je in de praktijk kunt gebruiken, hangt af van de beschikbaarheid ervan in het **lettertype** dat je gebruikt.
- Bovenaan elk HTML-document plaatsen we een **meta**-tag om aan de browser duidelijk te maken dat ons document UTF-8 gebruikt.<br/><br/>
- **Character entity references** maken gebruik van voorgedefinieerde **entities** met makkelijk te onthouden namen om accentletters en andere speciale tekens in een HTML-document op te nemen.
- **Character references** verwijzen rechtstreeks naar de **numerieke code** van een teken. Dat kan op twee manieren: met een **decimale** of met een **hexadecimale** waarde.
- Je vindt tabellen met de codes van alle Unicode-tekens op https://www.unicode.org/charts.<br/><br/>
- Sla een HTML-document altijd op met **UTF-8-codering**.
- **Editeer HTML-bestanden niet in Studio** maar editeeer het bestand op je lokale computer en imorteer het daarna in PinC.

___
Volgend hoofdstuk: [De structuur van een HTML-document](04_html_document.md)
