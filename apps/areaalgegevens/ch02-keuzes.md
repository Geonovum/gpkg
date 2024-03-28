# Keuzes

Tijdens de verkenning zijn een aantal keuzes gemaakt voor het int

De belangrijkste keuzes:

## Machine-leesbare identifiers vs. Mens-leesbare aliassen.

De behoefte was om de concepten en enumeraties op te nemen in de Geopackage met

1.  de machine-leesbare URI’s (met daarin UUID’s van de concepten,
    bijvoorbeeld), en daarnaast het opnemen van een mens-leesbare naam (alias).

In de Geopackage standaard wordt voor de objecten die worden een identifier in
de gpkg_contents gedefineerd als:

A human-readable identifier (e.g. short name) for the table_name content

D.w.z. dat UUID’s in de table_name worden geplaatst en mens-leesbare identifier.

Deze lijn is doorgetrokken en heeft geleid tot

|                  | table                        | Machine-leesbaar (Identifier) | Mens-leesbaar (name alias) |
|------------------|------------------------------|-------------------------------|----------------------------|
| Object           | gpkg_contents                | table_name                    | identifier                 |
| Attribuut        | gpkg_data_columns            | column_name                   | name                       |
| Relaties         | gpkgext_relations            | *Toe te voegen*               | relation_name              |
| Waardenlijst     | gpkg_data_column_constraints | value                         | description                |
| Attribuutwaarden | gpkg_data_column_constraints | value                         | description                |

## Eenheid van waarden

*Geopackage heeft geen mechanisme voor het vastleggen van een eenheden van
attribuutwaarden van een kolom. De metadata-extensie voorziet niet in het
vastleggen van eenheid, wel in andere Metadata gegevens. Er zijn verschillende
alternatieven met de voor/nadelen verkend o.m.*

*Uiteindelijk is voor de pragmatische aanpak gekozen door het opnemen van een
eenheid als postfix na een underscore (‘_’) in de kolomnaam.*

## Enumeraties

Belangrijk aspect bij het uitwisselen van areaalgegevens tussen opdrachtnemer en
opdrachtgever is de gegevensvalidatie, ofwel een vaste lijst met enumeraties
waaruit een opdrachtnemer kan kiezen voor het vullen van de attributen.
Geopackage biedt hier een standaardmechanisme voor in de data constraints
kolommen.

## Relaties

vastleggen via GeoPackage extensie Related Tables

![Afbeelding met tekst, diagram, schermopname, Plan Automatisch gegenereerde
beschrijving](media/e3d9c3e282fe77e71a0fa8cd0f64fe7c.png)
