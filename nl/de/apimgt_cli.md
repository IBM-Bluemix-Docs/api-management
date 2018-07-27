---



copyright:

  years: 2017
lastupdated: "2017-06-26"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

# Bluemix-API-Managementbefehle
{: #apimgt_cli}

Version: 1.0.0

Sie können das Plug-in für die Befehlszeilenschnittstelle (CLI = Command-Line Interface) der {{site.data.keyword.Bluemix_notm}}-API-Managementbefehle installieren, um allgemeine Managementaktionen für Ihre APIs mithilfe des Scriptings auszuführen. Die folgenden Informationen enthalten eine Auflistung der Befehle, die im CLI-Plug-in für das API-Management enthalten sind. Diese Angaben umfassen die Namen, Optionen, die Syntax, die Voraussetzungen und Beschreibungen sowie Beispiele zu den jeweiligen Befehlen.
{:shortdesc}

**Hinweis:** Unter den **Voraussetzungen** sind die Aktionen aufgelistet, die ausgeführt werden müssen, bevor der jeweilige Befehl verwendet werden kann. Für Befehle, für die keine Voraussetzungen bestehen, ist **Ohne** angegeben. Andernfalls können die Voraussetzungen die folgenden Aktionen umfassen:

**Hinweis:** Sie können das Kurzformat der Bluemix-Befehle verwenden. Der Befehl `bx apim` ist beispielsweise die Kurzform des Befehls `bluemix apim`.

Benutzen Sie die Indizes in der folgenden Tabelle, um auf die häufig verwendeten API-Managementbefehle zu verweisen.

<table summary="API-Managementbefehle.">
<caption>Tabelle 1. API-Managementbefehle</caption>
 <thead>
 <th colspan="5">API-Managementbefehle</th>
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
 
  
## API-Management - Hilfe
{: #apim_help}
Anzeigen der erweiterten Hilfe für die integrierten Befehle der ersten Ebene und die unterstützten Namensbereiche der Befehlszeilenschnittstelle (CLI = Command-Line Interface) für das API-Management oder die Hilfe für einen bestimmten integrierten Befehl oder Namensbereich.

### Syntax

```
bluemix apim help <object-action>
```
{: codeblock}

### Befehlsoptionen

   <dl>
   <dt>object-action (optional)</dt>
   <dd>Der Befehl, für den die Hilfe angezeigt wird. Erfolgt hier keine Angabe, dann wird die erweiterte Hilfe für die API-Management-CLI angezeigt.</dd>
   </dl>

### Beispiele

Anzeigen der erweiterten Hilfe für die API-Management-CLI:

```
bluemix apim help
```

Anzeigen der Hilfe für den Befehl `api-create`:

```
bluemix apim help api-create
```



## bluemix apim api
{: #apim_api}
Anzeigen der Eigenschaften einer verwalteten API.

### Syntax
```
bluemix apim api --name <API_NAME> [--swagger]
```
{: codeblock}

### Erforderliches Flag
   <dl>
   <dt>--name</dt>
   <dd>Gibt den Namen der verwalteten API an.</dd>
   </dl>


### Befehlsoptionen
   <dl>
   <dt>--swagger</dt>
   <dd>Zeigt die Informationen aus dem Open API-Definitionsdokument in der Ausgabe an.</dd>
   </dl>

### Ausgabe

Der Befehl gibt eine Tabelle aus, in der die folgenden Informationen zu der angegebenen API aufgelistet werden:

   <dl>
     <dt>Name</dt>
	 <dd>Der Name der API.</dd>
	 <dt>Typ</dt>
	 <dd>Der Typ der API. Gültige Einträge sind <em>whisk</em>, <em>cf-apps</em> und <em>user-defined</em>.</dd>
	 <dt>Verwaltet</dt>
	 <dd>Ist der Wert 'true', dann wurde der Endpunkt erkannt, jedoch nicht im Gateway zugänglich gemacht.</dd>
	 <dt>Zugänglich gemacht</dt>
	 <dd>Gibt an, ob sich die API im Gateway im Live-Modus befindet (<em>true</em>) oder nicht (<em>false</em>).
	 <dt>Gemeinsam genutzt</dt>
	 <dd>Gibt an, ob die API außerhalb Ihrer Bluemix-Organisation gemeinsam genutzt wird (<em>true</em>) oder nicht (<em>false</em>).</dd>
	 <dt>Verwaltete URL</dt>
	 <dd>Gibt den Standort der gemeinsam genutzten Version der API an.</dd>
   </dl>

   
### Beispiele

Anzeigen der Eigenschaften der API mit dem Namen 'cloudfound1':

```
bluemix apim api cloudfound1
```

Anzeigen der Eigenschaften und Definitionsdateiinhalte für die API mit dem Namen 'api2':

```
bluemix apim api api2 --swagger
```


## bluemix apim apis
{: #apim_apis}


Auflisten der APIs, die auf dem ermittelten Endpunktserver verfügbar sind und dort identifiziert wurden.

### Syntax
```
bluemix apim apis [--api-provider <API_PROVIDER>][--exposed][--shared]
```
{: codeblock}

### Befehlsoptionen

Hinweis: Wurden keine Optionen angegeben, dann werden die Informationen für alle APIs zurückgegeben.
   <dl>
   <dt>--api-provider </dt>
   <dd>Es werden nur die Typen von APIs zurückgegeben, die hier angegeben werden. Gültige Optionen sind <em>whisk</em> für OpenWhisk-APIs, <em>cf-apps</em> für Cloud Foundry-App-APIs und <em>user-defined</em> für APIs, die weder OpenWhisk noch Cloud Foundry zugeordnet sind.</dd>
   <dt>--exposed</dt>
   <dd>Gibt nur APIs zurück, die zugänglich gemacht wurden.</dd>
   <dt>--shared</dt>
   <dd>Gibt nur APIs zurück, die außerhalb Ihrer {{site.data.keyword.Bluemix_notm}}-Organisation gemeinsam genutzt werden.</dd>
   </dl>

### Ausgabe

Der Befehl gibt eine Tabelle aus, in der die folgenden Informationen zu den angegebenen APIs aufgelistet werden:

   <dl>
     <dt>Name</dt>
	 <dd>Der Name der API.</dd>
	 <dt>Typ</dt>
	 <dd>Der Typ der API. Gültige Einträge sind <em>whisk</em>, <em>cf-apps</em> und <em>user-defined</em>.</dd>
	 <dt>Verwaltet</dt>
	 <dd>Ist der Wert 'true', dann wurde der Endpunkt erkannt, jedoch nicht im Gateway zugänglich gemacht.</dd>
	 <dt>Zugänglich gemacht</dt>
	 <dd>Gibt an, ob sich die API im Gateway im Live-Modus befindet (<em>true</em>) oder nicht (<em>false</em>).
	 <dt>Gemeinsam genutzt</dt>
	 <dd>Gibt an, ob die API außerhalb Ihrer Bluemix-Organisation gemeinsam genutzt wird (<em>true</em>) oder nicht (<em>false</em>).</dd>
	 <dt>Verwaltete URL</dt>
	 <dd>Gibt den Standort der gemeinsam genutzten Version der API an, wenn die API zugänglich gemacht wurde. Der Wert lautet <em>nicht definiert</em>, wenn die API nicht zugänglich gemacht wird.</dd>
   </dl>


### Beispiele

Zurückgeben aller APIs, die auf dem Endpunktmanager zur Verfügung stehen:

```
bluemix apim apis 
```

Zurückgeben aller OpenWhisk-APIs, die zur Verfügung stehen:

```
bluemix apim apis --api-provider whisk
```

## bluemix apim api-create
{: #apim_api-create}


Ändert eine vorhandene nicht verwaltete API in eine verwaltete API, indem die zugehörige Swagger-Datei importiert wird.

### Syntax

```
bluemix apim api-create --name <API_NAME> --file <PATH_TO_OPEN_API_DEFINITION_FILE> --provider cf-apps [--expose]
```
{: codeblock}

### Erforderliche Flags

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Gibt den Namen der API an, die verwaltet werden soll.</dd>
   <dt>--file</dt>
   <dd>Gibt den Pfad zur Open API-Definitionsdatei an, die im YAML- oder JSON-Format vorliegt.</dd>
   <dt>--provider</dt>
   <dd>Gibt den Typ der API an, die von Ihnen erstellt wird. Hinweis: Der einzige gültige Eintrag ist <em>cf-apps</em>.
   </dl>

### Befehlsoption

   <dl>
   <dt>--expose</dt>
   <dd>Automatisches Bereitstellen des Endpunkts nach seiner Erstellung.</dd>
   </dl>

### Ausgabe

Der Befehl gibt die folgenden Informationen aus:
* Erfolgreich erstellt
* Fehler (mit Fehlerbeschreibung)

### Beispiele

Verwalten einer Cloud Foundry-API mit dem Namen 'apinumber1', die über eine YAML-Definitionsdatei mit dem Namen 'reservations1' verfügt:

```
bluemix apim api-create --name apinumber1 --file ~/dev/apis/reservations1.yaml --provider cf-apps
```

Verwalten einer Cloud Foundry-App mit dem Namen 'cfapi', die über eine JSON-Definitionsdatei mit dem Namen 'definition1' verfügt:

```
bluemix apim api-create --name cfapi --file ~/dev/apis/definition1.json --provider cf-apps
```

## bluemix apim api-delete
{: #apim_api-delete}

Entfernen einer verwalteten API aus der Datenbank.

### Syntax

```
bluemix apim api-delete --name <API_NAME> --confirm
```
{: codeblock}

### Erforderliche Flags

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Gibt den Namen der API an, die gelöscht werden soll. **Wichtig:** Beim Löschen einer Cloud Foundry-API wird die API aus dem verwalteten Status entfernt, die Cloud Foundry-App wird jedoch nicht gelöscht. Beim Löschen einer OpenWhisk-API wird die gesamte API gelöscht, die nach der Löschung erneut erstellt werden muss.</dd>
   <dt>--confirm</dt>
   <dd>Bestätigt, dass der Befehl ausgeführt werden soll, ohne eine Bestätigungsaufforderung anzugeben.</dd>
   </dl>


### Ausgabe

Der Befehl gibt die folgenden Informationen aus:
* Erfolgreich gelöscht
* Fehler (mit Fehlerbeschreibung)

### Beispiele

Löschen der Cloud Foundry-API 'cloudapi1':

```
bluemix apim api-delete --name cloudapi1 --confirm
```


## bluemix apim api-expose
{: #apim_api-expose}

Sichtbarmachen einer verwalteten API für andere Benutzer in meiner {{site.data.keyword.Bluemix_notm}}-Organisation.

### Syntax
```
bluemix apim api-expose --name <API_NAME>
```
{: codeblock}

### Erforderliches Flag

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Gibt den Namen der API an, die zugänglich gemacht werden soll.</dd>
   </dl>

### Ausgabe

Der Befehl gibt die folgenden Informationen aus:
* Erfolgreich zugänglich gemacht
* Fehler (mit Fehlerbeschreibung)

### Beispiel

Zugänglichmachung einer Cloud Foundry-API mit dem Namen 'cloudfound1' für meine {{site.data.keyword.Bluemix_notm}}-Organisation:

```
bluemix apim api-expose --name cloudfound1
```


## bluemix apim api-share
{: #apim_api-share}


Sichtbarmachen einer verwalteten API für andere Benutzer außerhalb meiner {{site.data.keyword.Bluemix_notm}}-Organisation.

### Syntax
```
bluemix apim api-share --name <API_NAME>
```
{: codeblock}

### Erforderliches Flag

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Gibt den Namen der API an, die gemeinsam genutzt werden soll.</dd>
   </dl>

### Ausgabe

Der Befehl gibt die folgenden Informationen aus:
* Erfolgreich gemeinsam genutzt
* Fehler (mit Fehlerbeschreibung)

### Beispiel

Gemeinsames Nutzen einer Cloud Foundry-API mit dem Namen 'cloudfound1' außerhalb meiner {{site.data.keyword.Bluemix_notm}}-Organisation:
```
bluemix apim api-share --name cloudfound1
```


## bluemix apim api-unexpose
{: #apim_api-unexpose}


Ausblenden einer verwalteten API, die für andere Benutzer in Ihrer {{site.data.keyword.Bluemix_notm}}-Organisation sichtbar ist.

### Syntax
```
bluemix apim api-unexpose --name <API_NAME>
```
{: codeblock}

### Erforderliches Flag

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Gibt den Namen der API an, deren Sichtbarkeit für andere Benutzer in Ihrer {{site.data.keyword.Bluemix_notm}}-Organisation aufgehoben werden soll.</dd>
   </dl>

### Ausgabe

Der Befehl gibt die folgenden Informationen aus:
* Zugänglichkeit erfolgreich aufgehoben
* Fehler (mit Fehlerbeschreibung)

### Beispiel

Aufheben der Sichtbarkeit einer OpenWhisk-API mit dem Namen 'openwhisk1' für andere Mitglieder meiner {{site.data.keyword.Bluemix_notm}}-Organisation:

```
bluemix apim api-unexpose --name openwhisk1
```


## bluemix apim api-unshare
{: #apim_api-unshare}


Hebt die Sichtbarkeit einer verwalteten API, die für andere Benutzer außerhalb meiner {{site.data.keyword.Bluemix_notm}}-Organisation sichtbar ist, auf.

### Syntax
```
bluemix apim api-unshare --name <API_NAME>
```
{: codeblock}

<strong>Erforderliches Flag</strong>:

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Gibt den Namen der API an, deren gemeinsame Nutzung beendet werden soll.</dd>
   </dl>

### Ausgabe

Der Befehl gibt die folgenden Informationen aus:
* Gemeinsame Nutzung erfolgreich beendet
* Fehler (mit Fehlerbeschreibung)

### Beispiel

Beenden der gemeinsamen Nutzung einer Cloud Foundry-API mit dem Namen 'cloudfound1' außerhalb meiner {{site.data.keyword.Bluemix_notm}}-Organisation:

```
bluemix apim api-unshare --name cloudfound1
```



## bluemix apim api-update
{: #apim_api-update}


Aktualisiert die Einstellungen einer verwalteten API, indem die zugehörige Definitionsdatei ersetzt wird. Wichtig: Hierbei handelt es sich um eine vollständige Ersetzung der vorhandenen Definitionen in der API durch die Definitionen in der neuen Datei. Leere oder fehlende Einträge in der neuen Datei, die auch in der vorhandenen Datei enthalten sind, werden aus der Definition entfernt.

### Syntax
```
bluemix apim api-update --name <API_NAME> --file <NEW_OPEN_API_DEFINITION_FILE>
```
{: codeblock}

### Erforderliche Flags

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Gibt den Namen der API an, die aktualisiert werden soll.</dd>
   <dt>--file</dt>
   <dd>Gibt den Pfad zur Open API-Ersatzdefinitionsdatei an, die im YAML- oder JSON-Format vorliegt.</dd>
   </dl>

### Ausgabe

Der Befehl gibt die folgenden Informationen aus:
* Erfolgreich aktualisiert
* Fehler (mit Fehlerbeschreibung)


### Beispiel

Aktualisieren einer OpenWhisk-API mit dem Namen 'whiskapi1' mit einer Definitionsdatei mit dem Namen 'definition1.json':

```
bluemix apim api-update --name whiskapi1 --filePath ~/path/definitions/definition1.json
```


## bluemix apim keys
{: #apim_api-keys}


Zeigt die Eigenschaften der Schlüssel an, die einer verwalteten API zugeordnet sind.

### Syntax
```
bluemix apim api-keys --name <API_NAME> --bluemix|--external
```
{: codeblock}

### Erforderliche Flags

   <dl>
   <dt>--name <i>API_NAME</i></dt>
   <dd>Gibt den Namen der API an, die zugänglich gemacht werden soll.</dd>
   <dt>--bluemix</dt>
   <dd>Listet die {{site.data.keyword.Bluemix_notm}}-API-Schlüssel für die angegebene API auf.</dd>
   <dt>--external</dt>
   <dd>Listet die externen API-Schlüssel für die angegebene API auf.</dd>
   </dl>

### Ausgabe

Der Befehl gibt eine Tabelle aus, in der die folgenden Informationen zu den angegebenen APIs aufgelistet werden:


   <dl>
     <dt>Schlüsselname</dt>
	 <dd>Der Name des API-Schlüssels.</dd>
	 <dt>Schlüsseltyp</dt>
	 <dd>Der Typ des API-Schlüssels. Die gültigen Einträge sind <em>bluemix</em> und <em>external</em>.</dd>
	 <dt>Client-ID</dt>
	 <dd>Der Name des Clients, der im Schlüssel angegeben ist.</dd>
	 <dt>Angegebener geheimer Schlüssel</dt>
	 <dd>Gibt an, ob der geheime API-Schlüssel für die API angegeben wurde. Die gültigen Werte sind <em>true</em> (wenn ein geheimer Schlüssel vorhanden ist) und <em>false</em> (wenn kein gemeiner Schlüssel vorhanden ist.
   </dl>


### Beispiele

Zurückgeben aller externen Schlüssel, die der API mit dem Namen 'cloudfound1' zugeordnet sind.

```
bluemix apim --name cloudfound1 --external
```

Zurückgeben der Schlüssel, die Personen in meiner {{site.data.keyword.Bluemix_notm}}-Organisation das Anzeigen meiner API mit dem Namen 'myapi1' erlauben.

```
bluemix apim --name myapi1 --bluemix 
```
 
