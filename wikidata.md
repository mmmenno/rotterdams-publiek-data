## Wikidata

Voor veel uitgaansgelegenheden hebben we op Wikidata items aangemaakt en / of aangevuld met relevante informatie - dateringen, verschillende namen, architecten, identifiers in andere datasets, afbeeldingen, etc.. Regelmatig hebben we daarbij items aangemaakt voor personen, verdwenen straten of andere zaken waar we die uitgaansgelegenheden graag mee wilden verbinden.

Op de [Wikidata sparql endpoint](https://query.wikidata.org/) vraag je die uitgaansgelegenheden op met de volgende query:

```
SELECT ?item ?itemLabel ?straatLabel ?coords WHERE {
  
    VALUES ?type { 
      wd:Q57660343 #podiumkunstgebouw
      wd:Q41253 #bioscoop
      wd:Q24354 #theatergebouw
      wd:Q24699794 #museumgebouw
      wd:Q207694 #kunstmuseum
      wd:Q856584 #bibliotheekgebouw
      wd:Q57659484 #tentoonstellingsgebouw
      wd:Q1060829 #concertgebouw
      wd:Q18674739 #evenementenlocatie
      wd:Q15206070 #poppodium
      wd:Q30022 #koffiehuis
      wd:Q1228895 #discotheek
      wd:Q1684522 #jazzclub
    }
    ?item wdt:P131 wd:Q2680952 .
    ?item wdt:P31 ?type .
    ?item wdt:P625 ?coords .
    OPTIONAL{
      ?item wdt:P669 ?straat .
    }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "nl,en". }
}
GROUP BY ?item ?itemLabel ?straatLabel ?coords
ORDER BY ?itemLabel
LIMIT 1000
```

Met de volgende query haal je ook alle dateringen op, zowel van de gebouwen zelf als van de periode dat een gebouw een bepaalde functie had en de periode dat het een bepaalde naam droeg:

```
SELECT ?item ?itemLabel ?typeLabel ?bouwjaar ?sloopjaar ?starttype ?eindtype ?naamstring ?startnaam ?eindnaam ?straat ?straatLabel WHERE {
  
    VALUES ?type { 
      wd:Q57660343 #podiumkunstgebouw
      wd:Q41253 #bioscoop
      wd:Q24354 #theatergebouw
      wd:Q24699794 #museumgebouw
      wd:Q207694 #kunstmuseum
      wd:Q856584 #bibliotheekgebouw
      wd:Q57659484 #tentoonstellingsgebouw
      wd:Q1060829 #concertgebouw
      wd:Q18674739 #evenementenlocatie
      wd:Q15206070 #poppodium
      wd:Q30022 #koffiehuis
      wd:Q1228895 #discotheek
      wd:Q1684522 #jazzclub
    }
    ?item wdt:P131 wd:Q2680952 .
    ?item wdt:P31 ?type .
    ?item wdt:P625 ?coords .
    OPTIONAL{
      ?item wdt:P669 ?straat .
    }
  OPTIONAL{
      ?item wdt:P571 ?bouwjaar .
    }
  OPTIONAL{
      ?item wdt:P576 ?sloopjaar .
    }
  OPTIONAL{
      ?item p:P31 ?iseen .
      ?iseen pq:P580 ?starttype .
      ?iseen pq:P582 ?eindtype .
    }
  OPTIONAL{
      ?item p:P2561 ?naam .
      ?naam ps:P2561 ?naamstring .
      ?naam pq:P580 ?startnaam .
      ?naam pq:P582 ?eindnaam .
    }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "nl,en". }
}
ORDER BY ?typeLabel ?itemLabel
LIMIT 1000
```