---



copyright:

  years: 2017
lastupdated: "2017-06-26"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

# Comandi di gestione delle API Bluemix
{: #apimgt_cli}

Versione: 1.0.0

Puoi installare il plugin dell'interfaccia riga di comando (CLI) di gestione delle API {{site.data.keyword.Bluemix_notm}} per completare le azioni di gestione comuni delle tue API con lo scripting. Le seguenti informazioni elencano i comandi inclusi con il plugin della CLI di gestione delle API, compresi i rispettivi nomi, opzioni, utilizzo, prerequisiti, descrizioni ed esempi.
{:shortdesc}

**Nota:** i **Prerequisiti** elencano quali azioni sono richieste prima di utilizzare il comando. I comandi che non hanno alcuna azione prerequisita elencano **Nessuno**. Altrimenti, i prerequisiti possono includere una o più delle seguenti azioni:

**Nota:** puoi utilizzare il formato breve dei comandi bluemix; ad esempio, `bx apim` è l'abbreviazione di `bluemix apim`.

Utilizza gli indici nella seguente tabella per fare riferimento ai comandi di gestione delle API utilizzati più frequentemente.

<table summary="Comandi gestione API.">
<caption>Tabella 1. Comandi gestione API</caption>
 <thead>
 <th colspan="5">Comandi gestione API</th>
 </thead>
 <tbody>
 <tr>
 <td>[bluemix apim help](apimgt_cli.html#apim_help)</td>
 <td>[bluemix apim api](apimgt_cli.html#apim_api)</td>
 <td>[bluemix apim apis](apimgt_cli.html#apim_apis)</td>
 <td>[bluemix apim api-create](apimgt_cli.html#apim_api-create)</td>
 <td>[bluemix apim api-delete](apimgt_cli.html#apim_api-delete)</td>
 <td>[bluemix apim api-expose](apimgt_cli.html#apim_api-expose)</td>
 <td>[bluemix apim api-share](apimgt_cli.html#apim_api-share)</td>
 <td>[bluemix apim api-unexpose](apimgt_cli.html#apim_api-unexpose)</td>
 <td>[bluemix apim api-unshare](apimgt_cli.html#apim_api-unshare)</td>
 <td>[bluemix apim api-update](apimgt_cli.html#apim_api-update)</td>
 <td>[bluemix apim keys](apimgt_cli.html#apim_keys)</td>
 </tr>
 </tbody>
 </table>
 
  
## Guida gestione API
{: #apim_help}
Visualizza la guida generale per i comandi integrati di primo livello e gli spazi dei nomi supportati della CLI di gestione delle API oppure la guida per un comando o uno spazio dei nomi integrati specifici.

### Sintassi

```
bluemix apim help <object-action>
```
{: codeblock}

### Opzioni del comando

   <dl>
   <dt>object-action (facoltativo)</dt>
   <dd>Il comando per cui viene virtualizzata la guida. Se non specificato, viene visualizzata la guida generale della CLI di gestione delle API.</dd>
   </dl>

### Esempi

Visualizza la guida generale per la CLI di gestione delle API:

```
bluemix apim help
```

Visualizza la guida per il comando `api-create`:

```
bluemix apim help api-create
```



## bluemix apim api
{: #apim_api}
Visualizza le proprietà di una API gestita.

### Sintassi
```
bluemix apim api --name <API_NAME> [--swagger]
```
{: codeblock}

### Indicatore obbligatorio
   <dl>
   <dt>--name</dt>
   <dd>Specifica il nome dell'API gestita</dd>
   </dl>


### Opzioni del comando
   <dl>
   <dt>--swagger</dt>
   <dd>Visualizza le informazioni dal documento di definizione Open API nell'output</dd>
   </dl>

### Output

Il comando restituisce una tabella che elenca le seguenti informazioni sull'API specificata:

   <dl>
     <dt>Nome</dt>
	 <dd>Il nome dell'API.</dd>
	 <dt>Tipo</dt>
	 <dd>Il tipo de API. Le voci valide sono <em>whisk</em>, <em>cf-apps</em> o <em>user-defined</em></dd>
	 <dt>Gestita</dt>
	 <dd>Se il valore è true, indica che l'endpoint viene rilevato ma non esposto nel gateway.</dd>
	 <dt>Esposta</dt>
	 <dd>Indica se l'API è live nel gateway (<em>true</em>) o meno (<em>false</em>).
	 <dt>Condivisa</dt>
	 <dd>Indica se l'API vene condivisa all'esterno della tua organizzazione Bluemix (<em>true</em>) o meno (<em>true</em>).</dd>
	 <dt>URL gestito</dt>
	 <dd>Specifica l'ubicazione della versione condivisa dell'API.</dd>
   </dl>

   
### Esempi

Visualizza le proprietà dell'API denominata cloudfound1:

```
bluemix apim api cloudfound1
```

Visualizza i contenuti del file di definizione e le proprietà per l'API denominata api2:

```
bluemix apim api api2 --swagger
```


## bluemix apim apis
{: #apim_apis}


Elenca le API disponibili e identificate sul server endpoint identificato.

### Sintassi
```
bluemix apim apis [--api-provider <API_PROVIDER>][--exposed][--shared]
```
{: codeblock}

### Opzioni del comando

Nota: se non vengono specificate opzioni, vengono restituite tutte le informazioni di tutte le API.
   <dl>
   <dt>--api-provider </dt>
   <dd>Restituisce solo i tipi di API che specifichi qui. Le opzioni valide sono <em>whisk</em> per le API Openwhisk, <em>cf-apps</em> per le API Cloud Foundry e <em>user-defined</em> per le API non associate a Openwhisk o Cloud Foundry.</dd>
   <dt>--exposed</dt>
   <dd>Restituisce solo le API che vengono esposte.</dd>
   <dt>--shared</dt>
   <dd>Restituisce solo le API che vengono condivise all'esterno della tua organizzazione {{site.data.keyword.Bluemix_notm}}.</dd>
   </dl>

### Output

Il comando restituisce una tabella che elenca le seguenti informazioni sulle API specificate:

   <dl>
     <dt>Nome</dt>
	 <dd>Il nome dell'API.</dd>
	 <dt>Tipo</dt>
	 <dd>Il tipo de API. Le voci valide sono <em>whisk</em>, <em>cf-apps</em> o <em>user-defined</em></dd>
	 <dt>Gestita</dt>
	 <dd>Se il valore è true, indica che l'endpoint viene rilevato ma non esposto nel gateway.</dd>
	 <dt>Esposta</dt>
	 <dd>Indica se l'API è live nel gateway (<em>true</em>) o meno (<em>false</em>).
	 <dt>Condivisa</dt>
	 <dd>Indica se l'API vene condivisa all'esterno della tua organizzazione Bluemix (<em>true</em>) o meno (<em>false</em>).</dd>
	 <dt>URL gestito</dt>
	 <dd>Specifica l'ubicazione della versione condivisa dell'API se è esposta. Il valore è <em>undefined</em> quando l'API non è esposta. </dd>
   </dl>


### Esempi

Restituisci tutte le API che sono disponibili sul gestore endpoint:

```
bluemix apim apis 
```

Restituisci tutte le API OpenWhisk che sono disponibili:

```
bluemix apim apis --api-provider whisk
```

## bluemix apim api-create
{: #apim_api-create}


Rendi un'API non gestita esistente un'API gestita importando il rispettivo file Swagger.

### Sintassi

```
bluemix apim api-create --name <API_NAME> --file <PATH_TO_OPEN_API_DEFINITION_FILE> --provider cf-apps [--expose]
```
{: codeblock}

### Indicatori obbligatori

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Specifica il nome dell'API che vuoi gestire.</dd>
   <dt>--file</dt>
   <dd>Fornisce il percorso al file di definizione Open API, che è nel formato YAML o JSON.</dd>
   <dt>--provider</dt>
   <dd>Specifica il tipo di API che stai creando. Nota: l'unica voce valida per questa operazione è <em>cf-apps</em>.
   </dl>

### Opzione del comando

   <dl>
   <dt>--expose</dt>
   <dd>Espone l'endpoint automaticamente dopo averlo creato.</dd>
   </dl>

### Output

Il comando fornisce le seguenti informazioni:
* Creazione eseguita correttamente
* Errore (con descrizione dell'errore)

### Esempi

Gestisci un'API Cloud Foundry denominata apinumber1 che dispone di un file di definizione yaml denominato reservations1:

```
bluemix apim api-create --name apinumber1 --file ~/dev/apis/reservations1.yaml --provider cf-apps
```

Gestisci un'applicazione Cloud Foundry denominata cfapi che dispone di un file di definizione json denominato definition1:

```
bluemix apim api-create --name cfapi --file ~/dev/apis/definition1.json --provider cf-apps
```

## bluemix apim api-delete
{: #apim_api-delete}

Rimuove un'API gestita dal database.

### Sintassi

```
bluemix apim api-delete --name <API_NAME> --confirm
```
{: codeblock}

### Indicatori obbligatori

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Specifica il nome dell'API che vuoi eliminare. **Importante:** l'eliminazione di un'API Cloud Foundry la rimuove dalla stato gestito, ma l'applicazione Cloud Foundry non viene eliminata. L'eliminazione di un'API OpenWhisk elimina l'API completa e deve essere ricreata dopo che viene eliminata.</dd>
   <dt>--confirm</dt>
   <dd>Conferma che il comando deve essere completato senza fornire una richiesta di conferma.</dd>
   </dl>


### Output

Il comando fornisce le seguenti informazioni:
* Eliminazione eseguita correttamente
* Errore (con descrizione dell'errore)

### Esempi

Elimina l'API Cloud Foundry cloudapi1:

```
bluemix apim api-delete --name cloudapi1 --confirm
```


## bluemix apim api-expose
{: #apim_api-expose}

Rende un'API gestita visibile ad altri all'interno della mia organizzazione {{site.data.keyword.Bluemix_notm}}.

### Sintassi
```
bluemix apim api-expose --name <API_NAME>
```
{: codeblock}

### Indicatore obbligatorio

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Specifica il nome dell'API che vuoi esporre.</dd>
   </dl>

### Output

Il comando fornisce le seguenti informazioni:
* Esposizione eseguita correttamente
* Errore (con descrizione dell'errore)

### Esempio

Esponi un'API Cloud Foundry denominata cloudfound1 con la mia organizzazione {{site.data.keyword.Bluemix_notm}}:

```
bluemix apim api-expose --name cloudfound1
```


## bluemix apim api-share
{: #apim_api-share}


Rende un'API gestita visibile ad altri all'esterno della mia organizzazione {{site.data.keyword.Bluemix_notm}}. 

### Sintassi
```
bluemix apim api-share --name <API_NAME>
```
{: codeblock}

### Indicatore obbligatorio

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Specifica il nome dell'API che vuoi condividere. </dd>
   </dl>

### Output

Il comando fornisce le seguenti informazioni:
* Condivisione riuscita correttamente
* Errore (con descrizione dell'errore)

### Esempio

Condividi un'API Cloud Foundry denominata cloudfound1 all'esterno della mia organizzazione {{site.data.keyword.Bluemix_notm}}:
```
bluemix apim api-share --name cloudfound1
```


## bluemix apim api-unexpose
{: #apim_api-unexpose}


Annulla la visibilità di un'API gestita visibile ad altri all'interno della tua organizzazione {{site.data.keyword.Bluemix_notm}}.

### Sintassi
```
bluemix apim api-unexpose --name <API_NAME>
```
{: codeblock}

### Indicatore obbligatorio

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Specifica il nome dell'API che vuoi rimuovere dalla visibilità agli altri nella tua organizzazione {{site.data.keyword.Bluemix_notm}}.</dd>
   </dl>

### Output

Il comando fornisce le seguenti informazioni:
* Annullamento visibilità riuscito correttamente
* Errore (con descrizione dell'errore)

### Esempio

Rimuovi un'API OpenWhisk denominata openwhisk1 dalla visibilità ad altri membri della mia organizzazione {{site.data.keyword.Bluemix_notm}}:

```
bluemix apim api-unexpose --name openwhisk1
```


## bluemix apim api-unshare
{: #apim_api-unshare}


Annulla la visibilità di un'API gestita visibile ad altri all'esterno della mia organizzazione {{site.data.keyword.Bluemix_notm}}.

### Sintassi
```
bluemix apim api-unshare --name <API_NAME>
```
{: codeblock}

<strong>Indicatore obbligatorio</strong>:

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Specifica il nome dell'API di cui vuoi annullare la condivisione. </dd>
   </dl>

### Output

Il comando fornisce le seguenti informazioni:
* Annullamento della condivisione riuscito correttamente
* Errore (con descrizione dell'errore)

### Esempio

Arresta la condivisione di un'API Cloud Foundry denominata cloudfound1 all'esterno della mia organizzazione {{site.data.keyword.Bluemix_notm}}: 

```
bluemix apim api-unshare --name cloudfound1
```



## bluemix apim api-update
{: #apim_api-update}


Aggiorna le impostazioni di una API gestita sostituendo il file di definizione. Importante: questa è una sostituzione completa delle definizioni esistenti nell'API con le definizioni in un nuovo file. Tutte le voci vuote o mancanti nel nuovo file che sono presenti nel file esistente vengono rimosse dalla definizione.

### Sintassi
```
bluemix apim api-update --name <API_NAME> --file <NEW_OPEN_API_DEFINITION_FILE>
```
{: codeblock}

### Indicatori obbligatori

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Specifica il nome dell'API che vuoi aggiornare. </dd>
   <dt>--file</dt>
   <dd>Fornisce il percorso al file di definizione Open API di sostituzione, che è nel formato YAML o JSON. </dd>
   </dl>

### Output

Il comando fornisce le seguenti informazioni:
* Aggiornamento riuscito correttamente
* Errore (con descrizione dell'errore)


### Esempio

Aggiorna un'API OpenWhisk denominata whiskapi1 con un file di definizione con il nome definition1.json: 

```
bluemix apim api-update --name whiskapi1 --filePath ~/path/definitions/definition1.json
```


## bluemix apim keys
{: #apim_api-keys}


Visualizza le proprietà delle chiavi che sono associate a una API gestita. 

### Sintassi
```
bluemix apim api-keys --name <API_NAME> --bluemix|--external
```
{: codeblock}

### Indicatori obbligatori

   <dl>
   <dt>--name <i>API_NAME</i></dt>
   <dd>Specifica il nome dell'API che vuoi esporre.</dd>
   <dt>--bluemix</dt>
   <dd>Elenca le chiavi API {{site.data.keyword.Bluemix_notm}} per l'API specificata.</dd>
   <dt>--external</dt>
   <dd>Elenca le chiavi API esterne per l'API specificata. </dd>
   </dl>

### Output

Il comando restituisce una tabella che elenca le seguenti informazioni sulle API specificate:


   <dl>
     <dt>Nome della chiave</dt>
	 <dd>Il nome della chiave API. </dd>
	 <dt>Tipo di chiave</dt>
	 <dd>Il tipo della chiave API. Le voci valide sono <em>bluemix</em> e <em>external</em>.</dd>
	 <dt>ID client</dt>
	 <dd>Il nome del client che viene identificato con la chiave. </dd>
	 <dt>Segreto fornito</dt>
	 <dd>Indica se il segreto API viene fornito per l'API. I valori possibili sono <em>true</em> se è presente un segreto, altrimenti <em>false</em>.
   </dl>


### Esempi

Restituisci tutte le chiavi esterne associate all'API denominata cloudfound1.

```
bluemix apim --name cloudfound1 --external
```

Restituisci le chiavi che consentono alle persone all'interno della mia organizzazione {{site.data.keyword.Bluemix_notm}} di visualizzare la mia API denominata myapi1.

```
bluemix apim --name myapi1 --bluemix 
```
 
