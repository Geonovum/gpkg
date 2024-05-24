# Aanleiding en doel

## Aanleiding

De afgelopen 10 jaar specificeren steeds meer (semi-)overheden hun
informatiebehoefte middels een datamodel richting de markt. De opdrachtnemer
leest het model in een applicatie, produceert data op basis van dit model en
levert deze terug. De opdrachtgever valideert de data (cf. het model) en bij
acceptatie wordt de data verwerkt in het achterliggende applicatielandschap. Om
te voorkomen dat organisaties hun behoeftes in arbitraire datamodellen
specificeren, is een concreet topmodel opgesteld: de NEN 2660-2. Deze maakt het
mogelijk dat organisaties hen specifieke behoeftes alsnog uniform kunnen
structureren en zo als model uitvragen aan de markt. In een provinciale context
is de uitwisseling van geometrie (als vectordata) essentieel. Denk aan punten,
lijnen, (multi)vlakken e.d. Deze vectordata in combinatie met tabellen laten
zich goed vastleggen in een geo-bestandsformaat. Vanuit praktisch oogpunt wordt
momenteel het gesloten Esri-bestandsformaat ‘’file geodatabase’’ toegepast als
uitwisselformaat door Provincie Zuid-Holland en Provincie Gelderland. Middels
deze verkenning willen de Provincies onderzoeken of het open
Geopackage-bestandsformaat zich hiervoor in de praktijk leent.

## Doel

De opdracht omvatte het onderzoeken van de haalbaarheid van het gebruik van
Geopackage als uitwisselingsformaat voor areaalgegevens. Voor meer informatie
over Geopackage, zie de handreiking Geopackage van Geonovum.

In de opdracht lag de focus op het modelleren van informatiebehoeften, met name
gericht op objecttypen, attributen, attribuutwaarden en relaties, in het
Geopackage-formaat. Het doel was om te bepalen of Geopackage geschikt is voor
het uitwisselen van dergelijke gegevens, vooral in vergelijking met het
traditionele gebruik van het Esri-bestandsformaat 'file geodatabase' door
Provincie Zuid-Holland en Provincie Gelderland. Geonovum was betrokken bij deze
opdracht vanwege haar rol als kennisorganisatie op het gebied van
geo-standaardisatie in Nederland.

## Aanpak

De aanpak omvatte het selecteren van een specifieke scope uit het NEN 2660-2
model.

Deze bestaat uit *Objecttypen* (o.a. fysieke objecttypen, documenttypen) waarvan
we *Kenmerken* op een specifieke manier ingevuld willen hebben. Fysieke objecten
willen we ook koppelen middels *Relaties* aan vereiste geometrieën en
documenten. Steeds vaker wordt ook de decompositie van een fysiek object
uitgevraagd. Zie onderstaande tabel voor een concrete scope van de
informatiebehoefte.

Deze selectie vormde de basis voor het modelleren van informatiebehoeften in het
Geopackage-bestandsformaat.

| **Objecttypen** | **Attributen**                                           | **Relaties**                      |
|-----------------|----------------------------------------------------------|-----------------------------------|
| Identifier      | Identifier                                               | Identifier                        |
| Naam            | Naam                                                     | Naam                              |
| Definitie       | Definitie                                                | Definitie                         |
|                 | Kardinaliteit                                            | Kardinaliteit                     |
|                 | Eenheid                                                  | (De)compositie-relatie objecttype |
|                 | Datatype                                                 | Associatie-relatie geometrietype  |
|                 | Domein (incl. domeinwaarden) Identifier  Naam  Definitie | Associatie-relatie documenttype   |

Het proces van het integreren van deze selectie uit de NEN2660-2 in Geopackage
omvatte de volgende stappen: het identificeren van gegevens die direct kunnen
worden opgenomen in Geopackage; het bepalen van elementen uit het model die met
enige aanpassing, zoals via een work-around, in Geopackage kunnen worden
opgenomen; en het vaststellen van elementen die niet compatibel zijn met het
Geopackage-formaat en mogelijk als suggestie tot verbetering aan OGC kunnen
worden voorgelegd.

Parallel aan het integeren van opstellen van een template Geopackage is de
ondersteuning en functionaliteit van GeoPackage in de opensource software QGIS
aangepast en uitgebreid. Zodoende kon het template Geopackage gelijk getest
worden. Voorts is gebruik gemaakt van DB Browser SQL Lite om de template
Geopackge op te stellen en te vullen.

De template Geopackages zijn getest door Gelderland en Zuid-Holland door het
vullen met eigen (IM)BOR data.
