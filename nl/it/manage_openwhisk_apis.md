---

copyright:
  years: 2017,2018
lastupdated: "2018-01-11"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creare API da azioni {{site.data.keyword.openwhisk_short}}
{: #manage_openwhisk_apis}

Le azioni {{site.data.keyword.openwhisk_short}} possono trarre vantaggio dall'essere gestite dalla gestione delle API.

Con la gestione delle API, puoi esporre un'azione {{site.data.keyword.openwhisk_short}} come una API. Dopo che hai definito la API, puoi applicare le politiche di sicurezza e di limitazione della frequenza, visualizzare l'utilizzo delle API e i log delle risposte e definire le politiche di condivisione delle API.  

Per creare una API {{site.data.keyword.openwhisk_short}}, completa la seguente procedura:

1. Nel dashboard {{site.data.keyword.openwhisk_short}}, fai clic sulla scheda **API**. Se già hai delle API {{site.data.keyword.openwhisk_short}} create, viene visualizzato un elenco delle tue API {{site.data.keyword.openwhisk_short}}. Se non hai alcuna API {{site.data.keyword.openwhisk_short}}, viene visualizzata una schermata di introduzione. 
2. Fai clic su **Crea una API {{site.data.keyword.openwhisk_short}}**. Viene visualizzata la finestra Crea API per {{site.data.keyword.openwhisk_short}}. 
3. Completa i campi nella sezione Informazioni API e fai quindi clic su **Crea operazione**. Viene visualizzata la finestra Crea operazione. Crei le operazioni per definire l'endpoint, il percorso https e il metodo per la tua API.
4. Nella finestra "Crea operazione", completa i campi richiesti per la tua operazione {{site.data.keyword.openwhisk_short}}. I campi presenti nella finestra "Crea operazione" includono:

    * Percorso - Il percorso in cui è ubicata la tua API. 
    * Verbo - Il metodo HTTP per la tua API. Seleziona tra i seguenti metodi:
	    * DELETE
		* GET
		* HEAD
		* OPTIONS
		* PATCH
		* POST
		* PUT
	* Pacchetto contenente l'azione - I pacchetti già disponibili nell'organizzazione che potrebbero avere l'azione che desideri utilizzare per questa API. Consulta [Utilizzo e creazione di pacchetti Cloud Functions](../openwhisk/openwhisk_packages.html) per ulteriori informazioni su questo campo.
	* Azioni - **Azioni disponibili in {{site.data.keyword.Bluemix_notm}}** è l'unica opzione disponibile.
	* Tipo di contenuto della risposta - Identifica il formato in cui l'API restituisce le informazioni. Puoi selezionare i seguenti formati:
	    * application/json - Questo è il formato predefinito ed è il più utilizzato.
		* text/html - Questo formato è utilizzato per le risposte usate in un sito Web.
		* text/plain - Questo formato è fornito in testo semplice e può essere utilizzato nei file CSV (comma-separated value).
		* image/svg+xml - Questo formato può essere utilizzato quando le acquisizioni schermo costituiscono il formato principale delle risposte.
		* Utilizza intestazione "Content-Type" dall'azione - Questo dipende dal tipo di contenuto che si trova nell'intestazione della risposta. 
	
5. Seleziona **Crea** per creare l'operazione. L'operazione viene aggiunta alla tabella Operazioni che richiamano azioni {{site.data.keyword.openwhisk_short}}.
5. Completa le restanti informazioni che vuoi completare. Puoi anche aggiungere o aggiornare le restanti informazioni in un secondo momento quando gestisci le tue API.
6. Fai clic su **Salva**. Viene visualizzata la pagina di panoramica della gestione delle API per la tua API e vengono visualizzate tutte le informazioni da te appena definite.
7. Continua la gestione della tua API con [Gestisci API](manage_apis.html).
