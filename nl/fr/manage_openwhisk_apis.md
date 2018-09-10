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

# Création d'API à partir d'actions {{site.data.keyword.openwhisk_short}}
{: #manage_openwhisk_apis}

Il est possible de gérer les actions {{site.data.keyword.openwhisk_short}} via la fonctionnalité de gestion des API.

La gestion des API vous permet d'exposer une action {{site.data.keyword.openwhisk_short}} en tant qu'API. Après avoir défini l'API, vous pouvez appliquer les règles de sécurité et de limite de fréquence, afficher l'utilisation de l'API ainsi que les journaux de réponses, et définir les règles de partage.  

Pour créer une API {{site.data.keyword.openwhisk_short}}, procédez comme suit :

1. Dans le tableau de bord {{site.data.keyword.openwhisk_short}}, cliquez sur l'onglet **API**. Si vous avez déjà créé des API {{site.data.keyword.openwhisk_short}}, la liste de vos API {{site.data.keyword.openwhisk_short}} créées s'affiche. Si vous ne disposez d'API {{site.data.keyword.openwhisk_short}}, un écran Initiation s'affiche. 
2. Cliquez sur **Créer une API {{site.data.keyword.openwhisk_short}}**. La fenêtre Créer une API pour {{site.data.keyword.openwhisk_short}} s'affiche. 
3. Renseignez les zones de la section Informations sur l'API, puis cliquez sur **Créer l'opération**. La fenêtre Créer l'opération s'affiche. Vous créez des opérations pour définir le noeud final, le chemin https et la méthode de votre API.
4. Dans la fenêtre Créer l'opération, renseignez les zones obligatoires pour votre opération {{site.data.keyword.openwhisk_short}}. Les zones de la fenêtre Créer l'opération sont les suivantes :

    * Chemin : chemin de votre API. 
    * Instruction : méthode HTTP de votre API. Sélectionnez l'une des méthodes suivantes :
	    * DELETE
		* GET
		* HEAD
		* OPTIONS
		* PATCH
		* POST
		* PUT
	* Package contenant l'action : packages déjà disponibles dans votre organisation et susceptibles de contenir l'action que vous souhaitez utiliser pour cette API. Voir la rubrique relative à l'[utilisation et à la création de packages Cloud Functions](../openwhisk/openwhisk_packages.html) pour plus d'informations sur cette zone.
	* Actions : **seules les actions disponibles dans {{site.data.keyword.Bluemix_notm}}** sont disponibles ici.
	* Type de contenu de réponse : identifie le format dans lequel l'API renvoie les informations. Vous pouvez sélectionner l'un des formats suivants :
	    * application/json : format par défaut, le plus souvent utilisé.
		* text/html : Utilisé pour les réponses employées sur un site Web.
		* text/plain : format de texte en clair, peut être employé dans des fichiers de valeurs séparées par des virgules.
		* image/svg+xml : peut être utilisé lorsque les réponses sont principalement des captures d'écran.
		* Utiliser l'en-tête "Content-Type" de l'action : dépend du type de contenu de l'en-tête de la réponse. 
	
5. Sélectionnez **Créer** pour créer l'opération. L'opération est ajoutée dans le tableau des opérations qui appellent les actions {{site.data.keyword.openwhisk_short}}.
5. Renseignez les informations restantes que vous souhaitez indiquer. Vous pouvez également ajouter ou mettre à jour ces informations ultérieurement au cours de la gestion des API.
6. Cliquez sur **Sauvegarder**. La page de présentation de la gestion de vos API s'ouvre et toutes les informations que vous venez de définir s'affichent.
7. Continuez la gestion de votre API en passant à la rubrique [Gestion des API](manage_apis.html).
