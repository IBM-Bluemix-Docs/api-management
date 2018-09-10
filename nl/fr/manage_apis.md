---

copyright:
  years: 2017,2018
lastupdated: "2018-08-23"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Gestion des API
{: #manage_apis}

Après avoir intégré votre API afin de la gérer et de la surveiller grâce au système de gestion d'API, vous pouvez afficher et modifier ses paramètres. Si vous n'avez pas intégré votre API, vous devez en intégrer une en procédant comme indiqué dans [Création d'API à partir d'actions {{site.data.keyword.openwhisk_short}}](manage_openwhisk_apis.html) ou dans [Activation des noeuds finaux gérés d'API](manage_cf_apis.html). 

Pour gérer les paramètres de votre API, procédez comme suit :

Si vous avez créé une API, et qu'elle est déjà ouverte dans l'interface, vous pouvez ignorer les trois premières étapes.

1. Sélectionnez l'API que vous souhaitez gérer à partir du tableau de bord {{site.data.keyword.Bluemix}} ou en choisissant une action sur le tableau de bord du service {{site.data.keyword.openwhisk_short}}, si les informations de votre API ne sont pas déjà affichées.
2. Cliquez sur **API Management** dans la navigation, ou sélectionnez l'onglet **API** s'il s'agit d'une action {{site.data.keyword.openwhisk_short}}.
3. Si nécessaire, sélectionnez l'API à gérer. Une fois la connexion établie, vous pouvez afficher et mettre à jour les sélections suivantes :
    * Récapitulatif
    * Définition
    * Partage
    * Explorateur d'API
4. Sélectionnez le curseur Exposer l'API gérée pour l'activer et exposer votre API. Remarque : Il n'est pas possible de définir certains paramètres lorsque l'API n'est pas exposée.  

## Récapitulatif des paramètres des API
{: #overview_api}

L'onglet Récapitulatif est sélectionné par défaut lorsque vous choisissez une API ; il comporte deux sections :
* Propriétés - La section Propriétés affiche les informations suivantes :
    * Informations de base sur l'API
	* Règles de sécurité
	* Informations sur les limites de fréquence
    * Détails du partage
* Analyse et consignation - La section Analyse et consignation affiche les statistiques suivantes :
	* Nombre de réponses et temps de réponse moyen au cours du dernier intervalle de temps que vous indiquez
    * Nombre d'appels API par minute, au format graphique
    * 100 dernières réponses dans le tableau Journal des réponses
	
Le graphique *Réponses* illustre rapidement le nombre de réponses reçues par votre API, ainsi que la répartition du statut des réponses. Cela peut vous aider à savoir si vous recevez une majorité de réponses d'erreur. Une majorité de réponses d'erreur peut signifier que votre trafic est plus important que ce que vous avez autorisé dans les paramètres de fréquence. Pour afficher la répartition numérique des réponses par code de réponse, survolez l'icône d'information. Voici les codes de réponse courants :
* 200  OK
* 201  Créé)
* 302  Trouvé
* 304  Non modifié
* 400  Demande incorrecte
* 401  Non autorisé
* 403  Interdit
* 500  Erreur de serveur interne
* 503  Service non disponible

Le tableau Journal des réponses contient les détails des 100 dernières réponses. Vous pouvez trier ces informations selon les entrées d'une colonne en sélectionnant l'en-tête de colonne approprié. Vous pouvez rechercher des entrées spécifiques dans le tableau Journal des réponses à l'aide de la barre *Effectuer des recherches dans les réponses*. Si vous souhaitez avoir davantage d'informations sur un événement, sélectionnez-le ou sélectionnez **Afficher les détails** dans le menu de liste des options (trois points verticaux) situé en regard de l'entrée concernée.


## Edition des paramètres d'API
{: #settings_api}

Dans l'onglet **Définition**, vous pouvez mettre à jour les informations de base concernant votre API. Ces informations incluent la documentation, le nom et l'URL de base. Utilisez la section Sécurité et limitation de débit pour indiquer un appel et une limite d'intervalle afin de veiller à ce que seul un certain nombre d'appels soient effectués par seconde, par minute ou par heure. Vous pouvez également demander une authentification lors de la création d'appels d'API afin d'empêcher toute utilisation non voulue de vos données, ou pour rassembler des statistiques sur l'API.

Pour modifier les paramètres d'une API, procédez comme suit :

1. Dans le tableau de bord de gestion de l'API, cliquez sur l'onglet **Définition**.
2. Vous pouvez nommer ou mettre à jour le nom de votre API et importer une définition d'API dans la section Informations sur l'API.
3. La section Sécurité et limitation de débit vous permet de mettre à jour les règles suivantes :
    * ///Require API key - Indique si l'appel API doit être traité uniquement si la clé d'API correcte est fournie. La valeur par défaut ne requiert pas de clé supplémentaire.
    * ///Security method - Lorsque l'option de clé d'API est sélectionnée, indique si le traitement de l'API requiert uniquement la clé d'API, ou s'il nécessite la clé d'API et la valeur confidentielle de l'API.
    * Emplacement de la clé d'API et du secret - En fonction des paramètres de la méthode, indique la manière dont les informations de sécurité de votre API sont incluses dans l'appel. Les noms d'appel précisent le mode d'identification des informations de sécurité. Pour plus d'informations sur l'utilisation des clés et des valeur confidentielles, voir [Gestion des clés et des valeur confidentielles](keys_secrets.html).
    * Limiter le débit des appels d'API clé par clé - Définit le nombre d'appels API autorisés pendant un intervalle de temps spécifié ; vous pouvez définir ce nombre pour chaque clé. Notez que le type burst-type de la méthode rate-limiting est utilisé. La fréquence moyenne des appels d'API est calculée pendant la durée totale de l'intervalle de temps que vous indiquez dans la fréquence. Si la fréquence des appels API pendant un intervalle excède la fréquence moyenne des appels API, les appels peuvent être refusés pendant un certain temps, jusqu'à la limite de durée indiquée dans la fréquence.   
    * Fournisseur OAuth - Permet de s'assurer via la mise en oeuvre du protocole OAuth pour les données d'identification de connexion sociale de fournisseurs tels que Google, Facebook, IBM App ID et GitHub, que seuls les utilisateurs dotés des paramètres de sécurité corrects puissent accéder à vos API.
	    **Remarque :** vous devez spécifier une instance de service App ID configurée dans {{site.data.keyword.Bluemix_notm}} pour fournir les données d'identification lorsque vous utilisez **App ID** comme fournisseur OAuth. Si vous ne disposez pas d'un service App ID existant, vous pouvez sélectionner **Créer** dans la section OAuth pour en créer un dans une nouvelle fenêtre, puis revenir à cette étape pour le spécifier pour la gestion d'API. Vous pouvez également sélectionner **Editer** pour changer l'instance de service sélectionnée.
4. Activer CORS - Cross-origin requests (CORS) active certaines demandes limitées provenant d'un autre domaine.
5. Cliquez sur **Sauvegarder**.

## Partage d'API
{: #share_api}

Vous pouvez partager des API avec d'autres utilisateurs dans ou en dehors de votre organisation {{site.data.keyword.Bluemix_notm}}. 

Quand vous partagez vos API avec d'autres personnes, qui se trouvent à l'intérieur ou à l'extérieur de votre organisation {{site.data.keyword.Bluemix_notm}}, vous pouvez créer des clés et des valeur confidentielles pour vos API. Chaque API gérée prend en charge 5 clés qui peuvent être créées et affectées à cette API. En envoyant une clé unique à un individu ou une société, vous pouvez suivre certaines statistiques sur le mode d'utilisation de l'API. Vous pouvez ainsi connaître le nombre d'appels envoyés à votre API par cette personne ou cette société. Vous pouvez également désactiver une clé ou limiter le nombre d'appels provenant d'une clé. Cela peut s'avérer utile pendant les tests, l'équilibrage de charge et la monétisation, ou lors de la résolution de certains problèmes liés à la sécurité.

Une *clé* est une chaîne unique de caractères qui est associée à votre API. Vous pouvez affecter plusieurs clés à une API, ce qui vous facilite le contrôle de l'utilisation de l'API par chaque client. Vous attribuez, par exemple, une clé à un client et une autre clé, à un autre client. Chaque fois que les clients appellent l'API, ils incluent la clé qui leur a été attribuée. En effectuant un suivi de cette clé, vous connaissez le nom du client qui a appelé l'API.

Il existe deux types de clés :

* Clés pour le partage de l'API avec les clients qui ont accès à votre organisation {{site.data.keyword.Bluemix_notm}}. 
* Clés pour le partage de l'API avec les clients qui n'ont pas accès à votre organisation {{site.data.keyword.Bluemix_notm}}. 

Les différents types de clés sont créés, gérés et supprimés de la même façon, la seule différence étant de savoir qui est en mesure d'utiliser les clés.

Une fois que vous avez créé une ou plusieurs clés pour votre API, vous pouvez limiter, par clé, le débit des appels effectués vers cette API. En activant le curseur **Limiter le débit des appels d'API clé par clé** sur l'onglet *Définition*, la limite spécifiée s'applique au nombre d'appels pour chaque clé que vous avez créée.   

Une *valeur confidentielle* est similaire à une clé, en ce sens qu'elle est utilisée pour gérer l'accès à l'API elle-même. Elle est personnalisable et peut être modifiée sans changer la clé. Il ne peut y avoir de valeur confidentielle s'il n'y a pas de clé. Ainsi, seule une personne avec la valeur confidentielle adéquate peut télécharger une nouvelle version de l'API. Vous pouvez avoir besoin d'une API et d'une valeur confidentielle pour vos appels d'API ou utiliser uniquement une clé. Les valeurs confidentielles peuvent être utiles si vous devez changer la valeur confidentielle mais ne voulez pas changer la clé. 

1. Dans le tableau de bord de gestion de l'API, cliquez sur l'onglet **Partage**.
2. Dans la zone "Partage dans l'organisation {{site.data.keyword.Bluemix_notm}}", sélectionnez **Exposer l'API gérée** si vous voulez rendre votre API disponible pour d'autres personnes avec un accès à votre organisation {{site.data.keyword.Bluemix_notm}}. Vous devez sélectionner cette option pour générer une clé.
3. Cliquez sur **Créer une clé d'API** afin de créer une clé unique pour votre API. La boîte de dialogue Créer une clé d'API s'affiche. La clé d'API est générée automatiquement.
4. Utilisez la clé d'API pour savoir quel utilisateur accède à l'API en envoyant à un utilisateur une clé unique. La passerelle peut savoir quelle la clé (et quel client) génère l'appel.
5. Cliquez sur l'icône **Menu** (trois points verticaux) en regard de la clé pour éditer ou supprimer cette clé d'API.

La section Partage en dehors de l'organisation {{site.data.keyword.Bluemix_notm}} vous permet de partager votre API avec des utilisateurs qui ne disposent pas d'un compte {{site.data.keyword.Bluemix_notm}}. Cette méthode de partage fournit un lien direct qui permet d'affiche les informations concernant votre API dans l'explorateur d'API. L'API contient un bouton permettant de l'exécuter dans la vue Explorateur d'API. Pour demander un lien vers votre API, procédez comme suit :

1. Dans la section Partage en dehors de l'organisation {{site.data.keyword.Bluemix_notm}} Organization, cliquez sur **Créer une clé d'API**. La boîte de dialogue Créer une clé d'API s'affiche.
     Vous remarquerez que l'utilisateur dispose d'une valeur confidentielle que vous ne contrôlez pas.
2. Indiquez un nom unique pour la clé d'API.
3. Sélectionnez **Créer une clé**. 
4. Envoyez le lien vers le portail d'API au client qui ne dispose pas d'un compte {{site.data.keyword.Bluemix_notm}}. La clé d'API et la valeur confidentielle (le cas échéant) étant incluses dans le lien, vous pouvez ainsi déterminer la clé qui a généré le lien.
  
Le lien de la documentation de l'API ouvre l'API dans l'onglet **Explorateur d'API**.

Pour plus d'informations sur l'utilisation des clés et des valeur confidentielles, voir [Gestion des clés et des valeur confidentielles](keys_secrets.html).

## Affichage et test dans l'explorateur d'API
{: #explore_api}

Sélectionnez l'onglet Explorateur d'API pour afficher le code html généré à partir de votre document Swagger. 

L'explorateur d'API affiche toutes les actions et la documentation de l'API qui s'appliquent à l'API. Vous pouvez afficher les opérations et les actions, ainsi que leur description, et tester l'API à partir de l'interface utilisateur. Vous pouvez également télécharger le document Swagger afin de réutiliser son contenu.

Pour tester l'API, procédez comme suit :
1. *Exemples* est sélectionné par défaut. Il s'agit d'un exemple du code de l'API sélectionnée.
2. Modifiez le format de l'exemple, si nécessaire, en sélectionnant un langage dans le menu situé en regard du langage indiqué. 
3. Sélectionnez **Essayez-la**.
4. Sélectionnez **Appeler une opération**. 

La réponse à la question s'affiche. 

## Domaines personnalisés
{: #custom_domains}

Dans certains cas, vous pouvez vouloir disposer d'un domaine personnalisé au lieu du domaine par défaut de la passerelle d'API. La fonctionnalité de gestion des API prend en charge la possibilité d'associer ces dernières à un nom de domaine de votre choix.

Procédez comme suit pour procéder à la configuration initiale du domaine personnalisé. Si vous avez déjà configuré le domaine, voir [Utilisation d'un domaine personnalisé avec votre API](manage_apis.html#custom_domains_bind).

Les domaines personnalisés ne sont pas isolés sur une API unique, mais sont étendus à un groupe d'API défini par 
- Le service {{site.data.keyword.Bluemix_notm}} d'origine (par exemple, {{site.data.keyword.openwhisk_short}})
- L'espace Cloud Foundry

Par exemple, un domaine personnalisé sera étendu à toutes les API {{site.data.keyword.openwhisk_short}} créées dans l'espace Cloud Foundry "dev".

### Configuration

Pour commencer, créez d'abord une nouvelle API dans un service {{site.data.keyword.Bluemix_notm}} qui prend en charge la fonctionnalité API Management intégrée, ou créez un proxy d'API à l'aide de la console des API {{site.data.keyword.Bluemix_notm}}.

#### Préparation des certificats

Pour enregistrer un domaine personnalisé, vous devez fournir des certificats TLS valides lors de la configuration. Utilisez le service [Certificate Manager](../services/certificate-manager) pour télécharger un certificat et une clé privée.

*Remarque : Les appels d'API sont uniquement disponibles via TLS (port 443). Le protocole HTTP simple n'est pas pris en charge.*

### Utilisation d'un domaine personnalisé avec votre API
{: #custom_domains_bind}

Une fois la configuration initiale terminée, liez une ou plusieurs API au domaine enregistré à partir de la section **Domaines personnalisés** de la console des API {{site.data.keyword.Bluemix_notm}} en procédant comme suit :

1. Dans la liste des cibles disponibles, localisez le service ou le domaine par défaut auquel le domaine personnalisé doit être attaché.
2. Dans une fenêtre de navigateur ou un onglet distinct, accédez à la page des paramètres de votre fournisseur DNS et créez un enregistrement CNAME pour le domaine souhaité. Utilisez la valeur de la colonne **Domaine par défaut / Alias** dans la page de gestion des domaines personnalisés {{site.data.keyword.Bluemix_notm}} comme cible CNAME, puis sauvegardez vos paramètres DNS.
  
    *Remarque : La propagation des modifications DNS peut prendre jusqu'à 48 heures, mais elle est généralement plus rapide.*
  
3. Sur la page des domaines personnalisés, cliquez sur les points de suspension de la ligne contenant le "domaine par défaut" cible, puis sélectionnez **Editer** dans le menu.
4. Dans la boîte de dialogue qui s'affiche, cochez la case **Affecter un domaine personnalisé**.
5. Indiquez le domaine personnalisé souhaité dans la zone **Nom du domaine** (par exemple, *api.mycompany.com*).
6. Copiez le nom de ressource de cloud (CRN) depuis Certificate Manager pour le certificat téléchargé lors de la configuration initiale.
7. Collez le CRN qui vous avez copié dans la zone **CRN du certificat**.
8. Cliquez sur **Sauvegarder**. Le nom de domaine spécifié doit s'afficher sur la ligne en regard du domaine par défaut, indiquant qu'il a été correctement appliqué.

*Remarque : Avant d'appliquer le domaine personnalisé, le pointeur DNS est vérifié en s'assurant que le domaine personnalisé CNAME pointe vers le domaine par défaut associé aux API. Si la configuration DNS n'est pas terminée ou que les modifications DNS de l'Etape 2 n'ont pas encore été propagées, une erreur s'affiche et les paramètres du domaine ne sont pas sauvegardés. Dans ce cas, réessayez régulièrement pendant 48 heures après la modification des paramètres DNS. Si l'erreur persiste au-delà de 48 heures, vérifiez vos paramètres DNS ou contactez le support {{site.data.keyword.Bluemix_notm}}.*
