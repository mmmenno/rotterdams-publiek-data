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

todo

## Filmvoorstellingen

Benieuwd naar wat er in zeg mei 1932 in welke Rotterdamse bioscoop draaide? Antwoord op die vraag vind je in [Cinema Context](http://www.cinemacontext.nl), dat duizenden filmvoorstellingen bevat. Maar voorstellingen van na 1950 zijn in die database nog niet opgenomen, terwijl wij juist ook de tijd wilden belichten die bezoekers zelf meegemaakt hadden.

Vandaar dat we op [hetvolk.org](https://hetvolk.org) enkele crowdsourceprojecten willen gaan draaien om filmladders uit de jaren '70, '80 en '90 in te voeren.


## Wikidata

Hier niet opgenomen is de data die we op Wikidata gemaakt hebben. Voor veel uitgaansgelegenheden hebben we daar items aangemaakt en / of aangevuld met relevante informatie (dateringen, verschillende namen, architecten, identifiers in andere datasets, zoals Cinema Context, etc.). Regelmatig hebben we daarbij items aangemaakt voor personen, verdwenen straten of andere zaken waar we die uitgaansgelegenheden graag mee wilden verbinden.
