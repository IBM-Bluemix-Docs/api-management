---

copyright:
  years: 2017,2018
lastupdated: "2018-08-23"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Gestire le API
{: #manage_apis}

Dopo che hai integrato la tua API in modo che sia gestita e monitorata dal sistema di gestione delle API, puoi visualizzare le modificare le sue impostazioni. Se non hai integrato la tua API, devi integrarne una completando la procedura in [Creazione di API dalle azioni {{site.data.keyword.openwhisk_short}}](manage_openwhisk_apis.html) o [Abilitazione degli endpoint gestiti dall'API](manage_cf_apis.html). 

Per gestire le impostazioni per la tua API, completa la seguente procedura:

Se hai creato una nuova API, ed è già aperta nell'interfaccia, puoi saltare i primi tre passi.

1. Seleziona l'API che vuoi gestire dal dashboard {{site.data.keyword.Bluemix}} o selezionando un'azione nel dashboard del servizio {{site.data.keyword.openwhisk_short}}, se le informazioni per la tua API non sono già visualizzate.
2. Fai clic su **Gestione API** nella barra di navigazione o seleziona la scheda **API** se si tratta di un'azione {{site.data.keyword.openwhisk_short}}.
3. Seleziona la API che vuoi gestire, se necessario. Quando viene stabilita una connessione, puoi visualizzare e aggiornare le seguenti selezioni:
    * Riepilogo
    * Definizione
    * Condivisione
    * Explorer API
4. Seleziona il dispositivo di scorrimento Esponi API gestita per eseguirne l'attivazione ed esporre la tua API. Nota: alcune delle impostazioni non possono essere impostate quando la API non è esposta.  

## Riepilogo delle impostazioni per le API
{: #overview_api}

La scheda Riepilogo è selezionata per impostazione predefinita quando selezioni una API ed è divisa in due sezioni:
* Proprietà - nella sezione Proprietà, puoi visualizzare le seguenti informazioni:
    * Le informazioni di base sulla tua API
	* Le politiche di sicurezza
	* Le informazioni sul limite della frequenza
    * i dettagli della condivisione
* Sezione Analisi e registrazione - nella sezione Analisi e registrazione, puoi visualizzare le seguenti statistiche:
	* Il numero di risposte e il tempo di risposta medio durante l'ultimo intervallo di tempo specificato
    * Il numero di chiamate API al minuto in formato grafico
    * Le ultime 100 risposte nella tabella Log delle risposte
	
Il grafico *Risposte* mostra una rapida rappresentazione di quante risposte ha ricevuto la tua API e la suddivisione dello stato delle risposte. Questo può aiutarti a determinare se stai ricevendo una prevalenza di risposte di errore. Una prevalenza di risposte di errore può indicare che hai più traffico di quanto ne hai consentito nelle tue impostazioni della frequenza. Puoi visualizzare una suddivisione numerica delle risposte in base al codice della risposta passando il puntatore del mouse sull'icona delle informazioni. I seguenti codici della risposta sono comuni:
* 200  OK
* 201  Creato
* 302  Trovato
* 304  Non modificato
* 400  Richiesta non valida
* 401  Non autorizzato
* 403  Non consentito
* 500  Errore interno del server
* 503  Servizio non disponibile

La tabella Log delle risposte contiene i singoli dettagli delle ultime 100 risposte. Puoi ordinare le informazioni in base alle voci in una colonna selezionando l'intestazione della colonna. Puoi cercare specifiche voci nella tabella Log delle risposte utilizzando la barra *Cerca risposte*. Ulteriori informazioni sono disponibili per un evento selezionandolo oppure selezionando **Visualizza dettagli** nell'elenco del menu di opzioni (tre puntini verticali) che si trova accanto a una voce.


## Modifica delle impostazioni di una API
{: #settings_api}

Nella scheda **Definizione**, puoi aggiornare le informazioni di base sulla tua API. Queste informazioni includono la documentazione, il nome e l'URL di base. Utilizza la sezione Sicurezza e limitazione della frequenza per specificare un limite di chiamate e di intervallo per garantire che venga eseguita solo una specifica quantità di chiamate al secondo, minuto od ora. Puoi anche richiedere l'autenticazione per creare delle chiamate API per evitare un utilizzo indesiderato dei tuoi dati oppure per raccogliere statistiche sulla API.

Per modificare le impostazioni per una API, completa la seguente procedura:

1. Nel dashboard Gestione delle API, fai clic sulla scheda **Definizione**.
2. Puoi denominare o aggiornare il nome della tua API e importare una definizione di API nella sezione Informazioni API.
3. Nella sezione Sicurezza e limitazione della frequenza, puoi aggiornare le seguenti politiche:
    * Richiedi chiave API - specifica se la chiamata API può essere elaborata solo quando viene fornita la chiave API corretta. L'impostazione predefinita non richiede una chiave aggiuntiva.
    * Metodo di sicurezza - quando l'opzione di chiave API è selezionata, specifica se l'elaborazione della API richiede solo la chiave API oppure richiede sia la chiave API che il segreto API.
    * Ubicazione di chiave e segreto API - a seconda della tua impostazione per il metodo, specifica in che modo le informazioni di sicurezza della tua API sono incluse nella chiamata. I nomi di richiamo specificano in che modo vengono identificate le informazioni di sicurezza. Per ulteriori informazioni sull'utilizzo delle chiavi e dei segreti, consulta [Gestisci chiavi e segreti](keys_secrets.html).
    * Limita frequenza delle chiamate API - imposta il numero di chiamate API consentito durante uno specifico intervallo di tempo, con l'opzione di eseguirne l'impostazione per ciascuna chiave. Nota che il metodo di limitazione della frequenza è di tipo burst. La frequenza media delle chiamate API viene calcolata sull'intervallo di tempo totale da te specificato nella frequenza. Se la frequenza delle chiamate API durante un intervallo supera la frequenza media delle chiamate API, è possibile che ci sia un periodo di chiamate rifiutate che può raggiungere il limite di tempo da te specificato nella frequenza.   
    * Provider OAuth - garantisce che gli utenti con i parametri di sicurezza corretti possano accedere alle tue API implementando OAuth tramite le credenziali di accesso social di provider come Google, Facebook, ID applicazione IBM e GitHub.
	    **Nota:** devi specificare un'istanza del servizio ID applicazione esistente configurata in {{site.data.keyword.Bluemix_notm}} per fornire i dati di identificazione quando utilizzi l'**ID applicazione** come tuo provider OAuth. Se non disponi di un servizio ID applicazione esistente, puoi selezionare **Crea** nella sezione OAuth per crearne uno in una nuova finestra e tornare indietro per specificarlo per la gestione API. Puoi anche selezionare **Modifica** per modificare un'istanza del servizio selezionata.
4. Abilita CORS - CORS (Cross-origin requests) abilita delle richieste limitate da un dominio differente.
5. Fai clic su **Salva**.

## Condivisione di API
{: #share_api}

Puoi condividere le API con altri utenti all'interno o all'esterno della tua organizzazione {{site.data.keyword.Bluemix_notm}}. 

Quando condividi le tue API con altri utenti, all'interno o all'esterno della tua organizzazione {{site.data.keyword.Bluemix_notm}}, puoi creare le chiavi e i segreti per le tue API. Ogni API gestita supporta 5 chiavi che possono essere create e a cui è possibile assegnare detta API. Inviando una chiave univoca a un singolo utente o a un'azienda, è possibile tenere traccia di alcune statistiche sulla modalità di utilizzo di tale API. Ad esempio, puoi tenere traccia del numero di chiamate alla tua API da tale persona o azienda. Puoi anche disabilitare una chiave o limitare le chiamate da una chiave. Ciò può essere utile durante l'esecuzione di test, il bilanciamento del carico di lavoro, la monetizzazione o per occuparsi di alcune situazioni di sicurezza.

Una *chiave* è una stringa di caratteri univoca associata alla tua API. Puoi assegnare più di una chiave a un'API, questo ti consente di tenere traccia dell'utilizzo dell'API per ogni cliente. Ad esempio, fornisci una chiave a un cliente e un'altra chiave a un altro cliente. Ogni volta che i clienti richiamano l'API, includono le proprie chiavi assegnate. Tracciando questa chiave, puoi sapere quale cliente ha richiamato l'API.

Esistono due tipi di chiavi:

* Le chiavi per condividere l'API con i clienti che hanno accesso alla tua organizzazione {{site.data.keyword.Bluemix_notm}}. 
* Le chiavi per condividere l'API con i clienti che non hanno accesso alla tua organizzazione {{site.data.keyword.Bluemix_notm}}. 

I differenti tipi di chiavi sono creati, conservati ed eliminati nello stesso modo. L'unica differenza è chi può utilizzare le chiavi.

Dopo aver creato una o più chiavi per la tua API, puoi limitare la frequenza di chiamate alle tue API per chiave. Abilitando lo slider **Limita frequenza di chiamate API per ogni singola chiave** nella scheda *Definizione*, il numero di chiamate per ogni chiave che hai creato viene limitato al limite di frequenza che imposti.   

Un *segreto* è simile a una chiave, poiché viene utilizzato per mantenere l'accesso all'API stessa. Un segreto è personalizzabile e può essere modificato senza modificare la chiave. Non può esserci un segreto se non c'è una chiave. Ad esempio, solo qualcuno con il segreto corretto può caricare una nuova versione dell'API. Puoi richiedere un'API e un segreto per le tue chiamate API oppure utilizzare solo una chiave. I segreti possono essere utili se hai bisogno di modificare il segreto ma non vuoi modificare la chiave. 

1. Nel dashboard Gestione delle API, fai clic sulla scheda **Condivisione**.
2. Nell'area "Condivisione nell'organizzazione {{site.data.keyword.Bluemix_notm}}" seleziona **Esponi API gestita** se vuoi che la tua API sia disponibile agli altri utenti con accesso alla tua organizzazione {{site.data.keyword.Bluemix_notm}}. Questa selezione è necessaria per generare una chiave.
3. Fai clic su **Crea chiave API** per creare una chiave univoca per la tua API. Viene visualizzata la finestra di dialogo Crea chiave API. La chiave API viene generata automaticamente.
4. Utilizza la chiave API per determinare quale utente sta accedendo alla API inviando all'utente una chiave univoca. Il gateway può determinare quale chiave (e cliente) sta generando la chiamata.
5. Fai clic sull'icona **Menu** (tre puntini verticali) accanto alla chiave per modificare o eliminare la chiave API.

Nella sezione Condivisione esternamente all'organizzazione {{site.data.keyword.Bluemix_notm}}, puoi condividere la tua API con utenti che non hanno un account {{site.data.keyword.Bluemix_notm}}. Questo metodo di condivisione fornisce un collegamento diretto per visualizzare le informazioni sulla API in Explorer API. La API contiene un pulsante per l'esecuzione nella vista Explorer API. Per richiedere un collegamento per la tua API, completa la seguente procedura:

1. Nella sezione "Condivisione esternamente all'organizzazione {{site.data.keyword.Bluemix_notm}}", fai clic su **Crea chiave API**. Viene visualizzata la finestra di dialogo Crea chiave API.
     Nota che l'utente ha un segreto che non puoi controllare.
2. Fornisci un nome univoco per la chiave API.
3. Seleziona **Crea chiave**. 
4. Invia il collegamento del portale API al cliente senza un account {{site.data.keyword.Bluemix_notm}}. La chiave e il segreto (se utilizzato) dell'API vengono inclusi nel collegamento in modo che puoi ancora determinare quale chiave ha generato il collegamento.
  
Il collegamento della documentazione API apre la API nella scheda **Explorer API**.

Per ulteriori informazioni sull'utilizzo delle chiavi e dei segreti, consulta [Gestisci chiavi e segreti](keys_secrets.html).

## Visualizzazione ed esecuzione di test con Explorer API
{: #explore_api}

Seleziona la scheda Explorer API per visualizzare l'html generato dal tuo documento Swagger. 

Explorer API mostra tutte le azioni e la documentazione API che si applicano alla API. Puoi visualizzare le operazioni e le azioni, le loro descrizioni e testare la API dalla IU. Puoi anche scaricare il documento Swagger per riutilizzarne il contenuto.

Per testare la API, completa la seguente procedura:
1. *Esempi* è selezionato per impostazione predefinita. Mostra un esempio del codice per la API selezionata.
2. Modifica il formato dell'esempio, se necessario, selezionando una lingua dal menu accanto alla lingua specificata. 
3. Seleziona **Provalo**.
4. Seleziona **Richiama operazione**. 

Viene visualizzata la risposta alla richiesta. 

## Domini personalizzati
{: #custom_domains}

In alcune istanze, potresti desiderare un dominio personalizzato o "personale" invece del dominio predefinito del gateway dell'API. La funzionalità di gestione delle API supporta le API di fronting con un nome di dominio di tua scelta.

Completa la seguente procedura per configurare inizialmente il dominio personalizzato. Se hai precedentemente completato la procedura di configurazione del dominio, consulta [Utilizzo di un dominio personalizzato con le tue API](manage_apis.html#custom_domains_bind).

I domini personalizzati non sono isolati in una singola API, ma sono applicabili a un gruppo di API definito da:
- Servizio {{site.data.keyword.Bluemix_notm}} di origine (ad esempio, {{site.data.keyword.openwhisk_short}})
- Spazio Cloud Foundry

Ad esempio, un dominio personalizzato verrà applicato a tutte le API {{site.data.keyword.openwhisk_short}} create nello spazio Cloud Foundry "dev".

### Configurazione

Per iniziare, crea una nuova API in un servizio {{site.data.keyword.Bluemix_notm}} che supporta la funzione Gestione delle API integrata oppure crea un proxy API utilizzando la console delle API {{site.data.keyword.Bluemix_notm}}.

#### Prepara i certificati

Per registrare un dominio personalizzato, è necessario fornire certificati TLS validi durante la configurazione. Utilizza il servizio [Gestore certificato](../services/certificate-manager) per caricare un certificato e una chiave privata.

*Nota: le chiamate API sono disponibili solo utilizzando TLS (porta 443). L'HTTP semplice non è supportato.*

### Utilizzo di un dominio personalizzato con le tue API
{: #custom_domains_bind}

Dopo aver completato la configurazione iniziale, associa una o più API al dominio registrato dalla sezione **Domini personalizzati** della console delle API {{site.data.keyword.Bluemix_notm}} completando la seguente procedura:

1. Nell'elenco di destinazioni disponibili, individua il servizio o il dominio predefinito a cui deve essere collegato il dominio personalizzato.
2. In una finestra o scheda separata del browser, vai alla pagina delle impostazioni del tuo provider DNS e crea un record CNAME per il dominio desiderato. Utilizza il valore della colonna **Dominio predefinito / Alias** nella pagina di gestione del dominio personalizzato {{site.data.keyword.Bluemix_notm}} come destinazione CNAME, quindi salva le tue impostazioni DNS.
  
    *Nota: le modifiche DNS possono richiedere fino a 48 ore per propagarsi, sebbene le modifiche avvengano in genere più rapidamente.*
  
3. Nella pagina dei domini personalizzati, fai clic sui tre punti nella riga che contiene il "dominio predefinito" di destinazione e seleziona **Modifica** dal menu.
4. Nella finestra di dialogo che viene visualizzata, seleziona la casella di spunta **Assegna un dominio personalizzato**.
5. Specifica il dominio personalizzato desiderato nel campo **Nome dominio** (ad esempio, *api.mycompany.com*)
6. Copia il CRN (Cloud Resource Name) dal Gestore certificato per il certificato che è stato caricato durante la configurazione iniziale.
7. Incolla il CRN che hai copiato nel campo **CRN certificato**.
8. Fai clic su **Salva**. Il nome di dominio specificato deve essere visualizzato nella riga accanto al dominio predefinito, a indicare che è stato applicato correttamente.

*Nota: prima di applicare il dominio personalizzato, il puntatore DNS verrà verificato garantendo che il CNAME del dominio personalizzato punti al dominio predefinito associato alle API. Se la configurazione DNS non è stata completata o le modifiche DNS dal passo 2 non sono ancora propagate, verrà visualizzato un errore e le impostazioni del dominio non verranno salvate. In tal caso, riprova periodicamente fino a 48 ore dopo la modifica delle impostazioni DNS. Se l'errore persiste oltre le 48 ore, verifica le tue impostazioni DNS o contatta il supporto {{site.data.keyword.Bluemix_notm}}.*
