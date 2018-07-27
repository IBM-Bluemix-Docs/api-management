---

copyright:
  years: 2017,2018
lastupdated: "2018-03-28"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# APIs verwalten
{: #manage_apis}

Wenn die API integriert wurde und somit vom API-Managementsystem verwaltet und überwacht wird, können die API-Einstellungen angezeigt und geändert werden. Wenn die API noch nicht integriert wurde, müssen Sie die Integration mithilfe der im Abschnitt [APIs aus {{site.data.keyword.openwhisk_short}}-Aktionen erstellen](manage_openwhisk_apis.html) beschriebenen Prozedur vornehmen oder [API-verwaltete Endpunkte aktivieren](manage_cf_apis.html). 

Führen Sie die folgenden Schritte aus, um die Einstellungen für Ihre API zu verwalten:

Wenn Sie eine neue API erstellt haben und diese in der Schnittstelle bereits geöffnet ist, können Sie die ersten drei Schritte überspringen.

1. Wählen Sie die API aus, die Sie im {{site.data.keyword.Bluemix}}-Dashboard verwalten möchten, oder indem Sie im Dashboard für den {{site.data.keyword.openwhisk_short}}-Service eine Aktion auswählen, sofern die Informationen für die API noch nicht angezeigt werden.
2. Klicken Sie auf **API-Management** in der Navigation oder wählen Sie die Registerkarte **APIs** aus, sofern es eine {{site.data.keyword.openwhisk_short}}-Aktion ist.
3. Wählen Sie gegebenenfalls die API aus, die verwaltet werden soll. Nachdem eine Verbindung hergestellt wurde, können die folgenden Optionen angezeigt und aktualisiert werden:
    * Zusammenfassung
    * Definition
    * Gemeinsame Nutzung
    * API-Explorer
4. Wählen Sie den Schieberegler für die Bereitstellung verwalteter APIs aus, um die API zu aktivieren und verfügbar zu machen. Hinweis: Einige Einstellungen können nicht festgelegt werden, wenn die API nicht bereitgestellt wurde.  

## Zusammenfassung der Einstellungen für APIs
{: #overview_api}

Die Registerkarte 'Zusammenfassung' ist bei Auswahl einer API standardmäßig ausgewählt und in zwei Abschnitte unterteilt:
* Eigenschaften - Im Abschnitt 'Eigenschaften' können die folgenden Informationen angezeigt werden:
    * Basisinformationen zur API
	* Sicherheitsrichtlinien
	* Informationen zur Ratenbegrenzung
    * Details zur gemeinsamen Nutzung
* Abschnitt für Analyse und Protokollierung - In diesem Abschnitt können die folgenden Statistiken angezeigt werden:
	* Anzahl der Antworten und durchschnittliche Antwortzeit im zuletzt angegebenen Zeitintervall
    * Anzahl der API-Aufrufe pro Minute im Grafikformat
    * Letzte 100 Antworten in der Tabelle 'Antwortprotokoll'
	
In der Grafik *Antworten* wird zusammenfassend dargestellt, wie viele Antworten die API empfangen hat. Ferner enthält sie eine Aufgliederung des Status der Antworten. Anhand dieser Daten Sie feststellen, ob vorwiegend Fehlerantworten empfangen werden. Eine Überzahl an Fehlerantworten kann darauf hinweisen, dass der Datenverkehr die festgelegte Begrenzung in den Rateneinstellungen übersteigt. Wenn Sie den Mauszeiger auf das Informationssymbol setzen, wird eine numerische Aufgliederung der Antworten nach Antwortcode angezeigt. Häufig vorkommende Antwortcodes:
* 200  OK
* 201  Erstellt
* 302  Gefunden
* 304  Nicht geändert
* 400  Fehlerhafte Anforderung
* 401  Nicht autorisiert
* 403  Unzulässig
* 500  Interner Serverfehler
* 503  Service nicht verfügbar

Die Tabelle 'Antwortprotokoll' enthält Details zu den letzten 100 Antworten. Wählen Sie eine Spaltenüberschrift aus, um die Informationen gemäß den Einträgen in der Spalte zu sortieren. Mithilfe von *Suchantworten* können Sie nach bestimmten Einträgen in der Tabelle 'Antwortprotokoll' suchen. Weitere Informationen zu einem Ereignis können Sie aufrufen, indem Sie das betreffende Ereignis oder **Details anzeigen** im Auswahlmenü (drei vertikale Punkte) neben dem Eintrag auswählen.


## API-Einstellungen bearbeiten
{: #settings_api}

Auf der Registerkarte **Definition** können Sie die Basisinformationen für die API aktualisieren. Dazu gehören Dokumentation, Name und Basis-URL. Im Abschnitt für Sicherheit und Ratenbegrenzung können Sie eine Aufruf- und Intervallbegrenzung festlegen, um sicherzustellen, dass nur eine bestimmte Anzahl Aufrufe pro Sekunde, Minute oder Stunde erfolgt. Ferner können Sie angeben, dass zur Erstellung von API-Aufrufen eine Authentifizierung erfolgen muss, um eine unerwünschte Verwendung Ihrer Daten zu verhindern oder Statistiken für die API zu erfassen.

Führen Sie die folgenden Schritte aus, um die Einstellungen für eine API zu ändern:

1. Klicken Sie im Dashboard für das API-Management auf die Registerkarte **Definition**.
2. Im Abschnitt für die API-Informationen können Sie der API einen Namen geben bzw. den Namen aktualisieren und eine API-Definition importieren.
3. Im Abschnitt für Sicherheit und Ratenbegrenzung können Sie die folgenden Richtlinien aktualisieren:
    * API-Schlüssel erforderlich - Gibt an, ob der API-Aufruf nur bei Angabe des richtigen API-Schlüssels verarbeitet werden kann. Bei der Standardeinstellung ist kein zusätzlicher Schlüssel erforderlich.
    * Sicherheitsmethode - Bei Auswahl der Option für den API-Schlüssel gibt diese Richtlinie an, ob für die Verarbeitung der API nur der API-Schlüssel oder der API-Schlüssel und der geheime Schlüssel erforderlich sind.
    * Position des API-Schlüssels und geheimen Schlüssels - Gibt je nach Einstellung für die Methode an, wie die API-Sicherheitsinformationen in den Aufruf einbezogen werden. Die Aufrufnamen geben an, wie die Sicherheitsinformationen identifiziert werden. Weitere Informationen zum Arbeiten mit Schlüsseln und geheimen Schlüsseln finden Sie im Abschnitt [Schlüssel und geheime Schlüssel verwalten](keys_secrets.html).
    * API-Aufrufrate begrenzen - Legt die Anzahl der API-Aufrufe fest, die in einem bestimmten Zeitintervall zulässig sind. Diese Einstellung kann pro Schlüssel festgelegt werden. Beachten Sie, dass bei der Ratenbegrenzung eine Blockmethode verwendet wird. Die Durchschnittsrate der API-Aufrufe wird für das gesamte in der Rate angegebene Zeitintervall berechnet. Wenn die Rate der API-Aufrufe in einem Intervall die Durchschnittsrate der API-Aufrufe übersteigt, können Aufrufe eine Zeit lang verweigert werden, und zwar bis zu dem in der Rate angegebene Zeitlimit.   
    * OAuth-Provider - Stellt sicher, dass Benutzer mit den korrekten Sicherheitsparametern auf die APIs zugreifen können, indem OAuth über Social Media-Anmeldeberechtigungsnachweise von Providern wie Google, Facebook, IBM App ID und GitHub umgesetzt wird.
	    **Hinweis:** Sie müssen eine vorhandene App ID-Serviceinstanz angeben, die in {{site.data.keyword.Bluemix_notm}} konfiguriert ist, um die Identifikationsdaten bereitzustellen, wenn Sie **App ID** als OAuth-Provider verwenden. Wenn Sie nicht über eine vorhandene App ID-Serviceinstanz verfügen, können Sie **Erstellen** im OAuth-Abschnitt auswählen, um eine Serviceinstanz in einem neuen Fenster zu erstellen, und dann zum API-Management zurückkehren, um die neue Serviceinstanz anzugeben. Durch die Auswahl von **Bearbeiten** können Sie auch eine ausgewählte Serviceinstanz ändern.
4. CORS aktivieren - Mit CORS (Cross-origin requests) können bestimmte Anforderungen aus einer anderen Domäne verarbeitet werden.
5. Klicken Sie auf **Speichern**.

## APIs gemeinsam nutzen
{: #share_api}

APIs können innerhalb und außerhalb der {{site.data.keyword.Bluemix_notm}}-Organisation mit anderen Benutzern gemeinsam genutzt werden. 

Im Falle der gemeinsamen Nutzung von APIs, entweder innerhalb oder außerhalb der {{site.data.keyword.Bluemix_notm}}-Organisation, können für die APIs Schlüssel und geheime Schlüssel erstellt werden. Jede verwaltete API unterstützt 5 Schlüssel, die erstellt und dieser API zugeordnet werden können. Durch Senden eines eindeutigen Schlüssels an eine Einzelperson oder ein Unternehmen können Statistiken zur Nutzung dieser API erfasst werden. Beispielsweise ist es möglich, die Anzahl der API-Aufrufe der Person oder des Unternehmens zu erfassen. Ferner können Schlüssel inaktiviert oder die Aufrufe eines Schlüssels begrenzt werden. Die kann bei der Durchführung von Tests, beim Lastausgleich, der gewinnbringenden Nutzung oder der Behebung von Sicherheitsproblemen hilfreich sein.

Bei einem *Schlüssel* handelt es sich um eine eindeutige Zeichenfolge, die Ihrer API zugeordnet ist. Sie können einer API mehrere Schlüssel zuweisen. Dies vereinfacht die Verfolgung der API-Nutzung durch die einzelnen Kunden. Beispiel: Sie ordnen einem Kunden einen Schlüssel zu und einem zweiten Kunden einen anderen Schlüssel. Sobald die Kunden die API aufrufen, geben Sie den ihnen zugewiesenen Schlüssel an. Durch Verfolgung dieses Schlüssels können Sie ermitteln, welcher Kunde die API aufgerufen hat.

Es gibt zwei Typen von Schlüsseln:

* Schlüssel zur gemeinsamen Nutzung der API mit Kunden, die über Zugriff auf Ihre {{site.data.keyword.Bluemix_notm}}-Organisation verfügen. 
* Schlüssel zur gemeinsamen Nutzung der API mit Kunden, die nicht über Zugriff auf Ihre {{site.data.keyword.Bluemix_notm}}-Organisation verfügen. 

Die unterschiedlichen Schlüsseltypen werden auf dieselbe Weise erstellt, verwaltet und gelöscht. Der einzige Unterschied besteht darin, welche Personen den Schlüssel benutzen dürfen.

Nach der Erstellung einzelner oder mehrerer Schlüssel für Ihre API können Sie die Quote der Aufrufe beschränken, die über den Schlüssel für Ihre APIs durchgeführt werden dürfen. Durch die Aktivierung des Schiebereglers **API-Aufrufquote für jeden Schlüssel separat begrenzen** auf der Registerkarte *Definition* wird die Anzahl der Aufrufe für jeden Schlüssel, den Sie erstellt haben, auf die von Ihnen definierte Quotenbegrenzung beschränkt.   

Ein *geheimer Schlüssel* ähnelt einem Schlüssel und wird zur Verwaltung des Zugriffs auf die API selbst verwendet. Ein geheimer Schlüssel ist anpassbar und kann geändert werden, ohne dass hierzu der Schlüssel geändert werden muss. Ohne das Vorhandensein eines Schlüssels kann kein geheimer Schlüssel definiert werden. Nur ein Benutzer mit dem korrekten geheimen Schlüssel kann eine neue Version der API hochladen. Sie können eine API und einen geheimen Schlüssel für Ihre API-Aufrufe anfordern oder lediglich einen Schlüssel verwenden. Geheime Schlüssel können nützlich sein, wenn Sie den geheimen Schlüssel ändern müssen, den Schlüssel jedoch beibehalten möchten. 

1. Klicken Sie im Dashboard für das API-Management auf die Registerkarte **Gemeinsame Nutzung**.
2. Wählen Sie im Bereich 'Gemeinsame Nutzung in {{site.data.keyword.Bluemix_notm}}-Organisation' die Option **Verwaltete API zugänglich machen** aus, wenn die API für andere Benutzer mit Zugriff auf Ihre {{site.data.keyword.Bluemix_notm}}-Organisation verfügbar sein soll. Diese Option muss ausgewählt werden, um einen Schlüssel zu generieren.
3. Klicken Sie auf **API-Schlüssel erstellen**, um einen eindeutigen Schlüssel für die API zu erstellen. Daraufhin wird das Dialogfenster 'API-Schlüssel erstellen' angezeigt. Der API-Schlüssel wird automatisch generiert.
4. Mit dem API-Schlüssel kann festgestellt werden, welcher Benutzer auf die API zugreift. Zu diesem Zweck wird ein eindeutiger Schlüssel an den Benutzer gesendet. Das Gateway kann feststellen, welcher Schlüssel (und Kunde) den Aufruf generiert.
5. Klicken Sie auf das **Menüsymbol** (drei vertikale Punkte) neben einem API-Schlüssel, um diesen Schlüssel zu bearbeiten oder zu löschen.

Im Abschnitt für die gemeinsame Nutzung außerhalb der {{site.data.keyword.Bluemix_notm}}-Organisation können Sie die API mit anderen Benutzern gemeinsam nutzen, die über kein {{site.data.keyword.Bluemix_notm}}-Konto verfügen. Bei dieser Methode wird ein direkter Link zum Anzeigen der Informationen zu dieser API im API-Explorer bereitgestellt. Die API enthält eine Schaltfläche zur Ausführung der API in der API-Exploreransicht. Führen Sie die folgenden Schritte aus, um einen Link für die API anzufordern:

1. Im Abschnitt für die gemeinsame Nutzung außerhalb der {{site.data.keyword.Bluemix_notm}}-Organisation, klicken Sie auf **API-Schlüssel erstellen**. Daraufhin wird das Dialogfenster 'API-Schlüssel erstellen' angezeigt.
     Beachten Sie, dass der Benutzer über einen geheimen Schlüssel verfügt, der nicht Ihrer Kontrolle unterliegt.
2. Geben Sie einen eindeutigen Namen für den API-Schlüssel an.
3. Wählen Sie **Schlüssel erstellen** aus. 
4. Senden Sie den API-Portallink an den Kunden ohne {{site.data.keyword.Bluemix_notm}}-Konto. Der API-Schlüssel und gegebenenfalls der geheime Schlüssel sind in diesem Link enthalten. Somit kann weiterhin festgestellt werden, welcher Schlüssel den Link generiert hat.
  
Der Link für die API-Dokumentation öffnet die API auf der Registerkarte **API-Explorer**.

Weitere Informationen zum Arbeiten mit Schlüsseln und geheimen Schlüsseln finden Sie im Abschnitt [Schlüssel und geheime Schlüssel verwalten](keys_secrets.html).

## Mit API-Explorer anzeigen und testen
{: #explore_api}

Wählen Sie die Registerkarte 'API-Explorer' aus, um generierte HTML aus dem Swagger-Dokument anzuzeigen. 

Der API-Explorer zeigt alle API-Aktionen sowie die Dokumentation an, die sich auf die API beziehen. Sie können die Operationen und Aktionen mit den zugehörigen Beschreibungen anzeigen und die API in der Benutzerschnittstelle testen. Ferner können Sie das Swagger-Dokument zur Wiederverwendung des Inhalts herunterladen.

Führen Sie die folgenden Schritte aus, um die API zu testen:
1. *Beispiele* ist standardmäßig ausgewählt. Es handelt sich hier um ein Codebeispiel für die ausgewählte API.
2. Ändern Sie gegebenenfalls das Beispielformat, indem Sie im Menü neben der angegebenen Sprache eine Sprache auswählen. 
3. Wählen Sie **Ausprobieren** aus.
4. Wählen Sie **Operation aufrufen** aus. 

Die Antwort auf die Anforderung wird angezeigt. 

## Angepasste Domänen
{: #custom_domains}

In bestimmten Instanzen kann der Einsatz einer angepassten Domäne (sog. Vanity Domain) anstelle der Standarddomäne des API-Gateways sinnvoll sein. Die API-Managementfunktionalität unterstützt APIs, denen eine angepasste Domäne vorgeschaltet ist, solange die Domäne in Ihrer {{site.data.keyword.Bluemix_notm}}-Umgebung registriert wurde.

Führen Sie die folgenden Schritte aus, um eine angepasste Domäne einzurichten. Wenn Sie die Schritte zur Einrichtung der Domäne bereits ausgeführt haben, dann sollten Sie die Informationen im Abschnitt [Angepasste Domäne mit APIs verwenden](manage_apis.html#custom_domains_bind) lesen.

### Konfiguration

Um einer API eine angepasste Domäne vorzuschalten, müssen Sie zuerst die Domäne in {{site.data.keyword.Bluemix_notm}} registrieren. Dieser Vorgang kann über die Managementanzeige der Organisation ausgeführt werden:

1. Wählen Sie im Organisationsselektor des {{site.data.keyword.Bluemix_notm}}-Headers die Option **Organisationen verwalten** aus.
2. Suchen Sie die gewünschte Organisation, in der die Domäne registriert werden soll, und wählen Sie dann die Option **Details anzeigen** aus.
3. Klicken Sie auf den Link **Organisation bearbeiten** neben dem Organisationsnamen.
4. Wählen Sie die Registerkarte **Domänen** aus.
5. Klicken Sie auf **Domäne hinzufügen** und geben Sie dann den Domänennamen ein.
6. Nachdem die Domäne in der Liste angezeigt wird, wählen Sie oben in der Anzeige **Speichern** aus.
7. Laden Sie ein SSL-Zertifikat für diese Domäne hoch. Hierzu können Sie das Symbol **Hochladen** neben dem Domänennamen auswählen. Sowohl das öffentliche Zertifikat als auch der entsprechende private Schlüssel sind erforderlich.  
	**Hinweis:**
	* Das API-Management-Gateway unterstützt Datenverkehr nur über das HTTPS-Protokoll, sodass ein SSL-Zertifikat angegeben werden muss.
	* {{site.data.keyword.Bluemix_notm}}-Testkonten unterliegen einer Beschränkung auf nur ein SSL-Zertifikat pro Organisation. Wenn zusätzliche Zertifikate erforderlich sind, dann müssen Sie für Ihr Konto ein Upgrade auf eine kostenpflichtige Preisstufe oder eine Abonnementpreisstufe durchführen.
	* Wenn Sie die Verwendung einzelner oder mehrerer Unterdomänen für den API-Datenverkehr planen, dann ist ein Platzhalterzertifikat oder ein Zertifikat erforderlich, das die gewünschten SANs (*Subject Alternative Names*) enthält.
8. Konfigurieren Sie die DNS-Einstellungen der Domäne. 
9. Erstellen Sie einen CNAME-Datensatz für die Domäne und wählen Sie dazu einen der folgenden sicheren Endpunkte als Ziel aus. Der ausgewählte Endpunkt ist von der Region abhängig, in der die Ziel-API gehostet wird:
	- **Vereinigte Staaten (Süden):** secure.us-south.bluemix.net.
	- **Großbritannien:** secure.eu-gb.bluemix.net.
	- **Frankfurt:** secure.eu-de.bluemix.net.
	- **Sydney:** secure.au-syd.bluemix.net.

### Angepasste Domäne mit APIs verwenden
{: #custom_domains_bind}

Nach Abschluss der Ersteinrichtung müssen Sie mindestens eine API über den Abschnitt **Definition** Ihrer API an die registrierte Domäne binden, indem Sie die folgenden Schritte ausführen:
1. Wählen Sie in *API-Basisinformationen* das Menü für die API-Domäne und anschließend eine angepasste Domäne aus den Domänen aus, die Sie in den vorherigen Schritten konfiguriert haben.

2. Optional: Geben Sie eine eindeutige Unterdomäne für diese API an.
	**Hinweis:** Zur Verwendung der Unterdomäne muss das in Schritt 7 der `Konfiguration` hochgeladene SSL-Zertifikat eine gültige Platzhalterkonfiguration enthalten *oder* jede Unterdomäne muss als SAN (Subject Alternative Name) aufgelistet werden.

3. Speichern Sie die API. Die Aktivierung der Domäneneinstellungen kann mehrere Minuten in Anspruch nehmen.

Weitere Informationen enthalten die folgenden Abschnitte:
[Domänen verwalten](../admin/manageorg.html#managedomains) und [Angepasste Domäne erstellen und verwenden](../manageapps/updapps.html#domain).
