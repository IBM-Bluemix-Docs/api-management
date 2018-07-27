---



copyright:

  years: 2017
lastupdated: "2017-06-26"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

# Commandes de gestion des API Bluemix
{: #apimgt_cli}

Version : 1.0.0

Vous pouvez installer le plug-in d'interface de ligne de commande de gestion des API {{site.data.keyword.Bluemix_notm}} pour effectuer des actions de gestion courante dans vos API en utilisant des scripts. Les informations suivantes répertorient les commandes incluses dans le plug-in d'interface de ligne de commande de gestion des API, dont les noms, les options, l'utilisation, les prérequis, les descriptions et les exemples.
{:shortdesc}

**Remarque :** la zone **Prérequis** indique les actions qui sont requises avant d'utiliser la commande. Les commandes pour lesquelles aucune action n'est requise indiquent **Aucun**. Sinon, les prérequis peuvent inclure une ou plusieurs des actions suivantes :

**Remarque :** vous pouvez utiliser le format abrégé des commandes Bluemix ; ainsi, `bx apim` est la forme abrégée de `bluemix apim`.

Utilisez les index du tableau suivant pour vous référer aux commandes de gestion des API fréquemment utilisées.

<table summary="Commandes de gestion des API.">
<caption>Tableau 1. Commandes de gestion des API</caption>
 <thead>
 <th colspan="5">Commandes de gestion des API</th>
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
 
  
## Aide relative à la gestion des API
{: #apim_help}
Affiche l'aide générale pour les commandes intégrées de premier niveau et les espaces de nom pris en charge de l'interface de ligne de commande, ou l'aide d'une commande intégrée ou d'un espace de nom spécifique.

### Syntaxe

```
bluemix apim help <object-action>
```
{: codeblock}

### Options de commande

   <dl>
   <dt>object-action (facultatif)</dt>
   <dd>Commande pour laquelle l'aide est affichée. Si rien n'est spécifié, l'aide générale pour l'interface de ligne de commande de gestion des API s'affiche.</dd>
   </dl>

### Exemples

Affiche l'aide générale pour l'interface de ligne de commande de gestion des API :

```
bluemix apim help
```

Affiche l'aide pour la commande `api-create` :

```
bluemix apim help api-create
```



## bluemix apim api
{: #apim_api}
Affiche les propriétés d'une API gérée.

### Syntaxe
```
bluemix apim api --name <API_NAME> [--swagger]
```
{: codeblock}

### Indicateur requis
   <dl>
   <dt>--name</dt>
   <dd>Spécifie le nom de l'API gérée</dd>
   </dl>


### Options de commande
   <dl>
   <dt>--swagger</dt>
   <dd>Affiche les informations du document de définition Open API dans la sortie</dd>
   </dl>

### Sortie

La commande génère un tableau qui répertorie les informations ci-après relatives à l'API spécifiée :

   <dl>
     <dt>Nom</dt>
	 <dd>Nom de l'API.</dd>
	 <dt>Type</dt>
	 <dd>Type de l'API. Les entrées valides sont <em>whisk</em>, <em>cf-apps</em> ou <em>user-defined</em></dd>
	 <dt>Gérée</dt>
	 <dd>Si la valeur est true, indique que le noeud final est reconnu mais non exposé sur la passerelle.</dd>
	 <dt>Exposée</dt>
	 <dd>Indique si l'API est opérationnelle sur la passerelle (<em>true</em>) ou non (<em>false</em>).
	 <dt>Partagée</dt>
	 <dd>Indique si l'API est partagée en dehors de votre organisation Bluemix (<em>true</em>) ou non (<em>true</em>).</dd>
	 <dt>URL gérée</dt>
	 <dd>Spécifie l'emplacement de la version partagée de l'API.</dd>
   </dl>

   
### Exemples

Affiche les propriétés de l'API intitulée cloudfound1 :

```
bluemix apim api cloudfound1
```

Affiche les propriétés et le contenu du fichier de définition pour l'API intitulée api2 :

```
bluemix apim api api2 --swagger
```


## bluemix apim apis
{: #apim_apis}


Répertorie les API qui sont disponibles et identifiées sur le serveur de noeud final repéré.

### Syntaxe
```
bluemix apim apis [--api-provider <API_PROVIDER>][--exposed][--shared]
```
{: codeblock}

### Options de commande

Remarque : si aucune option n'est spécifiée, les informations relatives à toutes les API sont retournées.
   <dl>
   <dt>--api-provider </dt>
   <dd>Renvoie uniquement les types des API que vous avez spécifiées ici. Les options valides sont <em>whisk</em> pour les API Openwhisk, <em>cf-apps</em> pour les API d'application Cloud Foundry et <em>user-defined</em> pour les API qui ne sont pas associées à Openwhisk ou Cloud Foundry.</dd>
   <dt>--exposed</dt>
   <dd>Ne retourne que les API qui sont exposées.</dd>
   <dt>--shared</dt>
   <dd>Ne retourne que les API qui sont partagées en dehors de votre organisation {{site.data.keyword.Bluemix_notm}}.</dd>
   </dl>

### Sortie

La commande génère un tableau qui répertorie les informations ci-après relatives aux API spécifiées :

   <dl>
     <dt>Nom</dt>
	 <dd>Nom de l'API.</dd>
	 <dt>Type</dt>
	 <dd>Type de l'API. Les entrées valides sont <em>whisk</em>, <em>cf-apps</em> ou <em>user-defined</em></dd>
	 <dt>Gérée</dt>
	 <dd>Si la valeur est true, indique que le noeud final est reconnu mais non exposé sur la passerelle.</dd>
	 <dt>Exposée</dt>
	 <dd>Indique si l'API est opérationnelle sur la passerelle (<em>true</em>) ou non (<em>false</em>).
	 <dt>Partagée</dt>
	 <dd>Indique si l'API est partagée en dehors de votre organisation Bluemix (<em>true</em>) ou non (<em>false</em>).</dd>
	 <dt>URL gérée</dt>
	 <dd>Spécifie l'emplacement de la version partagée de l'API si cette dernière est exposée. La valeur est <em>undefined</em> quand l'API n'est pas exposée. </dd>
   </dl>


### Exemples

Retourne toutes les API qui sont disponibles sur le gestionnaire des noeuds finaux :

```
bluemix apim apis 
```

Retourne toutes les API OpenWhisk qui sont disponibles :

```
bluemix apim apis --api-provider whisk
```

## bluemix apim api-create
{: #apim_api-create}


Transforme une API non gérée existante en une API gérée en important son fichier Swagger.

### Syntaxe

```
bluemix apim api-create --name <API_NAME> --file <PATH_TO_OPEN_API_DEFINITION_FILE> --provider cf-apps [--expose]
```
{: codeblock}

### Indicateurs requis

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Spécifie le nom de l'API que vous voulez gérer.</dd>
   <dt>--file</dt>
   <dd>Fournit le chemin d'accès au fichier de définition Open API, qui est au format YAML ou JSON.</dd>
   <dt>--provider</dt>
   <dd>Spécifie le type de l'API que vous créez. Remarque : la seule entrée valide est <em>cf-apps</em>.
   </dl>

### Option de commande

   <dl>
   <dt>--expose</dt>
   <dd>Expose automatiquement le noeud final après l'avoir créé.</dd>
   </dl>

### Sortie

La commande génère les informations suivantes, ou des informations similaires :
* Création effectuée
* Erreur (avec description de l'erreur)

### Exemples

Gère une API Cloud Foundry nommée apinumber1 disposant d'un fichier de définition yaml intitulé reservations1 :

```
bluemix apim api-create --name apinumber1 --file ~/dev/apis/reservations1.yaml --provider cf-apps
```

Gère une application Cloud Foundry nommée cfapi disposant d'un fichier de définition json intitulé definition1 :

```
bluemix apim api-create --name cfapi --file ~/dev/apis/definition1.json --provider cf-apps
```

## bluemix apim api-delete
{: #apim_api-delete}

Retire une API gérée de la base de données.

### Syntaxe

```
bluemix apim api-delete --name <API_NAME> --confirm
```
{: codeblock}

### Indicateurs requis

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Spécifie le nom de l'API que vous voulez supprimer. **Important :** la suppression d'une API Cloud Foundry retire l'API de l'état géré mais l'application Cloud Foundry n'est pas supprimée. La suppression d'une API OpenWhisk supprime l'intégralité de l'API et cette dernière doit être recréée après sa suppression.</dd>
   <dt>--confirm</dt>
   <dd>Confirme que la commande doit être exécutée sans fournir d'invite de confirmation.</dd>
   </dl>


### Sortie

La commande génère les informations suivantes, ou des informations similaires :
* Suppression terminée
* Erreur (avec description de l'erreur)

### Exemples

Supprime l'API Cloud Foundry cloudapi1 :

```
bluemix apim api-delete --name cloudapi1 --confirm
```


## bluemix apim api-expose
{: #apim_api-expose}

Rend une API gérée visible aux autres personnes qui se trouvent à l'intérieur de mon organisation {{site.data.keyword.Bluemix_notm}}.

### Syntaxe
```
bluemix apim api-expose --name <API_NAME>
```
{: codeblock}

### Indicateur requis

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Spécifie le nom de l'API que vous voulez exposer.</dd>
   </dl>

### Sortie

La commande génère les informations suivantes, ou des informations similaires :
* Exposition effectuée
* Erreur (avec description de l'erreur)

### Exemple

Expose une API Cloud Foundry nommée cloudfound1 avec mon organisation {{site.data.keyword.Bluemix_notm}} :

```
bluemix apim api-expose --name cloudfound1
```


## bluemix apim api-share
{: #apim_api-share}


Rend une API gérée visible aux autres personnes qui se trouvent à l'extérieur de mon organisation {{site.data.keyword.Bluemix_notm}}.

### Syntaxe
```
bluemix apim api-share --name <API_NAME>
```
{: codeblock}

### Indicateur requis

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Spécifie le nom de l'API que vous voulez partager.</dd>
   </dl>

### Sortie

La commande génère les informations suivantes, ou des informations similaires :
* Partage effectué
* Erreur (avec description de l'erreur)

### Exemple

Partage une API Cloud Foundry nommée cloudfound1 à l'extérieur de mon organisation {{site.data.keyword.Bluemix_notm}} :
```
bluemix apim api-share --name cloudfound1
```


## bluemix apim api-unexpose
{: #apim_api-unexpose}


Rend invisible une API gérée, jusque là visible aux autres personnes qui se trouvent à l'intérieur de mon organisation {{site.data.keyword.Bluemix_notm}}.

### Syntaxe
```
bluemix apim api-unexpose --name <API_NAME>
```
{: codeblock}

### Indicateur requis

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Spécifie le nom de l'API dont vous voulez retirer la visibilité aux autres personnes qui se trouvent à l'intérieur de mon organisation {{site.data.keyword.Bluemix_notm}}.</dd>
   </dl>

### Sortie

La commande génère les informations suivantes, ou des informations similaires :
* Visibilité retirée
* Erreur (avec description de l'erreur)

### Exemple

Retire une API OpenWhisk API intitulée openwhisk1 d'une vue accessible aux autres membres de mon organisation {{site.data.keyword.Bluemix_notm}} :

```
bluemix apim api-unexpose --name openwhisk1
```


## bluemix apim api-unshare
{: #apim_api-unshare}


Retire la visibilité d'une API gérée, jusque là visible aux autres personnes qui se trouvent à l'extérieur de mon organisation {{site.data.keyword.Bluemix_notm}}.

### Syntaxe
```
bluemix apim api-unshare --name <API_NAME>
```
{: codeblock}

<strong>Indicateur requis</strong>:

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Spécifie le nom de l'API dont vous voulez arrêter le partage.</dd>
   </dl>

### Sortie

La commande génère les informations suivantes, ou des informations similaires :
* Partage arrêté
* Erreur (avec description de l'erreur)

### Exemple

Arrête le partage d'une API Cloud Foundry nommée cloudfound1 à l'extérieur de mon organisation {{site.data.keyword.Bluemix_notm}} :

```
bluemix apim api-unshare --name cloudfound1
```



## bluemix apim api-update
{: #apim_api-update}


Met à jour les paramètres d'une API gérée en remplaçant son fichier de définition. Important : il s'agit d'un remplacement complet des définitions existantes dans l'API par les définitions du nouveau fichier. Toute entrée vide ou manquante dans le nouveau fichier qui se trouve dans le fichier existant est retirée de la définition.

### Syntaxe
```
bluemix apim api-update --name <API_NAME> --file <NEW_OPEN_API_DEFINITION_FILE>
```
{: codeblock}

### Indicateurs requis

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Spécifie le nom de l'API que vous voulez mettre à jour.</dd>
   <dt>--file</dt>
   <dd>Fournit le chemin d'accès au fichier de définition Open API de remplacement, qui est au format YAML ou JSON.</dd>
   </dl>

### Sortie

La commande génère les informations suivantes, ou des informations similaires :
* Mise à jour effectuée
* Erreur (avec description de l'erreur)


### Exemple

Met à jour une API OpenWhisk appelée whiskapi1 avec un fichier de définition nommé definition1.json :

```
bluemix apim api-update --name whiskapi1 --filePath ~/path/definitions/definition1.json
```


## bluemix apim keys
{: #apim_api-keys}


Affiche les propriétés des clés qui sont associées à une API gérée.

### Syntaxe
```
bluemix apim api-keys --name <API_NAME> --bluemix|--external
```
{: codeblock}

### Indicateurs requis

   <dl>
   <dt>--name <i>API_NAME</i></dt>
   <dd>Spécifie le nom de l'API que vous voulez exposer.</dd>
   <dt>--bluemix</dt>
   <dd>Répertorie les clés d'API {{site.data.keyword.Bluemix_notm}} pour l'API spécifiée.</dd>
   <dt>--external</dt>
   <dd>Répertorie les clés d'API externes pour l'API spécifiée.</dd>
   </dl>

### Sortie

La commande génère un tableau qui répertorie les informations ci-après relatives aux API spécifiées :


   <dl>
     <dt>Nom de la clé</dt>
	 <dd>Nom de la clé d'API.</dd>
	 <dt>Type de clé</dt>
	 <dd>Type de la clé d'API. Les entrées valides sont <em>bluemix</em> et <em>external</em>.</dd>
	 <dt>ID client</dt>
	 <dd>Nom du client qui est identifié par la clé.</dd>
	 <dt>Valeur confidentielle fournie</dt>
	 <dd>Indique si la valeur confidentielle de l'API est fournie pour l'API. Les valeurs possibles sont <em>true</em> s'il y a une valeur confidentielle, et <em>false</em>, dans le cas contraire.</dl>


### Exemples

Retourne toutes les clés externes qui sont associées à l'API intitulée cloudfound1.

```
bluemix apim --name cloudfound1 --external
```

Retourne les clés qui autorisent les personnes figurant à l'intérieur de mon organisation {{site.data.keyword.Bluemix_notm}} à voir mon API myapi1.

```
bluemix apim --name myapi1 --bluemix 
```
 
