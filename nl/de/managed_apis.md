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

# Eigene APIs
{: #manage_api}

Wählen Sie in der Navigation des Abschnitts **APIs** die Option **Verwaltete APIs** aus, um den Gesamtstatus der APIs anzuzeigen, die von Ihnen verwaltet werden oder früher verwaltet wurden, momentan jedoch nicht zugänglich sind. Wählen Sie **Gemeinsam genutzte APIs** aus, um alle APIs anzuzeigen, die in Ihrer {{site.data.keyword.Bluemix_notm}}-Organisation über das API-Management oder den {{site.data.keyword.apiconnect_full}}-Service gemeinsam genutzt wurden. Hier finden Sie auch **Preislisten** und Details für die verfügbaren {{site.data.keyword.apiconnect_service}}-Serviceoptionen.

Im Dashboard für APIs können alle APIs angezeigt werden, die über das API-Management verwaltet werden. 

## Verwaltete APIs anzeigen
{: #view_api}

Hier können APIs angezeigt werden, die für Cloud Foundry-Anwendungen, {{site.data.keyword.openwhisk_short}}-Aktionen und andere externe Quellen erstellt wurden.

1. Wählen Sie im {{site.data.keyword.Bluemix_notm}}-Dashboard das Symbol für **Menü** > **APIs** aus.
2. Klicken Sie zur Auswahl der Quelle auf **Verwaltete APIs**. Daraufhin wird eine Liste der momentan verwalteten APIs angezeigt. Die folgenden API-Typen sind verfügbar:
    * Benutzerdefinierte Endpunkte - Diese Einträge stellen APIs dar, die sich außerhalb der {{site.data.keyword.Bluemix_notm}}-Umgebung befinden und über den zugehörigen URL-Endpunkt überwacht werden. 
	* CF Apps - Diese Einträge sind Cloud Foundry-Apps, die entsprechendes API-Management beinhalten.
    * {{site.data.keyword.openwhisk_short}}-Apps - Diese Einträge stellen {{site.data.keyword.openwhisk_short}}-Aktionen dar, die in eine API eingeschlossen sind.

Wählen Sie den Namen einer API aus, um weitere Details zu dieser API anzuzeigen.

## Verwaltete APIs erstellen
{: #create_mgd_api}

Sie können eine API zur Liste der verwalteten APIs hinzufügen, ohne die Liste verlassen zu müssen. Wählen Sie dazu **Verwaltete API erstellen** aus.

Wählen Sie aus, ob Sie eine Cloud Foundry-Aktion, eine {{site.data.keyword.openwhisk_short}}-Aktion oder eine (externe) API für einen API-Proxy erstellen möchten, und geben Sie anschließend die Informationen für die neue API ein.  

API-Proxys (externe APIs) können nur hier hinzugefügt werden. Eine externe API ist eine API, die nicht im {{site.data.keyword.Bluemix_notm}}-Organisationsbereich erstellt oder gespeichert wurde. Die Verwaltung einer externen API erfolgt durch Angabe der URL des externen Endpunkts. Dies ist nützlich, wenn Sie testen möchten, ob das API-Management Ihre Anforderungen erfüllt, oder wenn Sie bereits über APIs mit vorhandenen URLs verfügen, die Sie nicht unterbrechen möchten. 

Weitere Informationen zu den erforderlichen Einstellungen für die API-Erstellung finden Sie in [APIs verwalten](manage_apis.html).

## Mit gemeinsam genutzten APIs arbeiten
{: #share_api}

Im Abschnitt **Gemeinsam genutzte APIs** können Sie die APIs anzeigen, die von anderen Benutzern erstellt und mit Ihnen gemeinsam genutzt werden. Ferner können für die APIs, die Cloud Foundry-Apps, {{site.data.keyword.openwhisk_short}}-Aktionen und dem {{site.data.keyword.appconserviceshort}}-Service zugeordnet sind, API-Schlüssel erstellt werden.

1. Klicken Sie im {{site.data.keyword.Bluemix_notm}}-Dashboard auf das Symbol für **Menü** > **APIs**.
2. Wählen Sie in der Navigation **Gemeinsam genutzte APIs** aus. Hier werden alle APIs angezeigt, die Sie nutzen können.
3. Wählen Sie eine API aus, um das zugehörige Entwicklerportal zu öffnen, in dem Sie einen Plan für die Nutzung subskribieren können. 
4. Lesen Sie nach Auswahl einer API die Informationen im Abschnitt [APIs verwalten](manage_apis.html), um die folgenden Tasks auszuführen: 
    * API-Nutzung anzeigen
    * API-Schlüssel erstellen
    * API-Explorer zum Anzeigen von Dokumentation und Testen der API verwenden
