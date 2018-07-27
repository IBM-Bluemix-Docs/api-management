---

copyright:
  years: 2017
lastupdated: "2017-07-25"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Esegui i comandi con la CLI di gestione API 
{: #apim-cli-over}

Puoi utilizzare la CLI di gestione API {{site.data.keyword.Bluemix_notm}} per completare alcune delle stesse attività della riga di comando che puoi completare con l'interfaccia utente grafica {{site.data.keyword.Bluemix_notm}}. I comandi possono essere immessi individualmente in una finestra del terminale o richiamati in una sequenza in uno script.
{:shortdesc}

## Prerequisiti
{: #apim-cli-script-prereq}

Prima di poter utilizzare la CLI di gestione API, devi aver completato la seguente procedura: 

* Ottieni un [ID Bluemix](../../admin/adminpublic.html#signing-up-for-bluemix){: new_window}. 
* Scarica e installa la [Riga di comando Bluemix](../../cli/reference/bluemix_cli/index.html#getting-started){: new_window}.
* Installa il {{site.data.keyword.Bluemix_notm}} [Plugin della riga di comando dell'API](../../cli/reference/bluemix_cli/index.html#install_plug-in){: new_window}.
* [Accedi](../../cli/reference/bluemix_cli/bx_cli.html){: new_window} alla riga di comando {{site.data.keyword.Bluemix_notm}}.

## Sequenza di comandi CLI di esempio per un'API

I seguenti passi illustrano un ciclo completo di comandi di gestione delle API dall'aggiunta di un gateway a un'API alla rimozione del gateway dall'API:

1. Accedi a {{site.data.keyword.Bluemix_notm}} 
    ```
    bluemix login -a https://api.ng.bluemix.net -c account_ID (1) -u username -p password
    ```
    {:codeblock}
    Ti permette di accedere alla tua organizzazione {{site.data.keyword.Bluemix_notm}} predefinita con l'interfaccia riga di comando.

2. Visualizza le tue API
    ```
    bluemix apim apis
    ```
    {:codeblock}
    Visualizza le API nella tua organizzazione predefinita.

3. Crea un'API
    ```
    bluemix apim api-create --name <API_NAME> --file <path_to_Swagger_file>
    ```
    {:codeblock}
    Utilizza il file Swagger per creare un'API gestita dall'API che specifichi nella tua organizzazione {{site.data.keyword.Bluemix_notm}}.

4. Aggiorna una definizione API esistente 
    ```
    bluemix apim api-update --name <API_NAME> --file <path_to_new_Swagger_file>
    ```
    {:codeblock}
    Sostituisce la definizione esistente dell'API che specifichi con la nuova definizione file Swagger.

5. Esponi l'API 
    ```
    bluemix apim api-expose --name <API_NAME>
    ```
    {:codeblock}
    Espone l'API.

6. Condividi l'API
    ```
    bluemix apim api-share --name <API_NAME>
    ```
    {:codeblock}
    Condivide l'API all'esterno della tua organizzazione {{site.data.keyword.Bluemix_notm}}.

7. Arresta l'esposizione dell'API
    ```
    bluemix apim api-unexpose --name <API_NAME>
    ```
    {:codeblock}
    Arresta la condivisione dell'API all'esterno della tua organizzazione {{site.data.keyword.Bluemix_notm}}.

8. Visualizza le chiavi per la tua API 
    ```
    bluemix apim keys --name <API_NAME>
    ```
    {:codeblock}
    Visualizza le chiavi associate alla tua API, se presenti.

9. Arresta la condivisione dell'API
    ```
    bluemix apim api-unshare --name <API_NAME>
    ```
    {:codeblock}
    Arresta la condivisione dell'API.
	
10. Rimuove l'API
    ```
    bluemix apim api-delete --name <API_NAME>
    ```
    {:codeblock}
    Rimuove il gateway dall'API. Non è più gestita.
    Importante: se elimini un'API Cloud Foundry, l'applicazione Cloud Foundry di base rimane nel servizio {{site.data.keyword.Bluemix_notm}}, ma non è più gestita. Un'API OpenWhisk che viene eliminata, rimuove tutte le interazioni tra le azioni OpenWhisk individuali. Dopo che viene eliminata l'API OpenWhisk, deve essere ricreata se desideri riutilizzarla.
    
Consulta [Comandi dell'interfaccia della riga di comando](../../cli/plugins/api-management-cliplugin/index.html) per un elenco completo dei comandi di gestione delle API e le rispettive opzioni.

