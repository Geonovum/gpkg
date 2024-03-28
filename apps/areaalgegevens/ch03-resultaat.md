# Resultaat

## Referentie-implementatie

Aan de hand van de volgende voorbeelddata is een proefimplementatie van
areaalgegevens in Geopackage uitgevoerd.

Tabel Voorbeelddata IMBOR eigenschappen

|                 | **IMBOR - kolom**     | **IMBOR - waarde**                                                                 |
|-----------------|-----------------------|------------------------------------------------------------------------------------|
| Concept         | FysiekObjectURI       | <https://data.crow.nl/imbor/def/1ea4ee45-672d-477d-9bb4-6961418fe601>              |
|                 | FysiekObjectLabel     | Weg                                                                                |
| Attribuut(vorm) | EigenschapURI         | <https://data.crow.nl/imbor/def/2b1b2ffa-6cdd-4c54-b8c3-475757e347ff>              |
|                 | EigenschapLabel       | lengte                                                                             |
|                 | Datatype              | xsd:decimal                                                                        |
|                 | Eenheid               | M                                                                                  |
|                 | VastewaardeLijstURI   | <https://data.crow.nl/imbor/def/bf86855c-e30b-4005-bacf-7e5683b531dd>              |
|                 | VastewaardelijstLabel | WegType                                                                            |
|                 | VastewaardeURI        | <https://data.crow.nl/imbor/id/domeinwaarden/23736fbb-f07a-480a-91af-75dc0965b159> |
|                 | VastewaardeLabel      | Nationale stroomweg                                                                |

Tabel Voorbeeldata IMBOR relaties

|         | **IMBOR - kolom** | **IMBOR - waarde**                                                                                                                          |
|---------|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| Subject | SubjectURI        | [https://data.crow.nl/imbor/def/1ea4ee45-672d-477d-9bb4-6961418fe601\|](https://data.crow.nl/imbor/def/1ea4ee45-672d-477d-9bb4-6961418fe601 |
|         | SubjectLabel      | Weg                                                                                                                                         |
|         |                   |                                                                                                                                             |
|         |                   |                                                                                                                                             |
| Relatie | heeftRelatieURI   | [https://w3id.org/nen2660/def\#hasPart](https://w3id.org/nen2660/def#hasPart)                                                               |
|         | heeftRelatieLabel | hasPart                                                                                                                                     |
|         |                   |                                                                                                                                             |
|         |                   |                                                                                                                                             |
| Object  | ObjectURI         | https://data.crow.nl/imbor/def/3414e1e7-fd9f-4e93-b44a-e3bf5df08314                                                                         |
|         | ObjectLabel       | Verkeerseiland                                                                                                                              |
|         |                   |                                                                                                                                             |
| Relatie | heeftRelatieURI   | [https://w3id.org/nen2660/def\#isDescribedBy](https://w3id.org/nen2660/def#isDescribedBy)                                                   |
|         | heeftRelatieLabel | [isDescribedBy](https://w3id.org/nen2660/def#isDescribedBy)                                                                                 |
|         |                   |                                                                                                                                             |
|         |                   |                                                                                                                                             |
| Object  | ObjectURI         | <https://data.crow.nl/imbor/def/8ab0ac02-ee94-4086-9b14-d53ede3c4101>                                                                       |
|         | ObjectLabel       | Inwinningsinformatie                                                                                                                        |
|         |                   |                                                                                                                                             |

Het template Geopackage is beschikbaar via

Hierna volgt een beschrijving van de verschillende NEN2660-2 onderdelen en hoe
deze in de template Geopackage zijn opgenomen.

### Sub/object

Structuur van sub/object wordt gedefinieerd in eigen feature tables. In deze
tabellen worden de instanties in records vastgelegd.

![Afbeelding met tekst, software, Lettertype, nummer Automatisch gegenereerde
beschrijving](media/30032b627fd4d133360f4d10a43a4826.png)

N.B. bij attribuut lengte van Weg wordt de eenheid ‘M’ als postfix opgenomen.

**gpkg_contents**

Definitie van sub/objecten wordt opgenomen in tabel gpkg_contents; de
Identifier-URI van het sub/object wordt opgenomen in de kolom ‘identifier’ van
tabel gpkg_contents

![Afbeelding met tekst, Lettertype, nummer, schermopname Automatisch
gegenereerde beschrijving](media/ce935eae4d99076662f183c6befea7e6.png)

![Afbeelding met tekst, Lettertype, lijn, nummer Automatisch gegenereerde
beschrijving](media/d5923f1c015b95e4c38c3c174c20372d.png)

### Attributen

Attributen, zijnde de kenmerken/eigenschappen van de sub/objecten worden
gedefinieerd in de tabel **gpkg_data_columns**:

-   (mensleesbare) naam van de eigenschap wordt opgenomen in kolom
    ‘column_name’.

-   (machineleesbare) identifier-URI wordt opgenomen in kolom ‘name’.

-   

![Afbeelding met tekst, Lettertype, lijn, nummer Automatisch gegenereerde
beschrijving](media/21c51f9456e15d7a72b7149bca6468f1.png)

![Afbeelding met tekst, Lettertype, lijn, nummer Automatisch gegenereerde
beschrijving](media/8e7f97d95235f7b86af34204dc751f40.png)

### Enumeraties

AEnumeraties (constraints op toegestane attribuutwaarden) worden gedefineerd in
de tabel gpkg_data_column_constraints:

-   (mensleesbare) naam van de waardenlijst of attribuutwaarde wordt opgenomen
    in kolom ‘description’.

-   (machineleesbare) identifier-URI wordt opgenomen in kolom ‘value’

Waardenlijst krijgt in de constraint_name een ‘_’ als prefix.

### Relaties

Voor relaties tussen sub/objecten wordt de extensie Related Tables op GeoPackage
toegepast.

De specificaties van de Related Tables extensie zijn vastgelegd in
<http://www.opengis.net/doc/IS/gpkg-rte/1.0>

![Afbeelding met tekst, schermopname, Lettertype, nummer Automatisch
gegenereerde beschrijving](media/2f458ef763d89f951a63c98b92d5bde5.png)

*Definiëren van de extensie*

Related Tables Extension wordt gedefinieerd in tabel **gpkg_extensions**; voor
elke relatie wordt een aparte *mapping table* aangemaakt, en elke relatie als
record toegevoegd aan de tabel gpkg_extensions.

![Afbeelding met tekst, Lettertype, lijn, nummer Automatisch gegenereerde
beschrijving](media/24b5a75724b2708378a663c10ada5daf.png)

![Afbeelding met tekst, schermopname, nummer, Lettertype Automatisch
gegenereerde beschrijving](media/9136c107dff8279c30d38a8083b856a1.png)

![Afbeelding met tekst, schermopname, nummer, Lettertype Automatisch
gegenereerde beschrijving](media/9136c107dff8279c30d38a8083b856a1.png)

In elke mapping table worden de instanties van de relaties in records
vastgelegd.

*Definiëren van de relaties*

De relaties worden gedefinieerd in de tabel **gpkg_ext_relations**. Voor elke
relatie wordt opgenomen:

-   naam van de kolom met de identificatie in de brontabel (base_table)

-   naam van de kolom met de identificatie van de doeltabel (related_table)

-   naam van de relatie

-   naam van de *mapping tabel* met de instanties van de relatie.

![Afbeelding met tekst, Lettertype, nummer, schermopname Automatisch
gegenereerde beschrijving](media/9ceaea77d5ed375ff4b0af041d90c244.png)

![Afbeelding met tekst, Lettertype, lijn, schermopname Automatisch gegenereerde
beschrijving](media/90d4bdcce41b1a655f08c5d85e43c09c.png)

## Change requests Geopackage standaard

Hieruit volgen twee wijzigingsverzoeken voor de Geopackage standaard:

-   Uitbreiden standaarden met de mogelijkheid voor het opnemen van eenheid als
    metadata bij de kolommen.

-   Uitbreiden standaard met de mogelijkheid voor het opnemen van een URI van
    een relatie.
