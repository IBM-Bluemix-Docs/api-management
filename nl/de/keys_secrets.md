---

copyright:
  years: 2017
lastupdated: "2017-11-09"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Schlüssel und geheime Schlüssel verwalten
{: #keys_secrets}

Wenn Ihre APIs mithilfe des API-Managements verwaltet werden, dann können Sie Schlüssel und geheime Schlüssel verwenden, um den Zugriff auf die APIs zu steuern.

## Schlüssel und geheimen Schlüssel erstellen
{: #create_key_secret}

Führen Sie die folgenden Schritte aus, um einen Schlüssel zu Ihrer API hinzuzufügen:

1. Öffnen Sie die Cloud Foundry-Anwendung oder die OpenWhisk-API, sofern diese Komponenten noch nicht geöffnet wurden.

2. Wählen Sie im Navigationsbereich die Option *API-Management* aus.

3. Wählen Sie die Registerkarte 'Gemeinsame Nutzung & Schlüssel' aus, um auf die Schlüssel für diese Anwendung oder API zuzugreifen. *Hinweis: Die Registerkarten werden erst angezeigt, nachdem Sie die Anwendung oder API zum ersten Mal gespeichert haben.*

4. Vergewissern Sie sich, dass sich der Schieberegler **Verwaltete API zugänglich machen** in der Position *Ein* befindet. Ihre API muss zugänglich gemacht werden, bevor Sie Schlüssel zuweisen können.

5. Erstellen Sie einen Schlüssel für einen Kunden, der Zugriff auf Ihre {{site.data.keyword.Bluemix_notm}}-Organisation hat.
  1. Wählen Sie die Option **API-Schlüssel erstellen +** im Abschnitt *Gemeinsame Nutzung in {{site.data.keyword.Bluemix_notm}}-Organisation* aus. Daraufhin erstellt das System automatisch einen Schlüssel und einen geheimen Schlüssel und trägt diese in die entsprechenden Felder ein. Sie können den Schlüssel bzw. den geheimen Schlüssel für diesen Schlüsseltyp nicht aktualisieren. 
  2. Geben Sie einen Namen für Ihren Schlüssel und den geheimen Schlüssel ein, um die Identifikation zu vereinfachen. Geben Sie z. B. den Namen des Kunden ein, der den (geheimen) Schlüssel verwenden wird.
  3. Wählen Sie **Speichern** aus, um den neuen Schlüssel zu speichern.
  4. Sie können die Schritte *a* bis *c* bei Bedarf für weitere Schlüssel wiederholen. Sie können maximal fünf Schlüssel pro API in diesem Abschnitt definieren.

6. Erstellen Sie einen Schlüssel für einen Kunden, der nicht Mitglied Ihrer {{site.data.keyword.Bluemix_notm}}-Organisation ist.
  1. Wählen Sie die Option **API-Schlüssel erstellen +** im Abschnitt *Gemeinsame Nutzung außerhalb der {{site.data.keyword.Bluemix_notm}}-Organisation* aus. Daraufhin erstellt das System automatisch einen Schlüssel und trägt diesen in das entsprechende Feld ein. Für diesen Schlüsseltyp wird zu Beginn kein geheimer Schlüssel angezeigt. Sie können den Schlüssel nicht aktualisieren. 
  2. Geben Sie einen Namen für Ihren Schlüssel ein, um die Identifikation zu vereinfachen. Geben Sie z. B. den Namen des Kunden ein, der den (geheimen) Schlüssel verwenden wird.
  3. Optional: Wenn Sie einen geheimen Schlüssel zum Schlüssel hinzufügen möchten, dann wählen Sie für den Schlüssel, zu dem der geheime Schlüssel hinzugefügt werden soll, die Option **API-Portallink** und anschließend **Geheimen Schlüssel für API festlegen** aus.
  4. Wählen Sie **Speichern** aus, um den neuen Schlüssel zu speichern.
  5. Sie können die Schritte *a* bis *d* bei Bedarf für weitere Schlüssel wiederholen. Sie können maximal fünf Schlüssel pro API in diesem Abschnitt definieren.
Ihre Schlüssel werden für die API aufgelistet, sobald die Registerkarte 'Gemeinsame Nutzung & Schlüssel' ausgewählt wird.

## Schlüssel und geheimen Schlüssel in API-Aufruf angeben
{: #spec_key_secret}

Ihre Kunden können Ihre API nur dann aufrufen, wenn sie den korrekten Schlüssel und/oder den korrekten geheimen Schlüssel im Header des Aufrufs angeben. Zum Aufrufen der API müssen Sie den Schlüssel und den geheimen Schlüssel wie im folgenden Beispiel dargestellt im API-Aufruf angeben:
```
curl --request PUT \
  --url https://appidtest.mybluemix.net/ \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --header 'x-ibm-client-secret: add_secret_here' \
  --data '{"id":999999999999999}'
```
{: codeblock}
Hierbei wird *add_secret_here* durch den geheimen Schlüssel für den korrekten Schlüssel ersetzt. 

## API-Schlüssel löschen
{: #delete_key}

Möglicherweise tritt eine Situation ein, in der Sie einen Schlüssel entfernen möchten. Möglicherweise erstellt ein Kunde, der Ihre API bislang verwendet hat, nun eine eigene API und benötigt Ihre API deshalb nicht mehr. Um sicherzustellen, dass keiner der Kunden mehr Ihre API verwendet, können Sie den Schlüssel löschen. Führen Sie die folgenden Schritte aus, um einen Schlüssel aus dem Service zu löschen:

1. Öffnen Sie die Cloud Foundry-Anwendung oder die OpenWhisk-API, sofern diese Komponenten noch nicht geöffnet wurden.

2. Wählen Sie im Navigationsbereich die Option *API-Management* aus.

3. Wählen Sie die Registerkarte *Gemeinsame Nutzung & Schlüssel* aus.

4. Suchen Sie den Schlüssel, der gelöscht werden soll. Tipp: Hier kann es hilfreich sein, die Schlüssel so zu benennen, dass sie auf einfache Weise identifiziert werden können.

5. Wählen Sie das Optionssymbol aus, das aus drei vertikalen Punkten besteht. Es befindet sich neben dem Schlüssel, den Sie löschen möchten. 

6. Wählen Sie **Schlüssel löschen** aus.

7. Bestätigen Sie die Löschung, um den Schlüssel zu entfernen.
