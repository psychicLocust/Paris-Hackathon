# Population surrounding an organization
## Declaring Geo Data in RDF
* We chose the [GeoSparQL Ontology](http://www.opengeospatial.org/standards/geosparql)
* For example a square grid unit for french population would be declared this way :
```
POLYGON ((9.19998656709306 41.374971504228512,9.199963208920366 41.376779624018049,9.20234379792694 41.376799664367191,9.202366964890617 41.37499155170341,9.19998656709306 41.374971504228512))
```
* As another example, a french organization would be declared this way :
```
<https://api.insee.fr/siren/siret/00708077300034>
	rdf:type org:OrganizationalUnit ;
 	rdfs:label "***ERS MEN AR***" ; 
	geo:hasGeometry ex:00708077300034Point .
ex:00708077300034Point a sf:Point;
	geo:asWKT "POINT(47.760546 -1.997442)"^^geo:wktLiteral.
```
## Converting population data
* First we download [this file](https://www.insee.fr/fr/statistiques/2520034) containing french population grid data
* Then we use [QGIS](https://qgis.org/) to convert it to ShapeFile and change projection from EPSG:3035 to EPSG:4326
* Then we export it from shapefile to CSV
* We use a [Java tool to convert it to RDF](https://github.com/alicela/CensusGrid-LOS) hacked from 
* 
## Converting organization data (SIRENE)
* We use [this repository](http://data.cquest.org/geo_sirene/last/)  containing files with added geolocalization information that has been produced [this way](https://www.insee.fr/fr/information/2509465) and this way
* We use a Python conversion script to convert it
* This Python script can be modified to add variables using [the W3C Organization Ontology](https://www.w3.org/TR/vocab-org/)