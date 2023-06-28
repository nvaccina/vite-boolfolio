# Vite Boolfolio

Front-office di laravel-api.

**Milestone 3**<br>
nome repo 2: vite-boolfolio<br>
Iniziamo ad occuparci della parte front-office della nostra applicazione: creiamo un nuovo progetto Vue 3 con Vite e installiamo axios.<br>
Colleghiamo questo progetto ad una repo separata.<br>
**Milestone 4**<br>
Nel componente principale della nostra Vue App facciamo una chiamata API all’endpoint costruito nel progetto Laravel (milestone 1) e recuperiamo tutti i progetti dal nostro back-end.
Stampiamo in console i risultati e verifichiamo di ricevere i dati correttamente.<br>
**Milestone 5**<br>
Creiamo un nuovo componente ProjectCard, che corrisponde ad una card per visualizzare un progetto. Utilizziamo questo componente per visualizzare tutti i progetti ricevuti tramite API.<br>
<br>
- Aggiungere il router a Vue e inserite  un menu di navigazione fra le pagine.
- Solo una delle pagine farà la chiamata axios per stampare il portfolio.
- Aggiungere un elenco di  bottoni per i tipi  e le tecnologie, Questi bottoni verranno stampati a seguito di chiamate axios dedicate.
- Al click di un bottone per il tipo o  tecnologie, nell’elenco dei progetti appariranno solo quelli di quel tipo o di quella tecnologia
- Aggiungere alla navigazione con Vue anche la rotta che accetta lo slug come parametro dinamico e la relativa API del dettaglio dell’elemento cliccato
- Creare un un form di ricerca per titolo;