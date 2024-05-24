# Keuzes

Tijdens de verkenning zijn een aantal keuzes gemaakt voor het integreren van de
gegevens conform bovenstaande tabel in Geopackage formaat.

De belangrijkste keuzes worden hieronder beschreven.

## Machine-leesbare identifiers vs. Mens-leesbare aliassen.

De wens was om concepten en enumeraties op te nemen in de Geopackage met
machine-leesbare URI’s of UUIDs en tegelijkertijd een mensleesbare naam (alias)
toe te voegen. In de Geopackage-standaard is de definitie van kolom *identifier*
in de tabel gpkg_contents gedefinieerd als:

>   "Een menselijk leesbare identifier (bijv. een korte naam) voor de inhoud van
>   de table_name." (*vertaald*)

en kolom *table_name* in de tabel *gpkg_contents* gedefinieerd als:

>   "De naam van de daadwerkelijke inhoudstabel (bijv. tegels, kenmerken of
>   attributen) of weergave" (*vertaald*)

We maken hier een andere keuze om (zie paragraaf 3.1.1):

-   de UUID en URI’s van een concept op te nemen in kolom *table\_*name van
    tabel gpkg_contents, dus table_name
    *https://data.crow.nl/imbor/def/1ea4ee45-672d-477d-9bb4-6961418fe601* of
    *1ea4ee45-672d-477d-9bb4-6961418fe601*.

-   De mensleesbare naam van het concept of objecttype op te nemen in de
    identifier, dus identifier ‘Weg’ of ‘Verkeerseiland’.

Deze benadering is consequent toegepast en heeft geleid tot opname van de
gegevens, zoals hieronder beschreven.

|                  | Geopackage tabel             | Machine-leesbaar (Identifier) | Mens-leesbaar (name alias) |
|------------------|------------------------------|-------------------------------|----------------------------|
| Object           | gpkg_contents                | table_name                    | identifier                 |
| Attribuut        | gpkg_data_columns            | column_name                   | name                       |
| Relaties         | gpkgext_relations            | *toe te voegen*               | relation_name              |
| Waardenlijst     | gpkg_data_column_constraints | value                         | description                |
| Attribuutwaarden | gpkg_data_column_constraints | value                         | description                |

## 

## Eenheid van waarden

In het Geopackage-formaat ontbreekt een ingebouwd mechanisme voor het vastleggen
van eenheden van attribuutwaarden in een kolom. Hoewel de metadata-extensie geen
specifieke ondersteuning biedt voor eenheden, kunnen andere metadata wel worden
vastgelegd. Verschillende alternatieven, elk met hun voor- en nadelen, zijn
overwogen:

1.  Het opnemen van de eenheid in de definitie.

2.  Het toevoegen van een aparte kolom voor de eenheid van het attribuut.

3.  Het vastleggen van relaties tussen attributen en eenheden met behulp van de
    Related Tables-extensie.

4.  Het opnemen van eenheidsinformatie in het begrippenkader, waarbij de
    definitie en andere metadata van het concept kunnen worden opgevraagd aan de
    hand van de objectidentifier.

Uiteindelijk is gekozen voor een pragmatische aanpak door de eenheid als postfix
toe te voegen aan de kolomnaam, gescheiden door een underscore ('_'). Dit is
echter een tijdelijke oplossing; een meer gestructureerde aanpak zou kunnen zijn
om de Geopackage-standaard uit te breiden, bijvoorbeeld door het opnemen van
eenheden in de Metadata-extensie of door dergelijke gegevens onder te brengen in
een aparte extensie.

## Enumeraties

Een essentieel aspect van het uitwisselen van areaalgegevens tussen
opdrachtnemers en opdrachtgevers is gegevensvalidatie. Dit omvat het gebruik van
een vastgestelde lijst met enumeraties waaruit een opdrachtnemer kan kiezen bij
het invullen van attributen.

Geopackage biedt hiervoor een standaardmechanisme via de table
*gpkg_data_columns_constraints*. Hiermee kunnen waardenlijsten worden opgenomen
in de Geopackage, waardoor het mogelijk is om na het invoeren van gegevens te
controleren of een toegevoegde waarde geldig is.

## Relaties

De GeoPackage-extensie Related Tables wordt gebruikt om relaties tussen
verschillende concepten vast te leggen. Met deze extensie kunnen tabellen worden
gemaakt die gerelateerd zijn aan andere tabellen binnen hetzelfde
GeoPackage-bestand. Hierdoor kunnen complexe relaties tussen verschillende
concepten worden gemodelleerd en opgeslagen, wat nuttig is voor het organiseren
van gegevens met meerdere niveaus van verbondenheid. Het gebruik van deze
extensie vereenvoudigt het beheer van gegevens en maakt het mogelijk om
uitgebreide en gestructureerde datasets te maken binnen een enkel
GeoPackage-bestand.

![Afbeelding met tekst, diagram, schermopname, Plan Automatisch gegenereerde
beschrijving](media/e3d9c3e282fe77e71a0fa8cd0f64fe7c.png)
