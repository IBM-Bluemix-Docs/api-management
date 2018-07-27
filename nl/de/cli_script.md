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

# Befehle mit API-Management-CLI ausführen
{: #apim-cli-over}

Sie können die {{site.data.keyword.Bluemix_notm}}-API-Management-CLI (Command-Line Interface; Befehlszeilenschnittstelle) verwenden, um bestimmte Tasks mit der Befehlszeile auszuführen, die Sie ebenfalls mit der grafischen {{site.data.keyword.Bluemix_notm}}-Benutzerschnittstelle ausführen können. Die Befehle können einzeln in einem Terminalfenster eingegeben oder in einer Sequenz in einem Script aufgerufen werden.
{:shortdesc}

## Voraussetzungen
{: #apim-cli-script-prereq}

Bevor Sie die API-Management-CLI verwenden können, müssen Sie zuerst die folgenden Schritte ausführen:

* Fordern Sie eine [Bluemix-ID](../../admin/adminpublic.html#signing-up-for-bluemix){: new_window} an. 
* Laden Sie die [Bluemix-Befehlszeile](../../cli/reference/bluemix_cli/index.html#getting-started){: new_window} herunter und installieren Sie sie.
* Installieren Sie das {{site.data.keyword.Bluemix_notm}} [Plug-in für die API-Managementbefehlszeile](../../cli/reference/bluemix_cli/index.html#install_plug-in){: new_window}.
* [Melden Sie sich ](../../cli/reference/bluemix_cli/bx_cli.html){: new_window} bei der {{site.data.keyword.Bluemix_notm}}-Befehlszeile an.

## Beispiel einer CLI-Befehlsfolge für eine API

In den folgenden Schritten wird ein vollständiger Zyklus von API-Managementbefehlen gezeigt, mit dem ein Gateway zu einer API hinzugefügt und dann wieder aus der API entfernt wird:

1. Melden Sie sich bei {{site.data.keyword.Bluemix_notm}} an. 
    ```
    bluemix login -a https://api.ng.bluemix.net -c account_ID (1) -u username -p password
    ```
    {:codeblock}
    Mit diesem Befehl melden Sie sich über die Befehlszeilenschnittstelle bei der {{site.data.keyword.Bluemix_notm}}-Standardorganisation an.

2. Zeigen Sie Ihre APIs an.
    ```
    bluemix apim apis
    ```
    {:codeblock}
    Zeigt die APIs in Ihrer Standardorganisation an.

3. Erstellen Sie eine API.
    ```
    bluemix apim api-create --name <API_NAME> --file <path_to_Swagger_file>
    ```
    {:codeblock}
    Verwendet die Swagger-Datei zum Erstellen einer verwalteten API anhand der API, die Sie in Ihrer {{site.data.keyword.Bluemix_notm}}-Organisation angeben.

4. Aktualisieren Sie eine vorhandene API-Definition.
    ```
    bluemix apim api-update --name <API_NAME> --file <path_to_new_Swagger_file>
    ```
    {:codeblock}
    Ersetzt die vorhandene Definition der API, die Sie angeben, durch die neue Definition der Swagger-Datei.

5. Machen Sie die API zugänglich.
    ```
    bluemix apim api-expose --name <API_NAME>
    ```
    {:codeblock}
    Macht die API zugänglich.

6. Nutzen Sie die API gemeinsam.
    ```
    bluemix apim api-share --name <API_NAME>
    ```
    {:codeblock}
    Nutzt die API gemeinsam mit anderen Benutzern außerhalb Ihrer {{site.data.keyword.Bluemix_notm}}-Organisation.

7. Beenden Sie die Zugänglichmachung der API.
    ```
    bluemix apim api-unexpose --name <API_NAME>
    ```
    {:codeblock}
    Beendet die gemeinsame Nutzung der API außerhalb Ihrer {{site.data.keyword.Bluemix_notm}}-Organisation.

8. Zeigen Sie die Schlüssel Ihrer API an.
    ```
    bluemix apim keys --name <API_NAME>
    ```
    {:codeblock}
    Zeigt die Schlüssel an, die Ihrer API zugeordnet sind (sofern vorhanden).

9. Beenden Sie die gemeinsame Nutzung der API.
    ```
    bluemix apim api-unshare --name <API_NAME>
    ```
    {:codeblock}
    Beendet die gemeinsame Nutzung der API.
	
10. Entfernen Sie die API.
    ```
    bluemix apim api-delete --name <API_NAME>
    ```
    {:codeblock}
    Entfernt das Gateway aus der API. Sie wird nicht mehr verwaltet.
    Wichtig: Wenn Sie eine Cloud Foundry-API löschen, dann bleibt die Cloud Foundry-Basis-App im {{site.data.keyword.Bluemix_notm}}-Service erhalten, wird jedoch nicht mehr verwaltet. Eine OpenWhisk-API, die gelöscht wird, entfernt alle Interaktionen zwischen den einzelnen OpenWhisk-Aktionen. Nachdem die OpenWhisk-API gelöscht wurde, muss sie erneut erstellt werden, wenn Sie sie wieder verwenden möchten.
    
Eine vollständige Liste der API-Managementbefehle und ihrer Optionen finden Sie im Abschnitt zu den [Befehlen der Befehlszeilenschnittstelle](../../cli/plugins/api-management-cliplugin/index.html).

