# Filmvoorstellingen jaren '80

Op [hetvolk.org](https://hetvolk.org/) hebben vrijwilligers in verschillende Rotterdams Publiek projecten Rotterdamse filmladders uit de jaren '80 ingevoerd, de ingevoerde data gecontroleerd en filmtitels verbonden met Wikidata- en imdb-identifiers. Het resultaat vind je in deze repository.

De voorstellingsdata wordt opgenomen in [Cinema Context](http://www.cinemacontext.nl), maar de (ruwe) data vind je nu al hier, in het bestand [data/filmvoorstellingen-jaren-80.csv](data/filmvoorstellingen-jaren-80.csv).

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons-Licentie" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a>

De voorstellingsgegevens vallen onder een <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">CC-BY licentie</a>. Als maker kan je vermelden 'Vrijwilligers Rotterdams Publiek'. We vinden het leuk om te horen wat je ermee wilt gaan doen of gedaan hebt.


## Een paar cijfers

- 23.827 'ladderonderdelen'
- 320.524 voorstellingen (gemiddeld zo'n 88 voorstellingen per dag gedurende 10 jaar)
- 3.630 films met Wikidata id
- 4.251 films met IMDB id
- 658 titels (dit kunnen ook festivals o.i.d. zijn) zonder Wikidata of IMDB id
- 22 bioscopen


## Totstandkoming dataset

De volgende stappen / deelprojecten hebben tot het uiteindelijke bestand geleid:

- verzamelen [filmladders](data/filmladders-jaren-80.csv) uit Delpher
- dubbele invoer op hetvolk.org
- samenvoegen van de dubbele invoer tot één bestand
- controle van het samengevoegde bestand op hetvolk.org
- extractie van unieke filmtitels uit de gecontroleerde set
- scriptmatig verbinden van unieke filmtitels met Wikidata en / of IMDB id
- controleren en aanvullen van Wikidata en / of IMDB id's op hetvolk.org
- opnemen van de gecontroleerde filmidentifiers in de gecontroleerde voorstellingsdata
- redactionele aanvullingen op die voorstellingsdata (vooral het handmatig opzoeken - nu met toegang tot de filmladder waarin gegevens over regisseur, acteurs, etc. terug te vinden waren - van Wikidata en / of IMDB identifiers bij nog niet 'thuisgebrachte' films)
- opnemen van gegevens (jaar, land, titel, beschrijving) uit Wikidata bij films met een Wikidata identifier.

Redactie: Thunnis van Oort en Menno den Engelse, programmeerwerk: Menno den Engelse 


## Velden

- _ladderid_ - ons id van filmladders, afgeleid uit filmladderuri
- _ladderuri_ - URI van krantenpagina in Delpher met filmladder
- _showtype_ - leeg indien reguliere voorstelling, verder keuze uit doorlopende voorstelling, festival, kindermatinee, nachtvoorstelling, retrospectief en anders
- _showtype\_other_ - door gebruiker ingevoerd showtype waar voornoemd veld 'anders' was
- _theater_ - naam van de bioscoop
- _cctheaterid_ - Cinema Context id van bioscoop
- _zaal_ - het zaalnummer zoals in de filmladder vermeld
- _aantal_ - het aantal keer dat een film die week vertoond werd (bij doorlopende voorstellingen: het aantal uur) binnen dit showtype (de film kan bijvoorbeeld zowel als reguliere voorstelling als als nachtvoorstelling in de ladder staan)
- _title_ - de van de ladder overgenomen titel
- _title\_wd_ - de titel volgens Wikidata
- _description\_wd_ - de beschrijving van Wikidata
- _wdid_ - het Wikidata id
- _imdb_ - het IMDB id
- _landen_ - de 'landen van oorsprong' volgens Wikidata
- _vroegste\_jaar_ - het jaar van de vroegste 'datum van uitgave' van Wikidata
- _programma_ - bij een programma van meerdere films krijgt elke film een eigen rij en is de unieke combinatie bioscoop, zaal en dit veld bedoeld om te herleiden dat die meerdere films binnen hetzelfde programma vielen (incidenteel toegepast) 
- _wat is dit_ - binnen het project 'controleren en aanvullen van Wikidata en / of IMDB id's op hetvolk.org' konden deelnemers aangeven of de titel een film of iets anders (een festival o.i.d.) betrof


