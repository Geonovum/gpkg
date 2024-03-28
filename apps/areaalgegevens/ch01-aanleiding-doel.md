# Aanleiding en doel

## Aanleiding

De afgelopen decennia hebben (semi-)overheidsinstanties steeds vaker hun
specifieke informatiebehoeften vastgelegd in datamodellen, die vervolgens aan de
markt worden voorgelegd. Dit proces omvat het lezen van het model door de
opdrachtnemer, het produceren van gegevens op basis van dit model en het
terugleveren ervan aan de opdrachtgever voor validatie. Deze gegevens worden dan
geïntegreerd in het achterliggende applicatielandschap.

Echter, er is behoefte ontstaan aan een uniforme structuur om te voorkomen dat
organisaties hun behoeften in willekeurige datamodellen specificeren. Dit heeft
geleid tot de ontwikkeling van de NEN 2660-2, een concreet topmodel dat
organisaties in staat stelt om hun specifieke behoeften uniform te structureren
en als model aan de markt voor te leggen.

## Doel

De opdracht omvatte het onderzoeken van de haalbaarheid van het gebruik van
Geopackage als uitwisselingsformaat voor areaalgegevens. Voor meer informatie
over Geopackage, zie de handreiking Geopackage van Geonovum.

In de opdracht lag de focus op het modelleren van informatiebehoeften, met name
gericht op objecttypen, attributen en relaties, in het Geopackage-formaat. Het
doel was om te bepalen of Geopackage geschikt is voor het uitwisselen van
dergelijke gegevens, vooral in vergelijking met het traditionele gebruik van het
Esri-bestandsformaat 'file geodatabase' door Provincie Zuid-Holland en Provincie
Gelderland. Geonovum was betrokken bij deze opdracht vanwege haar rol als
kennisorganisatie op het gebied van geo-standaardisatie in Nederland.

## Aanpak

De aanpak omvatte het selecteren van een specifieke scope uit het NEN 2660-2
model, zoals weergegeven in onderstaande tabel. Deze selectie vormde de basis
voor het modelleren van informatiebehoeften in het Geopackage-bestandsformaat.

| **Objecttypen** | **Attributen**                                          | **Relaties**                      |
|-----------------|---------------------------------------------------------|-----------------------------------|
| Identifier      | Identifier                                              | Identifier                        |
| Naam            | Naam                                                    | Naam                              |
| Definitie       | Definitie                                               | Definitie                         |
|                 | Kardinaliteit                                           | Kardinaliteit                     |
|                 | Eenheid                                                 | (De)compositie-relatie objecttype |
|                 | Datatype                                                | Associatie-relatie geometrietype  |
|                 | Domein (incl. domeinwaarden) Identifier Naam  Definitie | Associatie-relatie documenttype   |

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