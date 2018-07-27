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

# Exécution de commandes avec l'interface de ligne de commande de gestion des API
{: #apim-cli-over}

Vous pouvez utiliser l'interface de ligne de commande de gestion des API {{site.data.keyword.Bluemix_notm}} pour exécuter certaines des tâches que vous pouvez effectuer aussi avec l'interface utilisateur graphique {{site.data.keyword.Bluemix_notm}}. Les commandes peuvent être entrées individuellement dans une fenêtre de terminal ou appelée dans une séquence d'un script.
{:shortdesc}

## Prérequis
{: #apim-cli-script-prereq}

Avant de pouvoir utiliser l'interface de ligne de commande de gestion des API, vous devez avoir effectué les étapes suivantes :

* Obtenez un [ID Bluemix](../../admin/adminpublic.html#signing-up-for-bluemix){: new_window}. 
* Téléchargez et installez la [ligne de commande Bluemix](../../cli/reference/bluemix_cli/index.html#getting-started){: new_window}.
* Installez le plug-in de ligne de commande de gestion des API {{site.data.keyword.Bluemix_notm}} [](../../cli/reference/bluemix_cli/index.html#install_plug-in){: new_window}.
* [Connectez-vous](../../cli/reference/bluemix_cli/bx_cli.html){: new_window} à la ligne de commande {{site.data.keyword.Bluemix_notm}}.

## Séquence de ligne de commande exemple des commandes pour une API

La procédure ci-dessous illustre un cycle complet de commandes de gestion d'API allant de l'ajout d'une passerelle à une API à son retrait de cette API :

1. Connectez-vous à {{site.data.keyword.Bluemix_notm}} 
    ```
    bluemix login -a https://api.ng.bluemix.net -c account_ID (1) -u username -p password
    ```
    {:codeblock}
    Vous connecte à votre organisation {{site.data.keyword.Bluemix_notm}} par défaut avec l'interface de ligne de commande.

2. Affichez vos API
    ```
    bluemix apim apis
    ```
    {:codeblock}
    Affiche les API de votre organisation par défaut.

3. Créez une API
    ```
    bluemix apim api-create --name <API_NAME> --file <path_to_Swagger_file>
    ```
    {:codeblock}
    Utilise le fichier Swagger pour créer une API gérée depuis l'API que vous avez spécifiée dans votre organisation {{site.data.keyword.Bluemix_notm}}.

4. Mettez à jour une définition d'API existante
    ```
    bluemix apim api-update --name <API_NAME> --file <path_to_new_Swagger_file>
    ```
    {:codeblock}
    Remplace la définition existante de l'API que vous avez spécifiée par la nouvelle définition de fichier Swagger.

5. Exposez l'API
    ```
    bluemix apim api-expose --name <API_NAME>
    ```
    {:codeblock}
    Expose l'API.

6. Partagez l'API
    ```
    bluemix apim api-share --name <API_NAME>
    ```
    {:codeblock}
    Partage l'API avec d'autres personnes qui se trouvent à l'extérieur de votre organisation {{site.data.keyword.Bluemix_notm}}.

7. Arrêtez d'exposer l'API
    ```
    bluemix apim api-unexpose --name <API_NAME>
    ```
    {:codeblock}
    Arrête le partage de l'API à l'extérieur de votre organisation {{site.data.keyword.Bluemix_notm}}.

8. Affichez les clés pour votre API
    ```
    bluemix apim keys --name <API_NAME>
    ```
    {:codeblock}
    Affiche les clés qui sont associées à votre API, le cas échéant.

9. Arrêtez de partager l'API
    ```
    bluemix apim api-unshare --name <API_NAME>
    ```
    {:codeblock}
    Arrête le partage de l'API.
	
10. Retirez l'API
    ```
    bluemix apim api-delete --name <API_NAME>
    ```
    {:codeblock}
    Retirez la passerelle de l'API. Elle n'est alors plus gérée.
    Important : si vous supprimez une API Cloud Foundry, l'application Cloud Foundry de base reste dans le service {{site.data.keyword.Bluemix_notm}}, mais elle n'est plus gérée. Une API OpenWhisk qui est supprimée retire toutes les interactions entre les actions OpenWhisk individuelles. Une fois l'API OpenWhisk supprimée, elle doit être recréée si vous voulez la réutiliser.
    
Voir la rubrique relative aux [commandes d'interface de ligne de commande](../../cli/plugins/api-management-cliplugin/index.html) pour une liste complète des commandes de gestion d'API avec leurs options.

