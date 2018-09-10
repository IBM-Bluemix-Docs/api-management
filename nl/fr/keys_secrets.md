---

copyright:
  years: 2017,2018
lastupdated: "2018-01-05"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Gestion des clés et des valeur confidentielles
{: #keys_secrets}

Quand vos API sont gérées par la fonctionnalité de gestion des API, vous pouvez utiliser les clés et les valeur confidentielles pour contrôler l'accès aux API.

## Création d'une clé et d'une valeur confidentielle
{: #create_key_secret}

Pour ajouter une clé à votre API, procédez comme suit :

1. Ouvrez votre application Cloud Foundry ou l'API {{site.data.keyword.openwhisk_short}}, si ce n'est pas déjà fait.

2. Sélectionnez *API Management* dans la navigation.

3. Sélectionnez l'onglet Partage et clés pour accéder aux clés pour cette application ou API. *Remarque : vous ne pouvez voir les onglets qu'après une première sauvegarde de votre application ou API.*

4. Assurez-vous que le curseur **Exposer l'API gérée** est *activé*. Votre API doit être exposée pour que vous puissiez affecter des touches.

5. Créez une clé pour un client qui a accès à votre organisation {{site.data.keyword.Bluemix_notm}}.
  1. Sélectionnez **Créer une clé d'API** dans la section *Partage dans l'organisation {{site.data.keyword.Bluemix_notm}}*. Une clé et une valeur confidentielle sont automatiquement créées et entrées dans les zones adéquates. Vous ne pouvez pas mettre à jour la clé ou la valeur confidentielle pour ce type de clé. 
  2. Entrez un nom pour la clé et la valeur confidentielle afin de faciliter leur identification, comme le nom du client qui l'utilisera.
  3. Sélectionnez **Enregistrer** pour enregistrer la nouvelle clé.
  4. Vous pouvez répéter les étapes *a* à *c* pour les clés supplémentaires, si nécessaire. Vous pouvez avoir un maximum de 5 clés dans cette section par API.

6. Créez une clé pour un client qui n'est pas membre de votre organisation {{site.data.keyword.Bluemix_notm}}.
  1. Sélectionnez **Créer une clé d'API** dans la section *Partage en dehors de l'organisation {{site.data.keyword.Bluemix_notm}}*. Une clé est automatiquement créée et entrée dans la zone adéquate. Il n'y a pas de valeur confidentielle qui s'affiche initialement pour ce type de clé. Vous ne pouvez pas mettre à jour la clé. 
  2. Entrez un nom pour votre clé afin de faciliter son identification, comme le nom du client qui l'utilisera.
  3. Facultatif : si vous voulez ajouter une valeur confidentielle, sélectionnez **Lien vers le portail d'API** pour la clé dans laquelle vous voulez ajouter la valeur confidentielle et sélectionnez la commande permettant de définir la valeur confidentielle d'API.
  4. Sélectionnez **Enregistrer** pour enregistrer la nouvelle clé.
  5. Vous pouvez répéter les étapes *a* à *d* pour les clés supplémentaires, si nécessaire. Vous pouvez avoir un maximum de 5 clés dans cette section par API.
Vos clés sont répertoriées pour l'API quand l'onglet *Partage et clés* est sélectionné.

## Spécification d'une clé et d'une valeur confidentielle dans un appel d'API
{: #spec_key_secret}

Vos clients ne peuvent appeler votre API que s'ils incluent la clé correcte, la valeur confidentielle adéquate, ou les deux, dans l'en-tête de l'appel. Pour appeler l'API, ils doivent inclure la clé et la valeur confidentielle dans l'appel d'API, comme illustré dans l'exemple suivant :
```
curl --request PUT \
  --url https://appidtest.mybluemix.net/ \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --header 'x-ibm-client-secret: add_secret_here' \
  --data '{"id":999999999999999}'
```
{: codeblock}
Où *add_secret_here* est remplacé par la valeur confidentielle pour la clé adéquate. 

## Suppression d'une clé d'API
{: #delete_key}

A un certain moment, vous voudrez peut-être retirer une clé. Un client qui utilisait votre API peut avoir créé sa propre API et ne plus avoir besoin de la vôtre. Pour vous assurer qu'aucun de ses propres clients n'utilise votre API,vous pouvez supprimer la clé. Pour supprimer une clé d'un service, procédez comme suit :

1. Ouvrez votre application Cloud Foundry ou l'API {{site.data.keyword.openwhisk_short}}, si ce n'est pas déjà fait.

2. Sélectionnez *API management* dans la navigation.

3. Sélectionnez l'onglet *Partage et clés*.

4. Localisez la clé que vous voulez supprimer. Astuce : c'est là qu'il est utile de donner un nom aux clés afin qu'elles soient facilement identifiables.

5. Sélectionnez l'icône relative aux options, qui représente trois points alignés verticalement, en regard de la clé que vous voulez supprimer. 

6. Sélectionnez **Supprimer la clé**.

7. Confirmez la supprimer pour retirer la clé.
