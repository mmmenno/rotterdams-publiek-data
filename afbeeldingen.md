# Afbeeldingen van theaters, bioscopen, etc.

Uit de collecties van het Stadsarchief Rotterdam en, in mindere mate, het Nationaal Archief, hebben we zo'n 300 afbeeldingen gelinkt aan Wikidata identifiers van bioscopen, concertzalen, etc. Die links staan in de volgende twee bestanden:

- [sa-rp-links.ttl](data/sa-rp-links.ttl) bevat koppelingen tussen afbeeldingen van het Stadsarchief Rotterdam en locaties
- [na-rp-links.ttl](data/na-rp-links.ttl) bevat koppelingen tussen afbeeldingen van het Nationaal Archief en locaties

Uit praktische overwegingen is een beperkte hoeveelheid metadata van genoemde afbeeldingen, waaronder de afbeeldingsurl, opgenomen in de volgende bestanden:

- [sa-rp-imgs.ttl](data/sa-rp-imgs.ttl) bevat metadata van afbeeldingen van het Stadsarchief Rotterdam
- [na-rp-images.ttl](data/na-rp-images.ttl) bevat metadata van afbeeldingen van het Nationaal Archief

De volgende query toont het aantal afbeeldingen per locatie (en ook de zalen zonder afbeeldingen). Volg [deze link](https://api.druid.datalegend.net/s/JZVwDfRr7) om de queryresultaten in de Rotterdams Publiek sparql endpoint te bekijken. In de queryresultaten zie je ook of er op Wikidata al een afbeelding bij de locatie is opgenomen.

```
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX dct: <http://purl.org/dc/terms/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX edm: <http://www.europeana.eu/schemas/edm/>
SELECT ?location ?locationlabel (COUNT(DISTINCT(?cho)) AS ?nrofimgs) (COUNT(DISTINCT(?wikiafb)) AS ?nrofwikiafb) WHERE {
	SERVICE <https://query.wikidata.org/sparql> {
		VALUES ?type { 
			wd:Q57660343 	#podiumkunstgebouw
			wd:Q41253 		#bioscoop
			wd:Q24354 		#theatergebouw
			wd:Q24699794 	#museumgebouw
			wd:Q207694 		#kunstmuseum
			wd:Q856584 		#bibliotheekgebouw
			wd:Q57659484 	#tentoonstellingsgebouw
			wd:Q1060829 	#concertgebouw
			wd:Q18674739 	#evenementenlocatie
			wd:Q15206070 	#poppodium
			wd:Q30022 		#koffiehuis
			wd:Q1228895 	#dancing
		}
		?location wdt:P31 ?type .
		OPTIONAL{
			?location wdt:P18 ?wikiafb .
		}
		?location wdt:P131 wd:Q2680952 .
		?location rdfs:label ?locationlabel .
		FILTER (lang(?locationlabel) = 'nl') .
	}
	OPTIONAL{
		?cho a edm:ProvidedCHO .
		?cho foaf:depiction ?imgurl .
		?cho dct:spatial ?location .
	}
} 
GROUP BY ?location ?locationlabel
ORDER BY DESC(?nrofimgs) DESC(?nrofwikiafb)
LIMIT 1000
```

