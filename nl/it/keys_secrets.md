---

copyright:
  years: 2017,2018
lastupdated: "2018-01-05"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Gestisci chiavi e segreti
{: #keys_secrets}

Quando le tue API sono gestite dalla gestione delle API, puoi utilizzare le chiavi e i segreti per controllare l'accesso alle API.

## Creazione di una chiave e di un segreto
{: #create_key_secret}

Per aggiungere una chiave alla tua API, completa la seguente procedura:

1. Apri la tua applicazione Cloud Foundry o l'API {{site.data.keyword.openwhisk_short}}, se non sono già aperte.

2. Seleziona *Gestione API* nel riquadro di navigazione.

3. Seleziona la scheda Condivisione e chiavi per tale applicazione o API. *Nota: non puoi visualizzare le schede finché non salvi la tua applicazione o API per la prima volta.*

4. Assicurati che lo slider **Esponi API gestita** sia impostato nella posizione *attivo*. La tua API deve essere esposta prima di poter assegnare le chiavi.

5. Crea una chiave per un cliente che ha accesso alla tua organizzazione {{site.data.keyword.Bluemix_notm}}.
  1. Seleziona **Crea chiave API +** nella sezione *Condivisione nell'organizzazione {{site.data.keyword.Bluemix_notm}}*. Una chiave e un segreto vengono automaticamente creati e inseriti nei campi corretti. Non puoi aggiornare la chiave o il segreto per questo tipo di chiave. 
  2. Immetti un nome per la chiave e il segreto per aiutarti a identificarli. Ad esempio, il nome del cliente che la userà.
  3. Seleziona **Salva** per salvare la nuova chiave.
  4. Puoi ripetere i passi da *a* a *c* per ulteriori chiavi, se necessario. Puoi avere un massimo di 5 chiavi in questa sezione per API.

6. Crea una chiave per un cliente che non è un membro della tua organizzazione {{site.data.keyword.Bluemix_notm}}.
  1. Seleziona **Crea chiave API +** nella sezione *Condivisione esternamente all'organizzazione {{site.data.keyword.Bluemix_notm}}*. Una chiave viene automaticamente creata e immessa nel campo corretto. Non viene visualizzato inizialmente un segreto per questo tipo di chiave. Non puoi aggiornare la chiave. 
  2. Immetti un nome per la chiave per aiutarti a identificarla. Ad esempio, il nome del cliente che la userà.
  3. Facoltativo: se vuoi aggiungere un segreto alla chiave, seleziona **Collegamento del portale API** per la chiave a cui vuoi aggiungere il segreto e seleziona **Configura segreto API**.
  4. Seleziona **Salva** per salvare la nuova chiave.
  5. Puoi ripetere i passi da *a* a *d* per ulteriori chiavi, se necessario. Puoi avere un massimo di 5 chiavi in questa sezione per API.
Le chiavi vengono elencate per l'API quando viene selezionata la scheda *Condivisione e chiavi*.

## Specifica di una chiave e di un segreto in una chiamata API
{: #spec_key_secret}

I tuoi clienti possono richiamare soltanto la tua API se includono il segreto o la chiave corretti, o entrambi, nell'intestazione della chiamata. Per richiamare l'API, devono includere la chiave e il segreto nella chiamata API come illustrato nel seguente esempio:
```
curl --request PUT \
  --url https://appidtest.mybluemix.net/ \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --header 'x-ibm-client-secret: add_secret_here' \
  --data '{"id":999999999999999}'
```
{: codeblock}
Dove *add_secret_here* viene sostituito con il segreto per la chiave corretta. 

## Eliminazione di una chiave API
{: #delete_key}

Ad un certo punto, vorrai rimuovere una chiave. Forse un cliente che ha utilizzato la tua API crea la propria API e non ha più bisogno delle tue. Per assicurarti che nessuno dei suoi clienti stia ancora utilizzando la tua API, puoi eliminare la chiave. Per eliminare una chiave dal servizio, completa la seguente procedura:

1. Apri la tua applicazione Cloud Foundry o l'API {{site.data.keyword.openwhisk_short}}, se non sono già aperte.

2. Seleziona *Gestione API* nel riquadro di navigazione.

3. Seleziona la scheda *Condivisione e chiavi*.

4. Trova la chiave che desideri eliminare. Suggerimento: questo è il caso in cui è utile denominare le chiavi in modo che possano essere facilmente identificate.

5. Seleziona l'icona delle opzioni, che è i tre puntini verticali, accanto alla chiave che vuoi eliminare. 

6. Seleziona **Elimina chiave**.

7. Conferma l'eliminazione per rimuovere la chiave.
