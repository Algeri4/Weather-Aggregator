# *Weather Aggregator*

**Proposta di progetto — Progettazione, Algoritmi e Computabilità (a.a. 2026/27)**

| Componente del team | Matricola |
|---|---|
| Algeri Nicola | 1092461 |
| Bertoli Marco | 1092563 |

---

## 1. Contesto e problema

Quando dobbiamo pianificare un'attività all'aperto di qualsiasi tipo (un'uscita in bicicletta, un'escursione in montagna, un picnic, ...) consultiamo spesso diversi servizi meteorologici, in quanto le previsioni che vediamo online possono differire in modo significativo l'una dall'altra.

Il confronto manuale è, però, laborioso e richiede molto tempo. Inoltre non fornisce nessuna indicazione quantitativa su quanto le previsioni siano concordi, né su quale fonte sia storicamente la più affidabile.

## 2. Obiettivo del progetto

L'obiettivo del progetto è quello di fornire un sistema software per l'acquisizione, l'aggregazione, il confronto e la valutazione dell'affidabilità di previsioni meteo provenienti da modelli e servizi diversi tra loro.

Non vogliamo produrre nuove previsioni meteorologiche, ma ci focalizzeremo sull'integrazione di dati eterogenei che arrivano da fonti esterne e sulla loro elaborazione mediante algoritmi di aggregazione, analisi della dispersione e individuazione delle anomalie.

Dati un luogo e un intervallo di tempo scelti dall'utente, il sistema risponderà alle seguenti domande:

- qual è la previsione aggregata per una determinata variabile meteorologica?
- quanto concordano tra loro le diverse fonti?
- quali fonti forniscono previsioni anomale rispetto alle altre?
- quali fonti si sono dimostrate storicamente più accurate per quella località e per quella variabile?

## 3. Funzionalità previste

- Ricerca di una località e conversione in coordinate geografiche (geocoding).
- Acquisizione delle previsioni da più modelli e servizi meteorologici tramite API pubbliche gratuite.
- Normalizzazione dei dati: unità di misura, fusi orari, risoluzione temporale, dati mancanti.
- Allineamento temporale delle serie provenienti da fonti con passi temporali diversi.
- Calcolo di statistiche aggregate: media, mediana, minimo, massimo, deviazione standard.
- Individuazione e segnalazione delle previsioni anomale.
- Calcolo di un indice di concordanza tra le fonti.
- Aggregazione pesata delle previsioni.
- Visualizzazione dei risultati: previsione aggregata, confronto tra fonti, evoluzione temporale.
- *(Estensione)* Valutazione dell'accuratezza storica delle fonti, confrontando previsioni passate e dati osservati, e calcolo automatico dei pesi.

## 4. Nucleo algoritmico

Il sistema si baserà su algoritmi di elaborazione dei dati: allineamento su una griglia temporale comune di serie eterogenee, aggregazione statistica, individuazione delle previsioni anomale, calcolo di un indice di concordanza tra le fonti e aggregazione pesata. Definiremo e analizzeremo gli algoritmi nel corso dello sviluppo.

## 5. Architettura concettuale

```
┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐
│ Acquisizione dati│ → │  Normalizzazione │ → │ Motore di analisi│ → │    Risultati     │
│ API multiple     │   │ unità · timestamp│   │ statistiche ·    │   │ previsione aggr. │
│ geocoding        │   │ dati mancanti    │   │ anomalie · pesi  │   │ concordanza ·    │
│ caching          │   │ allineamento     │   │ concordanza      │   │ grafici          │
└──────────────────┘   └──────────────────┘   └──────────────────┘   └──────────────────┘
```

Integreremo ogni fonte con un adattatore dedicato, così da poter aggiungere nuove fonti senza modificare il motore di analisi.

Definiremo nel dettaglio l'architettura nell'iterazione 0 del processo agile AMDD tramite diagrammi UML e Architecture Decision Records (ADR).

## Documentazione e Pianificazione

**[Roadmap dei requisiti per le iterazioni e ADM]https://docs.google.com/spreadsheets/d/10ADHtKi5Zg1J3i9NpSl39cSRpWYiTWRaKsadT5ev3OQ/edit?usp=sharing

## 6. Aspetti da definire

I seguenti aspetti saranno definiti dopo l'approvazione della proposta:

- stack tecnologico e tool chain;
- tipologia di client (web, mobile o desktop);
- insieme iniziale delle variabili meteorologiche;
- ripartizione dei ruoli all'interno del team.
