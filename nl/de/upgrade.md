---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-10"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Auf weitere Funktionen des API-Managements zugreifen
{: #upgrade}

Die Funktion für das API-Management, die zusammen mit der {{site.data.keyword.Bluemix}}-API bereitgestellt wird, erlaubt Ihnen die eingeschränkte Steuerung von Aufrufquoten und von OAuth sowie die Anzeige von Analysen. Durch ein Upgrade auf den {{site.data.keyword.apiconnect_full}}-Service kann das API-Management erweitert werden. Der {{site.data.keyword.apiconnect_short}}-Service bietet mehr Auswahlmöglichkeiten bei Sicherheitsrichtlinien und eine bessere Steuerung der Ratenbegrenzungen. Darüber hinaus haben Sie die Möglichkeit, ein vollständig anpassbares Entwicklerportal zu konfigurieren, um API-Inhalte zu teilen und mit der Entwickler-Community zu kommunizieren. Weitere Vorteile:
* Lebenszyklusmanagement
* Zusammengesetzte APIs
* Web-Service-Integration
* Protokollmediation
* API-Generierung aus Schemas
* Micro-Service-Entwicklung

Die Migration auf den {{site.data.keyword.apiconnect_short}}-Service ist einfach. Die APIs, die über das API-Management gesteuert werden, müssen Sie nicht erneut erstellen. Sie können APIs automatisch oder manuell migrieren.

## APIs automatisch auf {{site.data.keyword.apiconnect_short}} migrieren
{: #auto_migrate_api}

Wenn Sie ein Upgrade auf {{site.data.keyword.apiconnect_short}} durchführen möchten, dann müssen Sie die APIs über das API-Management auf den {{site.data.keyword.apiconnect_short}}-Service migrieren. Wählen Sie hierzu die folgende Prozedur für den API-Typ aus, der migriert werden soll, und führen Sie die entsprechenden Schritte aus.

### Cloud Functions-API

1. Wählen Sie im {{site.data.keyword.Bluemix_notm}}-Menü die Option **Funktionen** aus, um Ihre Cloud Functions-Komponenten anzuzeigen.

2. Wählen Sie in der Liste 'Funktionen' in der Navigation **APIs** aus.

3. Wählen Sie den Namen der Funktions-API aus, die migriert werden soll.

4. Wählen Sie in der Navigation **Definition** aus.

5. Wählen Sie im Abschnitt *API-Definitionsdatei* die Optionen für **API-Definitionsdatei** > **In API Connect exportieren** > **API exportieren** aus. Wenn Sie bereits über einen {{site.data.keyword.apiconnect_short}}-Service verfügen, dann wird die API automatisch auf den vorhandenen Service migriert. Wenn Sie noch keinen {{site.data.keyword.apiconnect_short}}-Service konfiguriert haben, dann wird der Service automatisch mit einem kostenlosen Lite-Plan hinzugefügt und die API wird migriert. Wenn die Bereitstellung für die Instanz fehlgeschlagen ist, dann müssen Sie die Schritte zum [manuellen Migrieren von APIs auf {{site.data.keyword.apiconnect_short}}](#man_migrate_api) ausführen, um die Migration auf den neuen Service manuell auszuführen. 

6. Bevor Sie die Anzeige der ursprünglichen API schließen, müssen Sie den Schieberegler für **Verwaltete API zugänglich machen** inaktivieren. Dadurch wird verhindert, dass Benutzer weiterhin mit dem Endpunkt der alten Version arbeiten können.

### Cloud Foundry-API

1. Öffnen Sie die vorhandene Cloud Foundry-API-Quelle im {{site.data.keyword.Bluemix_notm}}-Dashboard. 

2. Wählen Sie im Navigationsmenü die Option **API-Management** aus.

3. Wählen Sie in der Navigation **Definition** aus.

4. Wählen Sie die Optionen für **API-Definitionsdatei** > **In API Connect exportieren** > **API exportieren** aus. Wenn Sie bereits über einen {{site.data.keyword.apiconnect_short}}-Service verfügen, dann wird die API automatisch auf den vorhandenen Service migriert. Wenn Sie noch keinen {{site.data.keyword.apiconnect_short}}-Service konfiguriert haben, dann wird der Service automatisch mit einem kostenlosen Lite-Plan hinzugefügt und die API wird migriert. Wenn die Bereitstellung für die Instanz fehlgeschlagen ist, dann müssen Sie die Schritte zum [manuellen Migrieren von APIs auf {{site.data.keyword.apiconnect_short}}](#man_migrate_api) ausführen, um die Migration auf den neuen Service manuell auszuführen.
   
5. Nachdem der Inhalt auf die {{site.data.keyword.apiconnect_short}}-Instanz migriert wurde, müssen Sie den Link auswählen, der für den Zugriff auf die migrierte Version bereitgestellt wird.
    **Wichtig:** Um Probleme mit mehreren aktiven Instanzen der API zu vermeiden, sollten Sie sicherstellen, dass Sie den Schieberegler *API verwalten* in der ursprünglichen Version der API inaktivieren.

6. Wählen Sie die Registerkarte **APIs** in der Navigation aus.

7. Wählen Sie **Entwürfe** aus, um die neue API anzuzeigen.

## APIs manuell auf {{site.data.keyword.apiconnect_short}} migrieren
{: #man_migrate_api}

Wenn der Prozess zum Migrieren Ihrer API auf den {{site.data.keyword.apiconnect_short}}-Service nicht korrekt abgeschlossen werden konnte, dann führen Sie die folgenden Schritte aus, um die Migration manuell durchzuführen:

1. Öffnen Sie die API.
	1. Melden Sie sich bei {{site.data.keyword.Bluemix_notm}} an.
	2. Führen Sie für eine Cloud Foundry-App die folgenden Schritte aus: 
		1. Wählen Sie im Menü die Option **Dashboard** aus.
		2. Wählen Sie den Namen der Cloud Foundry-App aus, die migriert werden soll.
		3. Wählen Sie im Navigationsbereich die Option **API-Management** aus.
	3. Führen Sie für eine Cloud Functions-Aktion die folgenden Schritte aus: 
		1. Wählen Sie im Menü die Option **Funktionen** aus.
		2. Wählen Sie in der Navigation **APIs** aus.
		3. Wählen Sie den Namen der API aus, die migriert werden soll.
2. Laden Sie das Swagger-Dokument für die API aus dem API-Management herunter.
    1. Wählen Sie in der Navigation **Definition** aus.
	2. Wählen Sie die Option **API-Definitionsdatei** aus.
    3. Wählen Sie abhängig vom verwendeten Dateityp entweder **YAML exportieren** oder **JSON exportieren** aus, um die Definition der API herunterzuladen. Daraufhin wird die Datei in den Downloadordner Ihres Systems heruntergeladen.
3. Erstellen Sie die {{site.data.keyword.apiconnect_short}}-Instanz und bereiten Sie diese vor. 
	1. Rufen Sie in der Navigation **APIs** auf, um die Services zu filtern.
	2. Wählen Sie den API Connect-Service aus. 
    3. Erstellen Sie eine Instanz des {{site.data.keyword.apiconnect_short}}-Service aus dem {{site.data.keyword.Bluemix_notm}}-Katalog.
	4. Wählen Sie Ihren Plan aus. Beim Lite-Plan handelt es sich um die kostenlose Option.
	5. Wählen Sie **Erstellen**, um die Instanz zu erstellen.
4. Importieren Sie das Swagger-Dokument in die {{site.data.keyword.apiconnect_short}}-Instanz. Führen Sie dazu die folgenden Schritte aus:
	1. Wählen Sie im Dashboard für den {{site.data.keyword.apiconnect_short}}-Service **Navigieren zu... (>>)** > **Entwürfe** im Menü aus.
	2. Wählen Sie Sie die API-Registerkarte aus.
	3. Wählen Sie **+Hinzufügen** > **API aus Datei oder URL importieren** aus.
	4. Suchen Sie die Swagger-Datei, die Sie aus dem API-Management heruntergeladen haben, und wählen Sie sie aus. Wählen Sie **Öffnen** aus.
	5. Wählen Sie **Importieren** aus, um die API in den {{site.data.keyword.apiconnect_short}}-Service zu importieren.
5. Um Probleme mit mehreren aktiven Instanzen der API zu vermeiden, sollten Sie sicherstellen, dass Sie den Schieberegler *API verwalten* in der ursprünglichen Version der API inaktivieren.

Ihre API steht in der {{site.data.keyword.apiconnect_short}}-Serviceinstanz zur Verfügung. 

## API veröffentlichen

Führen Sie die folgenden Schritte aus, um mit der Veröffentlichung der API fortzufahren:

1. Erstellen Sie einen Katalog.
	1. Wählen Sie **+Hinzufügen** aus, um einen Katalog zu erstellen.
	2. Geben Sie einen Anzeigenamen und einen Namen für den Katalog ein und wählen Sie **Hinzufügen** aus.
	3. Wählen Sie den erstellten Katalog aus.
2. Geben Sie Einstellungen für die API an.
    1. Wählen Sie **Produkt erstellen** aus.
	2. Geben Sie einen Namen für das Produkt an.
	2. Wählen Sie das erstellte Produkt aus, um die zugehörigen Einstellungen anzuzeigen.
	3. Legen Sie die Ratenbegrenzung für die API fest.
	4. Legen Sie die Stufe für die API fest.
3. Fügen Sie gegebenenfalls den Endpunkt für die API hinzu.
    1. Wählen Sie die API aus.
	2. Wählen Sie die Registerkarte 'Assembly' aus.
	3. Fügen Sie den Endpunkt hinzu, sofern dieser noch nicht angegeben wurde.
	
 Nach der Migration Ihrer APIs können Sie durch Öffnen der Kachel für den {{site.data.keyword.apiconnect_short}}-Service und über das {{site.data.keyword.Bluemix_notm}}-Dashboard auf sämtliche Funktionen des API-Managements zugreifen. 

