# Gebeurtenissen

De gebeurtenissen zijn te vinden in [deze sparql endpoint](https://druid.datalegend.net/menno/events/sparql/events). Vraag ze daar op met de volgende query:

```
PREFIX dct: <http://purl.org/dc/terms/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX edm: <http://www.europeana.eu/schemas/edm/>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX sem: <http://semanticweb.cs.vu.nl/2009/11/sem/>
PREFIX dbo: <http://dbpedia.org/ontology/>
SELECT DISTINCT ?item ?label ?place ?placelabel ?eventtype ?typelabel ?begin ?end (COUNT(?cho) AS ?images) WHERE {
?item a sem:Event ;
  sem:eventType ?eventtype ;
  sem:hasPlace ?place ;
  rdfs:label ?label ;
  sem:hasEarliestBeginTimeStamp ?begin;
  sem:hasLatestEndTimeStamp ?end .
?place wdt:P131 wd:Q2680952 ;
  rdfs:label ?placelabel .
?eventtype rdfs:label ?typelabel .
?cho dc:subject ?item .
?cho foaf:depiction ?imgurl .
MINUS { ?cho dc:type <http://vocab.getty.edu/aat/300263837> }
} 
GROUP BY ?item ?label ?place ?placelabel ?eventtype ?typelabel ?begin ?end
ORDER BY ?begin ?item 
LIMIT 1000
```

De gebeurtenissen zijn verbonden met plaatsen (theaters bijvoorbeeld), maar ook met personen en afbeeldingen in erfgoedcollecties. Hieronder als voorbeeld de query die de gebeurtenis 'Optreden Edith Piaf in het Luxor Theater' ophaalt:

```
PREFIX dct: <http://purl.org/dc/terms/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX edm: <http://www.europeana.eu/schemas/edm/>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX sem: <http://semanticweb.cs.vu.nl/2009/11/sem/>
PREFIX dbo: <http://dbpedia.org/ontology/>
SELECT DISTINCT ?item ?label ?place ?placelabel ?typelabel ?begin ?end ?cho ?imgurl ?title ?creator ?actor ?actorwdid ?actorlabel ?actorwiki ?actordescription WHERE {
VALUES ?item {<https://watwaarwanneer.info/event/3598>}
?item a sem:Event ;
	sem:eventType ?eventtype ;
	sem:hasPlace ?place ;
	rdfs:label ?label ;
	sem:hasEarliestBeginTimeStamp ?begin;
	sem:hasLatestEndTimeStamp ?end .
OPTIONAL{
	?item sem:hasActor ?actor .
    ?actor rdf:value ?actorwdid .
    ?actor rdfs:label ?actorlabel .
    OPTIONAL{
     	?actorwdid dc:description ?actordescription .
    }
    OPTIONAL{
     	?actorwdid foaf:isPrimaryTopicOf ?actorwiki .
    }
}
?place wdt:P131 wd:Q2680952 ;
	rdfs:label ?placelabel .
?eventtype rdfs:label ?typelabel .
?cho dc:subject ?item .
?cho foaf:depiction ?imgurl .
  OPTIONAL{
    ?cho dc:title ?title
  }
  OPTIONAL{
    ?cho dc:creator ?creator
  }
} 
ORDER BY ?begin 
LIMIT 100
```