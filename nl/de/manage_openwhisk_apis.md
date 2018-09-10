---

copyright:
  years: 2017,2018
lastupdated: "2018-07-02"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# APIs aus {{site.data.keyword.openwhisk_short}}-Aktionen erstellen
{: #manage_openwhisk_apis}

{{site.data.keyword.openwhisk_short}}-Aktionen können von der Verwaltung mit dem API-Management profitieren.

Mit dem API-Management können Sie eine {{site.data.keyword.openwhisk_short}}-Aktion als API zugänglich machen. Nach dem Definieren der API können Richtlinien für Sicherheit und Ratenbegrenzung angewendet werden. Ferner ist es möglich, Protokolle zu API-Nutzung und -Antworten anzuzeigen und Richtlinien für die gemeinsame Nutzung von APIs festzulegen.  

Führen Sie die folgenden Schritte aus, um eine {{site.data.keyword.openwhisk_short}}-API zu erstellen:

1. Klicken Sie im {{site.data.keyword.openwhisk_short}}-Dashboard auf die Registerkarte **APIs**. Wenn Sie bereits {{site.data.keyword.openwhisk_short}}-APIs erstellt haben, wird eine Liste der {{site.data.keyword.openwhisk_short}}-APIs angezeigt. Wenn keine {{site.data.keyword.openwhisk_short}}-APIs vorhanden sind, wird eine Einführungsanzeige angezeigt. 
2. Klicken Sie auf **{{site.data.keyword.openwhisk_short}}-API erstellen**. Daraufhin wird das Fenster 'API für {{site.data.keyword.openwhisk_short}} erstellen' angezeigt. 
3. Füllen Sie die Felder im Abschnitt für die API-Informationen aus und klicken Sie dann auf **Operation erstellen**. Daraufhin wird das Fenster 'Operation erstellen' angezeigt. Operationen werden erstellt, um den Endpunkt, den HTTPS-Pfad und die Methode für die API zu definieren.
4. Füllen Sie im Fenster 'Operation erstellen' die erforderlichen Felder für Ihre {{site.data.keyword.openwhisk_short}}-Operation aus. Die Felder, die im Fenster 'Operation erstellen' enthalten sind, beinhalten die folgenden Felder:

    * Pfad - Der Pfad, auf dem sich Ihre API befindet. 
    * Verb - Die HTTP-Methode für Ihre API. Wählen Sie aus den folgenden Methoden aus:
	    * LÖSCHEN
		* ABRUFEN
		* KOPFZEILE
		* OPTIONEN
		* PATCH
		* POST
		* PUT
	* Aktion zum Paketinhalt - Die Pakete, die bereits in Ihrer Organisation bereitgestellt werden, enthalten möglicherweise die Aktion, die Sie für diese API verwenden möchten. Weitere Informationen zu diesem Feld finden Sie im Abschnitt [Cloud Functions-Pakete erstellen und verwenden](../openwhisk/openwhisk_packages.html).
	* Aktionen - Die Option **Aktionen, die in {{site.data.keyword.Bluemix_notm}} verfügbar sind ** ist die einzig verfügbare.
	* Antwortinhaltstyp - gibt das Format an, in welchem die API die Informationen zurückgibt. Sie können aus den folgenden Formaten auswählen:
	    * application/json - Dieses Format ist das am meisten genutzte Standardformat.
		* text/html - Dieses Format wird für Antworten, die auf einer Website eingesetzt werden, verwendet.
		* text/plain - Dieses Format wird in einfachem Text angegeben und kann in durch Kommas getrennten Wertedateien verwendet werden.
		* image/svg+xml - Dieses Format kann verwendet werden, wenn Screenshots das Hauptformat von Antworten sind.
		* Verwendung der Kopfzeile 'Inhaltstyp' aus Aktion - Dieses Format ist abhängig vom der Art des Inhalts, der in der Kopfzeile der Antwort enthalten ist. 
	
5. Wählen Sie **Erstellen**, um die Operation zu erstellen. Die Operation wird den Operationen hinzugefügt, die die Tabelle mit den {{site.data.keyword.openwhisk_short}}-Aktionen aufrufen.
5. Geben Sie die restlichen Informationen an, die Sie benötigen. Sie können diese Informationen auch später bei der Verwaltung der APIs hinzufügen oder aktualisieren.
6. Klicken Sie auf **Speichern**. Daraufhin wird die Übersichtsseite des API-Managements für die betreffende API mit den von Ihnen definierten Informationen angezeigt.
7. Fahren Sie mit der Verwaltung der API fort (siehe [APIs verwalten](manage_apis.html)).
