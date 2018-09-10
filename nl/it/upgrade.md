---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-26"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Accesso a ulteriori funzioni di Gestione delle API
{: #upgrade}

La funzione di gestione delle API che viene fornito con l'API {{site.data.keyword.Bluemix}} ti permette il controllo limitato delle frequenze di chiamata, di OAuth e di visualizzare le analisi. Puoi avere un maggiore controllo della gestione sulle API eseguendo l'upgrade al servizio {{site.data.keyword.apiconnect_full}}. Il servizio {{site.data.keyword.apiconnect_short}} fornisce ulteriori scelte di politiche di sicurezza e un maggiore controllo sui limiti di frequenza. Oltre a ciò, potrai configurare un portale degli sviluppatori pienamente personalizzabile in modo da poter generare un'interazione per le tue API e partecipare alla community degli sviluppatori. Altri vantaggi includono:
* Gestione del ciclo di vita
* API composite
* Integrazione dei servizi web
* Mediazione del protocollo
* Generazione di API dallo schema
* Sviluppo di microservizi

La migrazione al servizio {{site.data.keyword.apiconnect_short}} è facile e non devi ricreare nessuna delle API che stai gestendo con la gestione delle API. Puoi migrare le tue API automaticamente o manualmente.

## Migra automaticamente le tue API a {{site.data.keyword.apiconnect_short}}
{: #auto_migrate_api}

Se decidi di eseguire l'upgrade a {{site.data.keyword.apiconnect_short}}, dovrai migrare le tue API da Gestione delle API al servizio {{site.data.keyword.apiconnect_short}} selezionando e completando la seguente procedura per il tipo di API che stai migrando.

### API Cloud Functions

1. Seleziona **Functions** nel tuo menu {{site.data.keyword.Bluemix_notm}} per visualizzare il tuo Cloud Functions.

2. Nell'elenco delle funzioni, seleziona **API** nella navigazione.

3. Seleziona il nome dell'API Function che vuoi migrare.

4. Seleziona **Definizione** nella navigazione.

5. Seleziona **File di definizione API** > **Apri in API Connect** > **Continua** nella sezione *File di definizione API*. Se già disponi di un servizio {{site.data.keyword.apiconnect_short}} esistente, viene migrata automaticamente l'API al servizio esistente. Se non disponi ancora di un servizio {{site.data.keyword.apiconnect_short}} configurato, viene automaticamente aggiunto con un piano Lite gratuito e viene migrata l'API. Se la tua istanza non viene fornita, completa la procedura in [Migrazione manuale delle API a {{site.data.keyword.apiconnect_short}}](#man_migrate_api) per migrarla manualmente al nuovo servizio. 

6. Prima di chiudere la schermata dell'API originale, disabilita lo slider per **Esponi API gestita**. Questo evita che qualcuno utilizzi l'endpoint della vecchia versione.

### API Cloud Foundry

1. Apri la tua origine API Cloud Foundry esistente nel dashboard {{site.data.keyword.Bluemix_notm}}. 

2. Seleziona **Gestione API** nel menu di navigazione.

3. Seleziona **Definizione** nella navigazione.

4. Seleziona **File di definizione API** > **Apri in API Connect** > **Continua**. Se già disponi di un servizio {{site.data.keyword.apiconnect_short}} esistente, viene migrata automaticamente l'API al servizio esistente. Se non disponi ancora di un servizio {{site.data.keyword.apiconnect_short}} configurato, viene automaticamente aggiunto con un piano Lite gratuito e viene migrata l'API. Se la tua istanza non viene fornita, completa la procedura in [Migrazione manuale delle API a {{site.data.keyword.apiconnect_short}}](#man_migrate_api) per migrarla manualmente al nuovo servizio.
   
5. Dopo aver migrato il contenuto all'istanza {{site.data.keyword.apiconnect_short}}, seleziona il link fornito per accedere alla versione migrata.
    **Importante:** per evitare problemi con l'esecuzione di più istanze dell'API, assicurati di disabilitare lo slider *Gestisci l'API* nella versione originale dell'API.

6. Seleziona la scheda **API** nella navigazione.

7. Seleziona **Bozze** per visualizzare la tua nuova API.

## Migrazione manuale della API a {{site.data.keyword.apiconnect_short}}
{: #man_migrate_api}

Se il processo per migrare la tua API al servizio {{site.data.keyword.apiconnect_short}} non termina correttamente, completa la seguente procedura per migrarla manualmente:

1. Apri la tua API.
	1. Accedi a {{site.data.keyword.Bluemix_notm}}.
	2. Per un'applicazione Cloud Foundry: 
		1. Seleziona **Dashboard** nel menu.
		2. Seleziona il nome dell'applicazione Cloud Foundry che vuoi migrare.
		3. Seleziona **Gestione API** nel riquadro di navigazione.
	3. Per un'azione Cloud Functions: 
		1. Seleziona **Functions** nel menu.
		2. Seleziona **API** nella navigazione.
		3. Seleziona il nome dell'API che vuoi migrare.
2. Scarica il documento Swagger per la API da Gestione delle API.
    1. Seleziona **Definizione** nella navigazione.
	2. Seleziona **File di definizione API**.
    3. Seleziona **Esporta YAML** o **Esporta JSON**, a seconda del tuo tipo di file, per scaricare la definizione dell'API. Il file viene scaricato nella tua cartella di scaricamento.
3. Crea e prepara l'istanza di {{site.data.keyword.apiconnect_short}}. 
	1. Passa a **API** nella navigazione per filtrare i servizi.
	2. Seleziona il servizio API Connect. 
    3. Crea un'istanza del servizio {{site.data.keyword.apiconnect_short}} dal catalogo {{site.data.keyword.Bluemix_notm}}.
	4. Seleziona il tuo piano. Il piano Lite è l'opzione gratuita.
	5. Seleziona **Crea** per creare l'istanza.
4. Importa il documento Swagger nella tua istanza di {{site.data.keyword.apiconnect_short}} completando la seguente procedura:
	1. Dal dashboard del servizio {{site.data.keyword.apiconnect_short}}, seleziona **Passa a... (>>)** > **Bozze** nel menu.
	2. Seleziona la scheda API.
	3. Seleziona **+Aggiungi** > **Importa API da un file o URL**.
	4. Trova e seleziona il file Swagger che hai scaricato da Gestione delle API. Seleziona **Apri**.
	5. Seleziona **Importa** per impostare la tua API nel servizio {{site.data.keyword.apiconnect_short}}.
5. Per evitare problemi conseguenti all'esecuzione di più istanze dell'API, assicurati di disabilitare lo slider *Gestisci l'API* nella versione originale dell'API.

La tua API è disponibile nell'istanza del servizio {{site.data.keyword.apiconnect_short}}. 

## Pubblica l'API

Puoi continuare pubblicando l'API completando la seguente procedura:

1. Crea un catalogo.
	1. Seleziona **+Aggiungi** per creare un catalogo.
	2. Immetti un nome di visualizzazione e il nome per il tuo catalogo e seleziona **Aggiungi**.
	3. Seleziona il catalogo che hai creato.
2. Specifica le impostazioni per la tua API.
    1. Seleziona **Crea prodotto**.
	2. Specifica un nome per il prodotto.
	2. Seleziona il prodotto che hai creato per visualizzarne le impostazioni.
	3. Imposta il limite della frequenza per la API.
	4. Imposta il livello per la API.
3. Aggiungi l'endpoint per la API, se necessario.
    1. Seleziona la API.
	2. Seleziona la scheda Assemblaggio.
	3. Aggiungi l'endpoint, se non è già specificato.
	
 Dopo che hai migrato le tue API, puoi accedere a tutte le funzioni di Gestione delle API aprendo il tile di servizio {{site.data.keyword.apiconnect_short}} e tramite il dashboard {{site.data.keyword.Bluemix_notm}}. 

