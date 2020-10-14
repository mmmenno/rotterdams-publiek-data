# Data Rotterdams Publiek

Binnen het project Rotterdams Publiek hebben we data uit verschillende bronnen samengevoegd om zo een beeld te geven van het culturele verleden van Rotterdam. Op de website [rotterdamspubliek.nl](https://rotterdamspubliek.nl/) is te zien in hoeverre we daar in geslaagd zijn.

Zelf hebben we, vaak om al beschikbare data te verbinden, ook data gemaakt. Deze data is hier, onder een CC0 licentie, te vinden.

## Quotes

Om bioscopen, theaters en andere uitgaansgelegenheden, waar soms geen of weinig afbeeldingen van zijn, verder te 'illustreren', hebben we quotes uit [Delpher](https://www.delpher.nl/) verzameld. Zo hebben we Wikidata items verbonden met Delpher artikelen, op de volgende manier:

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

## Gebeurtenissen

todo

## Koppelingen tussen afbeeldingen en Wikidata items

Uit de collecties van het Stadsarchief Rotterdam en, in mindere mate, het Nationaal Archief, zijn afbeeldingen gelinkt aan Wikidata identifiers van bioscopen, concertzalen, etc. Die links staan in de volgende twee bestanden:

- [sa-rp-links.ttl](data/sa-rp-links.ttl) bevat koppelingen tussen afbeeldingen van het Stadsarchief Rotterdam en locaties
- [na-rp-links.ttl](data/na-rp-links.ttl) bevat koppelingen tussen afbeeldingen van het Nationaal Archief en locaties

Uit praktische overwegingen is een beperkte hoeveelheid metadata van genoemde afbeeldingen, waaronder de afbeeldingsurl, opgenomen in de volgende bestanden:

- [sa-rp-imgs.ttl](data/sa-rp-imgs.ttl) bevat metadata van afbeeldingen van het Stadsarchief Rotterdam
- [na-rp-images.ttl](data/na-rp-images.ttl) bevat metadata van afbeeldingen van het Nationaal Archief

De volgende query toont het aantal afbeeldingen per locatie (en ook de zalen zonder afbeeldingen). Volg [deze link](https://api.druid.datalegend.net/s/s_eUCNgVS) om de queryresultaten in de Rotterdams Publiek sparql endpoint te bekijken.

```
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX dct: <http://purl.org/dc/terms/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX edm: <http://www.europeana.eu/schemas/edm/>
SELECT ?location ?locationlabel (COUNT(DISTINCT(?cho)) AS ?nrofimgs) WHERE {
  SERVICE <https://query.wikidata.org/sparql> {
  	VALUES ?type { 
      wd:Q57660343 	#podiumkunstgebouw
      wd:Q41253 	#bioscoop
      wd:Q24354 	#theatergebouw
      wd:Q24699794 	#museumgebouw
      wd:Q207694 	#kunstmuseum
      wd:Q856584 	#bibliotheekgebouw
      wd:Q57659484 	#tentoonstellingsgebouw
      wd:Q1060829 	#concertgebouw
      wd:Q18674739 	#evenementenlocatie
      wd:Q15206070 	#poppodium
      wd:Q30022 	#koffiehuis
      wd:Q1228895 	#dancing
  	}
  	?location wdt:P31 ?type .
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
ORDER BY DESC(?nrofimgs)
LIMIT 1000
```

## Filmvoorstellingen

Benieuwd naar wat er in zeg mei 1932 in welke Rotterdamse bioscoop draaide? Antwoord op die vraag vind je in [Cinema Context](http://www.cinemacontext.nl), dat duizenden filmvoorstellingen bevat. Maar voorstellingen van na 1950 zijn in die database nog niet opgenomen, terwijl wij juist ook de tijd wilden belichten die bezoekers zelf meegemaakt hadden.

Vandaar dat we op [hetvolk.org](https://hetvolk.org) enkele crowdsourceprojecten willen gaan draaien om filmladders uit de jaren '70, '80 en '90 in te voeren.


## Wikidata

Hier niet opgenomen is de data die we op Wikidata gemaakt hebben. Voor veel uitgaansgelegenheden hebben we daar items aangemaakt en / of aangevuld met relevante informatie (dateringen, verschillende namen, architecten, identifiers in andere datasets, zoals Cinema Context, etc.). Regelmatig hebben we daarbij items aangemaakt voor personen, verdwenen straten of andere zaken waar we die uitgaansgelegenheden graag mee wilden verbinden.
