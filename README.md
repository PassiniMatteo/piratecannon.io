# Piratecannon.io - Multiplayer Evolution Arena

Piratecannon.io è un videogioco multiplayer in tempo reale basato su browser, che combina dinamiche di Arena Shooter ed Evolution Game. Il progetto è stato sviluppato con un'architettura autoritativa per garantire l'integrità del gioco e una sincronizzazione fluida tra i client.

## Caratteristiche Tecniche

### Architettura Server-Side Autoritativa
Il cuore del gioco risiede in un server Node.js che gestisce la simulazione fisica a un tick rate di 20Hz. Tutte le collisioni, il calcolo dei danni e l'evoluzione dei giocatori sono elaborati esclusivamente sul server per prevenire tentativi di cheating e garantire una "Single Source of Truth".

### Netcode e Sincronizzazione
* **Client-Side Prediction:** Gli input del giocatore locale vengono applicati istantaneamente sul client per eliminare la percezione della latenza di rete.
* **Server Reconciliation:** Il client corregge la propria posizione basandosi sui dati validati dal server, riapplicando gli input in sospeso per una transizione fluida.
* **Interpolazione Entità:** I movimenti degli altri giocatori vengono interpolati per eliminare lo stuttering visivo causato dal campionamento dei pacchetti di rete.

### Meccaniche di Gioco e Progression
* **Evolution System:** Sistema di livellamento automatico basato sulla raccolta di risorse (Oro). Ogni livello aumenta dinamicamente la scala dello sprite, la potenza di fuoco e il numero di torri attive.
* **Combat Engine:** Mira manuale basata sulle coordinate del mouse con supporto al fuoco continuo.
* **Dynamic Physics:** Implementazione di meccaniche di inerzia e attrito dell'acqua, con l'aggiunta di un modificatore di danno (Sniper Bonus) applicato quando la velocità della nave è nulla.
* **Responsive Viewport:** Gestione dinamica dello zoom della telecamera in funzione della stazza della nave, garantendo un bilanciamento della visuale di gioco a ogni livello di evoluzione.

## Tech Stack

* **Frontend:** Phaser 3, TypeScript, Vite.
* **Backend:** Node.js, Express, Socket.io.
* **Data Management:** TypeScript Interfaces condivise tra Client e Server per la consistenza dei dati.
* **Ambiente di Sviluppo:** Visual Studio Code, Git per il versioning.

## Struttura del Progetto

* `/client`: Logica di rendering, gestione degli input e sistemi particellari.
* `/server`: Physics engine, gestione degli stati dei socket e logica autoritativa.
* `/shared`: Definizioni di tipo TypeScript e costanti di configurazione comuni.

## Installazione e Avvio

### Prerequisiti
* Node.js (versione 16.x o superiore)
* npm

### Setup Locale

1. **Clonare la repository:**
   ```bash
   git clone [https://github.com/PassiniMatteo/piratecannon.io.git](https://github.com/PassiniMatteo/piratecannon.io.git)
   cd pirate-td-io
2. **Configurazione Server:**
   ```bash
   cd server
   npm install
   npm run dev

3. **Configurazione Client:**
   Aprire un secondo terminale:
   ```bash
   cd client
   npm install
   npm run dev

##Il gioco sarà accessibile all'indirizzo http://localhost:5173.
##Progetto sviluppato a scopo dimostrativo per l'implementazione di sistemi multiplayer autoritativi.
