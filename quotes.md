# Quotes

Om bioscopen, theaters en andere uitgaansgelegenheden, waar soms geen of weinig afbeeldingen van zijn, verder te 'illustreren', hebben we quotes uit krantenartikelen op [Delpher](https://www.delpher.nl/) verzameld. Zo hebben we Wikidata items verbonden met Delpher artikelen, op de volgende manier:

```
<http://www.rotterdamspubliek.nl/quote/5>
	a schema:Quotation ;
	schema:isPartOf [
		a schema:Article ;
		rdf:value <https://resolver.kb.nl/resolve?urn=ddd:010953155:mpeg21:a0365> ;
		schema:isPartOf "Het vrĳe volk" ;
		schema:datePublished "1958-03-27"^^xsd:date ;
	] ;
	schema:about wd:Q74835984 ;
	schema:text "Onze buurtgenoten kwamen wel in troepen op de krantenzaal af. Ze namen de hele garderobe in beslag en vulden die grote krantenzaal; ze zaten er gezellig en nu en dan lazen ze ook wel eens wat, vooral de advertenties. Dat advertentielezen nam sterk toe in de crisisjaren met de grote werkloosheid. Tot de mobilisatie in '39 is het in de krantenzaal heel druk gebleven."^^xsd:string .
```

De quotes zijn te vinden in het bestand [quotations.ttl](data/quotations.ttl).

De volgende query, die je draait op [deze sparql endpoint](https://druid.datalegend.net/menno/rotterdamspubliek/sparql/rotterdamspubliek) toont het aantal quotes per locatie:

```
PREFIX schema: <http://schema.org/>
PREFIX dct: <http://purl.org/dc/terms/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
SELECT ?location ?locationlabel (COUNT(DISTINCT(?quote)) AS ?nrofquotes) WHERE {
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
			wd:Q1684522 	#jazzclub
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
		?quote a schema:Quotation .
		?quote schema:about ?location .
	}
} 
GROUP BY ?location ?locationlabel
ORDER BY ASC(?nrofquotes)
LIMIT 1000
```
