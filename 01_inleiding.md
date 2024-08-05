# 1. Inleiding

## HTML, CSS en Javascript

De afkorting HTML staat voor _HyperText Markup Language_. HTML is _geen_ programmeertaal, maar een _markup_-taal: een manier om te beschrijven hoe webpagina’s gestructureerd zijn. Het aanbrengen van structuur houdt in: het markeren van kopjes, platte tekst, opsommingen of tabellen, wat vet of cursief moet staan, waar een hyperlink of een afbeelding komt, etc.

De bedoeling is daarbij uitdrukkelijk om structuur te scheiden van opmaak. De structuur bepaalt wat iets _is_, de opmaak bepaalt _hoe het eruit ziet_. Voor de opmaak (bv. lettertype, tekengrootte, regelafstand, marges, kleuren, uitlijning, randen, etc.) gebruiken we geen HTML, maar CSS (Cascading Style Sheets). Als je geen CSS gebruikt, dan wordt de webpagina weergegeven met een (ietwat saaie) standaard opmaak, die per browser wat kan verschillen.

Naast de structuur en de opmaak komt bij veel webpagina’s vaak (maar niet altijd) nog een derde element kijken: _interactiviteit_. Om een pagina interactief te maken, maken we doorgaans gebruik van Javascript (en dat is _wel_ een programmeertaal).

## HTML in PinC

In deze handleiding zullen we ons beperken tot pure HTML, zullen we CSS terloops vermelden waar nodig, en zullen we het helemaal niet meer hebben over Javascript.

PinC maakt gebruik van HTML (en CSS) bij:

- dynamische rapporten;
- enkele velden in de bronnentabel (metadata);
- HTML-pagina’s, bijvoorbeeld de bijlagen bij de metadata;
- teksttegels in Stories.

In deze handleiding zullen we geen aandacht meer besteden aan HTML in dynamische rapporten, aangezien de rapporten uitgefaseerd worden. Bestaande rapporten worden (voorlopig) nog wel aangepast, maar nieuwe rapporten worden niet meer gecreëerd. De rapporten worden vervangen door Stories.

In PinC maken we gebruik van HTML waar we grotere stukken tekst nodig hebben, bijvoorbeeld bij de metadata die we meegeven bij elke bron. Bij grotere stukken tekst is het handig om de tekst te kunnen indelen in meerdere alinea’s, om tussenkopjes te kunnen invoegen, om opsommingen te kunnen maken, om tabellen te kunnen invoegen of hier en daar een afbeelding te kunnen plaatsen. Daarnaast maken we ook gebruik van de mogelijkheid om tekst te benadrukken door middel van vet of cursief en om hyperlinks toe te voegen naar externe websites, naar bijlagen, etc.

Lang niet elk veld in de bronnentabel laat toe om met HTML te werken; in heel wat velden kun je alleen maar platte tekst invoegen, zonder enige vorm van structuur of opmaak. Enkel in de velden die HTML accepteren, kunnen we HTML gebruiken. Wanneer we heel veel tekst willen toevoegen, werken we met een HTML-bijlage: een aparte HTML-pagina waarin er in principe geen beperkingen zijn en waar we zowel de structuur als de opmaak helemaal naar onze hand kunnen zetten.

Dit is geen volledige handleiding HTML. We beperken ons tot de HTML-elementen en ‑attributen die nuttig of nodig zijn voor PinC.

Als je meer over HTML wilt weten, kun je onder andere terecht bij de [HTML-tutorial van w3schools.com](https://www.w3schools.com/html/default.asp).

## XHTML

De HTML-variant die we in deze handleiding en bij voorkeur ook in PinC gebruiken, is **XHTML**. XHTML combineert HTML met de strengere vormvereisten van XML (_eXtended Markup Language_). Maar maak je daar geen zorgen over. Als je de voorbeelden in deze handleiding volgt, werk je vanzelf met XHTML.

___
Volgend hoofdstuk: [Elementen en attributen](02_elementen_attributen.md)
