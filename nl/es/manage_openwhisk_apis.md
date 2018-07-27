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

# Creación de API desde acciones de {{site.data.keyword.openwhisk_short}}
{: #manage_openwhisk_apis}

Las acciones de {{site.data.keyword.openwhisk_short}} se pueden beneficiar de la gestión por parte de la función de gestión de API.

Con la gestión de API, puede exponer una acción de {{site.data.keyword.openwhisk_short}} como una API. Después de definir la API, puede aplicar políticas de seguridad y de limitación de tasas, ver el uso de la API y los registros de respuestas y definir políticas de compartición de API.  

Para crear una API de {{site.data.keyword.openwhisk_short}}, siga los pasos siguientes:

1. En el panel de control de {{site.data.keyword.openwhisk_short}}, pulse el separador **API**. Si ya tiene API de {{site.data.keyword.openwhisk_short}} creadas, se muestra una lista de sus API de {{site.data.keyword.openwhisk_short}}. Si aún no tiene ninguna API de {{site.data.keyword.openwhisk_short}}, se muestra la pantalla de iniciación. 
2. Pulse **Crear una API de {{site.data.keyword.openwhisk_short}}**. Se muestra la ventana Crear API para {{site.data.keyword.openwhisk_short}}. 
3. Rellene los campos de la sección Información de API y luego pulse **Crear operación**. Se muestra la ventana Crear operación. Se crean operaciones para definir el punto final, la vía de acceso https y el método para la API.
4. En la ventana "Crear operación", rellene los campos necesarios para la operación de {{site.data.keyword.openwhisk_short}}. Los campos incluidos en la ventana "Crear operación" son los siguientes:

    * Vía de acceso - Vía de acceso donde se encuentra la API. 
    * Verbo - El método HTTP para la API. Seleccione uno de los siguientes métodos:
	    * DELETE
		* GET
		* HEAD
		* OPTIONS
		* PATCH
		* POST
		* PUT
	* Paquete que contiene la acción - Los paquetes que ya están disponibles en su organización que pueden tener la acción que desea utilizar para esta API. Consulte [Uso y creación de paquetes de Funciones de Cloud](../openwhisk/openwhisk_packages.html) para obtener más información sobre este campo.
	* Acciones - **Acciones que están disponibles en {{site.data.keyword.Bluemix_notm}}** es la única opción que está disponible.
	* Tipo de contenido de respuesta - Identifica el formato en que la API devuelve la información. Puede seleccionar entre los siguientes formatos:
	    * application/json - Es el formato predeterminado y el que se utiliza con más frecuencia.
		* text/html - Se utiliza para respuestas que se utilizan en un sitio web.
		* text/plain - Se proporciona en texto sin formato y pueden utilizarse en archivos de valores separados por coma.
		* image/svg+xml - Puede utilizarse cuando el formato principal de las respuestas son capturas de pantalla.
		* Utilizar la cabecera "Content-Type" de la acción - Este parámetro depende del tipo de contenido que está en la cabecera de la respuesta. 
	
5. Seleccione **Crear** para crear la operación. La operación se añade a la tabla Operaciones que invocan acciones de {{site.data.keyword.openwhisk_short}}.
5. Especifique el resto de la información que desee. También puede añadir o actualizar el resto de la información más tarde cuando gestione las API.
6. Pulse **Guardar**. Se abre la página de visión general de la gestión de API correspondiente a su API y se muestra toda la información que acaba de definir.
7. Continúe gestionando la API con [Gestionar API](manage_apis.html).
