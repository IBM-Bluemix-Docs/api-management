---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-10"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Acceso a más características de gestión de API
{: #upgrade}

La función de gestión de API que se proporciona con la API de {{site.data.keyword.Bluemix}} le permite el control limitado de tarifas de llamadas, OAuth, y analíticas de vista. Dispondrá de un mayor control sobre la gestión de las API si actualiza al servicio {{site.data.keyword.apiconnect_full}}. El servicio {{site.data.keyword.apiconnect_short}} ofrece más opciones de políticas de seguridad y un mayor control sobre los límites de tasas. Además, podrá configurar un portal de desarrollador completamente personalizable para poder socializar sus API y comunicarse con la comunidad de desarrolladores. Otras de sus ventajas son:
* Gestión del ciclo de vida
* API compuestas
* Integración de servicios Web
* Mediación de protocolos
* Generación de API a partir de esquema
* Desarrollo de microservicios

La migración al servicio {{site.data.keyword.apiconnect_short}} es muy sencilla y no tienen que volver a crear ninguna de las API que gestiona actualmente con gestión de API. Puede migrar sus API de forma automática o manual.

## Migración de API automáticamente a {{site.data.keyword.apiconnect_short}}
{: #auto_migrate_api}

Si decide actualizar a {{site.data.keyword.apiconnect_short}}, tendrá que migrar sus API de gestión de API al servicio {{site.data.keyword.apiconnect_short}} seleccionando y completando el procedimiento siguiente para el tipo de API que está migrando.

### API de funciones de Cloud

1. Seleccione **Funciones** en el menú de {{site.data.keyword.Bluemix_notm}} para ver sus Funciones de Cloud.

2. En la lista Funciones, seleccione **API** en la navegación.

3. Seleccione el nombre de la API de función que desea migrar.

4. Seleccione **Definición** en la navegación.

5. Seleccione **Archivo de definición de API** > **Exportar a API Connect** > **Exportar API** en la sección *Archivo de definición de API*. Si ya tiene un servicio de {{site.data.keyword.apiconnect_short}} existente, se migrará la API automáticamente al servicio existente. Si todavía no tiene un servicio de {{site.data.keyword.apiconnect_short}} configurado, se añadirá automáticamente el servicio con un plan Lite gratuito y migrará la API. Si la instancia no se ha podido suministrar, siga los pasos de [Migración manual de API a {{site.data.keyword.apiconnect_short}}](#man_migrate_api) para migrarla manualmente al nuevo servicio. 

6. Antes de cerrar la pantalla de la API original, inhabilite el control deslizante para **Exponer API gestionada**. Esto impide que cualquiera actúe en el punto final de la versión anterior.

### API de Cloud Foundry

1. Abra el origen de la API de Cloud Foundry existente en el panel de control de {{site.data.keyword.Bluemix_notm}}. 

2. Seleccione **Gestión de API** en el menú de navegación.

3. Seleccione **Definición** en la navegación.

4. Seleccione **Archivo de definición de API** > **Exportar a API Connect** > **Exportar API**. Si ya tiene un servicio de {{site.data.keyword.apiconnect_short}} existente, se migrará la API automáticamente al servicio existente. Si todavía no tiene un servicio de {{site.data.keyword.apiconnect_short}} configurado, se añadirá automáticamente el servicio con un plan Lite gratuito y migrará la API. Si la instancia no se ha podido suministrar, siga los pasos de [Migración manual de API a {{site.data.keyword.apiconnect_short}}](#man_migrate_api) para migrarla manualmente al nuevo servicio.
   
5. Una vez que el contenido se haya migrado a la instancia de {{site.data.keyword.apiconnect_short}}, seleccione el enlace que se proporciona para acceder a la versión migrada.
    **Importante:** Para evitar problemas con varias instancias de la API en ejecución, asegúrese de inhabilitar el control deslizante *Gestionar la API* en la versión original de la API.

6. Seleccione el separador **API** en la navegación.

7. Seleccione **Borradores** para ver la nueva API.

## Migración de API manualmente a {{site.data.keyword.apiconnect_short}}
{: #man_migrate_api}

Si el proceso para migrar la API al servicio de {{site.data.keyword.apiconnect_short}} no ha finalizado correctamente, realice los pasos siguientes para migrarla manualmente:

1. Abra la API.
	1. Inicie sesión en {{site.data.keyword.Bluemix_notm}}.
	2. Para una app de Cloud Foundry: 
		1. Seleccione **Panel de control** en el menú.
		2. Seleccione el nombre de la app de Cloud Foundry que desea migrar.
		3. Seleccione **Gestión de API** en la navegación.
	3. Para una acción de Cloud Functions: 
		1. Seleccione **Funciones** en el Menú.
		2. Seleccione **API** en la navegación.
		3. Seleccione el nombre de la API que desee migrar.
2. Descargue el documento Swagger correspondiente a la API desde gestión de API.
    1. Seleccione **Definición** en la navegación.
	2. Seleccione **Archivo de definición de API**.
    3. Seleccione **Exportar YAML** o **Exportar JSON**, dependiendo del tipo de archivo, para descargar la definición de la API. El archivo se descarga en la carpeta de descargas.
3. Cree y prepare la instancia de {{site.data.keyword.apiconnect_short}}. 
	1. Vaya a **API** en la navegación para filtrar los servicios.
	2. Seleccione el servicio de API Connect. 
    3. Cree una instancia del servicio {{site.data.keyword.apiconnect_short}} desde el catálogo de {{site.data.keyword.Bluemix_notm}}.
	4. Seleccione su plan. El plan Lite es la opción gratuita.
	5. Seleccione **Crear** para crear la instancia.
4. Importe el documento Swagger en la instancia de {{site.data.keyword.apiconnect_short}} siguiendo los pasos siguientes:
	1. En el panel de control del servicio {{site.data.keyword.apiconnect_short}}, seleccione **Ir a... (>>)** > **Borradores** en el menú.
	2. Seleccione el separador API.
	3. Seleccione **+Añadir** > **Importar API desde un archivo o URL**.
	4. Busque y seleccione el archivo Swagger que ha descargado desde gestión de API. Seleccione **Abrir**.
	5. Seleccione **Importar** para importar la API en el servicio {{site.data.keyword.apiconnect_short}}.
5. Para evitar problemas que resultan de la ejecución de varias instancias de la API, asegúrese de inhabilitar el control deslizante *Gestionar la API* en la versión original de la API.

La API está disponible en la instancia de servicio de {{site.data.keyword.apiconnect_short}}. 

## Publicar la API

Puede seguir publicando la API siguiendo estos pasos:

1. Cree un catálogo.
	1. Seleccione **+Añadir** para crear un catálogo.
	2. Especifique un nombre de visualización y un nombre para su catálogo y seleccione **Añadir**.
	3. Seleccione el catálogo que ha creado.
2. Especifique los valores para la API.
    1. Seleccione **Crear producto**.
	2. Especifique un nombre para el producto.
	2. Seleccione el producto que ha creado para ver sus valores.
	3. Defina el límite de tasa para la API.
	4. Defina el nivel para la API.
3. Añada el punto final para la API, si es necesario.
    1. Seleccione la API.
	2. Seleccione el separador Ensamblado.
	3. Añada el punto final, si aún no se ha especificado.
	
 Después de migrar las API, puede acceder a todas las características de gestión de API abriendo el mosaico del servicio {{site.data.keyword.apiconnect_short}} y desde el panel de control de {{site.data.keyword.Bluemix_notm}}. 

