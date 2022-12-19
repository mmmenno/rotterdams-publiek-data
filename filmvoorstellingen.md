# Filmvoorstellingen jaren '80

Op [hetvolk.org](https://hetvolk.org/) hebben vrijwilligers in verschillende Rotterdams Publiek projecten Rotterdamse filmladders uit de jaren '80 ingevoerd, de ingevoerde data gecontroleerd en filmtitels verbonden met Wikidata- en imdb-identifiers. Het resultaat vind je in deze repository.

De voorstellingsdata wordt opgenomen in [Cinema Context](http://www.cinemacontext.nl), maar de (ruwe) data vind je nu al hier, in het bestand [data/filmvoorstellingen-jaren-80.csv](data/filmvoorstellingen-jaren-80.csv).

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons-Licentie" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a>

De voorstellingsgegevens vallen onder een <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">CC-BY licentie</a>. Als maker kunt u vermelden 'Vrijwilligers Rotterdams Publiek'.


## Totstandkoming dataset

De volgende stappen / deelprojecten hebben tot het uiteindelijke bestand geleid:

- verzamelen [filmladders](data/filmladders-jaren-80.csv) uit Delpher
- dubbele invoer op hetvolk.org
- samenvoegen van de dubbele invoer tot één bestand
- controle van het samengevoegde bestand op hetvolk.org
- extractie van unieke filmtitels uit de gecontroleerde set
- scriptmatig verbinden van unieke filmtitels met Wikidata en / of IMDB id
- controleren en aanvullen van Wikidata en / of IMDB id's op hetvolk.org
- opnemen van de gecontroleerde identifiers in de gecontroleerde voorstellingsdata
- redactionele aanvullingen op die voorstellingsdata (vooral het handmatig opzoeken - nu met toegang tot de filmladder waarin gegevens over regisseur, acteurs, etc. terug te vinden waren - van Wikidata en / of IMDB identifiers bij nog niet 'thuisgebrachte' films)
- opnemen van gegevens (jaar, land, titel, beschrijving) uit Wikidata bij films met een Wikidata identifier.


## Velden

- _ladderid_ ons id van filmladders, afgeleid uit filmladderuri
- _ladderuri_ URI van krantenpagina in Delpher met filmladder
- _showtype_ 



