---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-26"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Accès à des fonctions de gestion des API supplémentaires
{: #upgrade}

La fonction de gestion des API qui est fournie avec votre API {{site.data.keyword.Bluemix}} vous permet de contrôler de façon limitée le débit des appels ainsi que le protocole d'autorisation OAuth et d'afficher des analyses. Vous pouvez accroître votre contrôle sur la gestion des API en effectuant une mise à niveau vers le service {{site.data.keyword.apiconnect_full}}. Le service {{site.data.keyword.apiconnect_short}} offre plus de choix en matière de règles de sécurité, ainsi qu'un contrôle accru sur les limites de fréquence. Vous avez, de plus, la possibilité de configurer un portail de développeur entièrement personnalisable qui vous permet de diffuser vos API sur les réseaux sociaux et de vous engager auprès de la communauté des développeurs. Vous bénéficiez également d'autres avantages :
* Gestion du cycle de vie
* API composites
* Intégration des services Web
* Médiation de protocole
* Génération d'API à partir de schéma
* Développement de microservices

La migration vers le service {{site.data.keyword.apiconnect_short}} est simple et vous n'avez pas à recréer les API que vous gérez grâce à la gestion d'API. Vous pouvez migrer vos API automatiquement ou manuellement.

## Migration automatique des API vers {{site.data.keyword.apiconnect_short}}
{: #auto_migrate_api}

Si vous décidez d'effectuer une mise à niveau vers {{site.data.keyword.apiconnect_short}}, vous devez migrer vos API depuis la gestion des API vers le service {{site.data.keyword.apiconnect_short}}, en sélectionnant ci-dessous la procédure correspondant au type d'API que vous migrez puis en effectuant les différentes étapes.

### API Cloud Functions

1. Sélectionnez **Fonctions** dans votre menu {{site.data.keyword.Bluemix_notm}} pour afficher Cloud Functions.

2. Dans la liste Fonctions, sélectionnez **API** dans la navigation.

3. Sélectionnez le nom de l'API de fonction que vous voulez migrer.

4. Sélectionnez **Définition** dans la navigation.

5. Sélectionnez **Fichier de définition de l'API** > **Ouvrir dans API Connect** > **Continuer** dans la section *Fichier de définition de l'API*. Si vous disposez déjà d'un service {{site.data.keyword.apiconnect_short}} existant, l'API est migrée automatiquement vers ce service. Si vous n'avez pas encore de service {{site.data.keyword.apiconnect_short}} configuré, le service est automatiquement ajouté avec un plan limité gratuit et l'API est migrée. Si la mise à disposition de votre instance échoue, suivez la procédure décrite dans [Migration manuelle des API vers {{site.data.keyword.apiconnect_short}}](#man_migrate_api) pour procéder à une migration manuelle vers le nouveau service. 

6. Avant de fermer l'écran de l'API d'origine, désactivez le curseur pour **Exposer l'API gérée**, afin d'empêcher quiconque d'agir sur le noeud final de l'ancienne version.

### Cloud Foundry API

1. Ouvrez votre source d'API Cloud Foundry existante dans le tableau de bord {{site.data.keyword.Bluemix_notm}}. 

2. Sélectionnez **API Management** dans le menu de navigation.

3. Sélectionnez **Définition** dans la navigation.

4. Sélectionnez **Fichier de définition de l'API** > **Ouvrir dans API Connect** > **Continuer**. Si vous disposez déjà d'un service {{site.data.keyword.apiconnect_short}} existant, l'API est migrée automatiquement vers ce service. Si vous n'avez pas encore de service {{site.data.keyword.apiconnect_short}} configuré, le service est automatiquement ajouté avec un plan limité gratuit et l'API est migrée. Si la mise à disposition de votre instance échoue, suivez la procédure décrite dans [Migration manuelle des API vers {{site.data.keyword.apiconnect_short}}](#man_migrate_api) pour procéder à une migration manuelle vers le nouveau service.
   
5. Une fois le contenu migré vers l'instance {{site.data.keyword.apiconnect_short}}, sélectionnez le lien qui est fourni pour accéder à la version migrée.
    **Important :** pour empêcher les problèmes générés par l'exécution simultanée de plusieurs instances de l'API, prenez soin de désactiver le curseur de gestion de l'API dans la version d'origine de l'API.

6. Sélectionnez l'onglet **API** dans la navigation.

7. Sélectionnez **Brouillons** pour afficher votre nouvelle API.

## Migration manuelle des API vers {{site.data.keyword.apiconnect_short}}
{: #man_migrate_api}

Si le processus de migration de votre API vers le service {{site.data.keyword.apiconnect_short}} ne s'est pas terminé correctement, procédez comme suit pour effectuer une migration manuelle :

1. Ouvrez votre API.
	1. Connectez-vous à {{site.data.keyword.Bluemix_notm}}.
	2. Pour une application Cloud Foundry : 
		1. Sélectionnez **Tableau de bord** dans le menu.
		2. Sélectionnez le nom de l'application Cloud Foundry que vous voulez migrer.
		3. Sélectionnez **API Management** dans la navigation.
	3. Pour une action Cloud Functions : 
		1. Sélectionnez **Fonctions** dans le menu.
		2. Sélectionnez **API** dans la navigation.
		3. Sélectionnez le nom de l'API que vous voulez migrer.
2. Téléchargez le document Swagger de l'API à partir de la gestion d'API.
    1. Sélectionnez **Définition** dans la navigation.
	2. Sélectionnez **Fichier de définition de l'API**.
    3. Sélectionnez **Exporter YAML** ou **Exporter JSON**, selon votre type de fichier, pour télécharger la définition de l'API. Le fichier est enregistré dans votre dossier de téléchargement.
3. Créez et préparez l'instance {{site.data.keyword.apiconnect_short}}. 
	1. Accédez à **API** dans la navigation pour filtrer les services.
	2. Sélectionnez le service API Connect. 
    3. Créez une instance du service {{site.data.keyword.apiconnect_short}} à partir du catalogue {{site.data.keyword.Bluemix_notm}}.
	4. Sélectionnez votre plan. Le plan limité est une option gratuite.
	5. Sélectionnez **Créer** pour créer l'instance.
4. Importez le document Swagger dans votre instance {{site.data.keyword.apiconnect_short}} en procédant comme suit :
	1. Dans le tableau de bord du service
{{site.data.keyword.apiconnect_short}}, sélectionnez **Accéder à... (>>)** > **Brouillons** dans le menu.
	2. Sélectionnez l'onglet API.
	3. Sélectionnez **+Ajouter** > **Importer l'API à partir d'un fichier ou d'une URL**.
	4. Recherchez et sélectionnez le fichier Swagger que vous avez téléchargé depuis la gestion d'API. Sélectionnez **Ouvrir**.
	5. Sélectionnez **Importer** pour importer votre API dans le service {{site.data.keyword.apiconnect_short}}.
5. Pour empêcher les problèmes générés par l'exécution simultanée de plusieurs instances de l'API, prenez soin de désactiver le curseur de gestion de l'API dans la version d'origine de l'API.

Votre API est disponible dans l'instance de service {{site.data.keyword.apiconnect_short}}. 

## Publication de l'API

Vous pouvez publier l'API en procédant comme suit :

1. Créez un catalogue.
	1. Sélectionnez **+Ajouter** pour créer un catalogue.
	2. Entrez un nom d'affichage et un nom pour le catalogue, puis sélectionnez **Ajouter**.
	3. Sélectionnez le catalogue que vous avez créé.
2. Indiquez les paramètres de votre API.
    1. Sélectionnez **Créer un produit**.
	2. Spécifiez un nom pour le produit.
	2. Sélectionnez le produit que vous avez créé pour afficher ses paramètres.
	3. Définissez la limite de fréquence de l'API.
	4. Définissez le niveau de l'API.
3. Ajoutez le noeud final de l'API, si nécessaire.
    1. Sélectionnez l'API.
	2. Sélectionnez l'onglet Assemblage.
	3. Ajoutez le noeud final, s'il n'est pas déjà spécifié.
	
 Après avoir migré vos API, vous pouvez accéder à toutes les fonctions de gestion des API en ouvrant la mosaïque de services {{site.data.keyword.apiconnect_short}} et à partir du tableau de bord {{site.data.keyword.Bluemix_notm}}. 

