---

copyright:
  years: 2017,2018
lastupdated: "2018-01-11"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Mis API
{: #manage_api}

Seleccione **API gestionadas** en la navegación de la sección **API** para ver el estado general de las API que gestiona y de las que ha gestionado pero actualmente no están expuestas. Seleccione **API compartidas** para ver todas las API que se han compartido con su organización de {{site.data.keyword.Bluemix_notm}} a través de la gestión de API o del servicio {{site.data.keyword.apiconnect_full}}. **Tarifas** enumera y proporciona los detalles para las opciones de servicio de {{site.data.keyword.apiconnect_service}} disponibles.

Puede ver juntas todas las API que gestiona con la gestión de API en el panel de control de API. 

## Visualización de las API gestionadas
{: #view_api}

Aquí puede ver las API creadas para aplicaciones de Cloud Foundry, acciones de {{site.data.keyword.openwhisk_short}} y otras fuentes externas.

1. Desde el panel de control de {{site.data.keyword.Bluemix_notm}}, seleccione el icono **Menú** > **API**.
2. Para seleccionar su origen, pulse **API gestionadas**. Se muestra una lista de las API que se gestionan actualmente. Los tipos de API incluyen los siguientes:
    * Puntos finales definidos por el usuario - Estas entradas son API que están fuera del entorno de {{site.data.keyword.Bluemix_notm}} y de las que hace un seguimiento su punto final de URL. 
	* Apps CF - Estas entradas son apps de Cloud Foundry que tienen una gestión de API correspondiente.
    * Apps de {{site.data.keyword.openwhisk_short}} - Estas entradas son acciones de {{site.data.keyword.openwhisk_short}} acomodadas dentro de una API.

Seleccione el nombre de una API para ver más detalles sobre la misma.

## Creación de API gestionadas
{: #create_mgd_api}

Puede añadir una API a la lista sin abandonar la lista de API gestionadas seleccionando **Crear API gestionada**.

Después de seleccionar si desea crear una API de Cloud Foundry, de una acción de {{site.data.keyword.openwhisk_short}} o de proxy de API (externa), especifique la información correspondiente a la nueva API.  

Este es el único lugar donde puede añadir una API de proxy, o API externa. Una API externa es una que no se crea ni se almacena en el espacio de la organización de {{site.data.keyword.Bluemix_notm}}. Puede gestionar una API externa especificando el URL de su punto final externo. Esto se resultará útil si prueba la gestión de API para ver si se ajusta a sus necesidades, o si ya tiene API en ejecución con URL existentes que no desea interrumpir. 

Consulte [Gestión de API](manage_apis.html) para obtener más información sobre los valores necesarios para crear las API.

## Cómo trabajar con API compartidas
{: #share_api}

En la sección **API compartidas**, puede ver las API que otros han creado y que han compartido con usted. También puede crear claves de API para las API asociadas con apps de Cloud Foundry, acciones de {{site.data.keyword.openwhisk_short}} y con el servicio {{site.data.keyword.appconserviceshort}}.

1. Desde el panel de control de {{site.data.keyword.Bluemix_notm}}, pulse el icono **Menú** > **API**.
2. Seleccione **API compartidas** en la navegación. Aquí se muestran todas las API que puede consumir.
3. Para consumir una API, selecciónela para abrir su portal de desarrollador, donde se puede suscribir a un plan para utilizarla. 
4. Después de seleccionar la API que desea gestionar, consulte [Gestión de API](manage_apis.html) para obtener más información sobre cómo realizar las tareas siguientes: 
    * Ver la utilización de una API
    * Crear claves de API
    * Utilice el Explorador de API para ver documentación y probar la API.
