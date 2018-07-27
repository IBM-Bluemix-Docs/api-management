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

# Ejecutar mandatos con la CLI de gestión de API
{: #apim-cli-over}

Puede utilizar la CLI de gestión de API de {{site.data.keyword.Bluemix_notm}} para completar algunas de las mismas tareas con la línea de mandatos que puede completar con la interfaz gráfica de usuario de {{site.data.keyword.Bluemix_notm}}. Los mandatos pueden especificarse individualmente en una ventana de terminal o invocarse en una secuencia de un script.
{:shortdesc}

## Requisitos previos
{: #apim-cli-script-prereq}

Antes de poder utilizar la CLI de gestión de API, debe haber completado los pasos siguientes:

* Obtenga un [ID de Bluemix](../../admin/adminpublic.html#signing-up-for-bluemix){: new_window}. 
* Descargue e instale la [línea de mandatos de Bluemix](../../cli/reference/bluemix_cli/index.html#getting-started){: new_window}.
* Instale el {{site.data.keyword.Bluemix_notm}} [plug-in de línea de mandatos de gestión de la API](../../cli/reference/bluemix_cli/index.html#install_plug-in){: new_window}.
* [Inicie sesión](../../cli/reference/bluemix_cli/bx_cli.html){: new_window} en la línea de mandatos de {{site.data.keyword.Bluemix_notm}}.

## Ejemplo de secuencia de CLI de mandatos para una API

Los pasos siguientes muestran un ciclo completo de mandatos de gestión de API de añadir una pasarela a una API a eliminar la pasarela de la API:

1. Iniciar la sesión en {{site.data.keyword.Bluemix_notm}} 
    ```
    bluemix login -a https://api.ng.bluemix.net -c account_ID (1) -u username -p password
    ```
    {:codeblock}
    Se inicia sesión en su organización de {{site.data.keyword.Bluemix_notm}} predeterminada con la interfaz de línea de mandatos.

2. Mostrar las API
    ```
    bluemix apim apis
    ```
    {:codeblock}
    Muestra las API en su organización predeterminada.

3. Crear una API
    ```
    bluemix apim api-create --name <API_NAME> --file <path_to_Swagger_file>
    ```
    {:codeblock}
    Utiliza el archivo Swagger para crear una API gestionada desde la API que especifique en la organización de {{site.data.keyword.Bluemix_notm}}.

4. Actualizar una definición de API existente
    ```
    bluemix apim api-update --name <API_NAME> --file <path_to_new_Swagger_file>
    ```
    {:codeblock}
    Sustituye la definición existente de la API que especifique con la nueva definición de archivo Swagger.

5. Exponer la API
    ```
    bluemix apim api-expose --name <API_NAME>
    ```
    {:codeblock}
    Expone la API.

6. Compartir la API
    ```
    bluemix apim api-share --name <API_NAME>
    ```
    {:codeblock}
    Comparte la API con terceros fuera de la organización de {{site.data.keyword.Bluemix_notm}}.

7. Dejar de exponer la API
    ```
    bluemix apim api-unexpose --name <API_NAME>
    ```
    {:codeblock}
    Detiene la compartición de la API fuera de la organización de {{site.data.keyword.Bluemix_notm}}.

8. Mostrar las claves para la API
    ```
    bluemix apim keys --name <API_NAME>
    ```
    {:codeblock}
    Muestra las claves asociadas con la API, si las hay.

9. Dejar de compartir la API
    ```
    bluemix apim api-unshare --name <API_NAME>
    ```
    {:codeblock}
    Detiene la compartición de la API.
	
10. Eliminar la API
    ```
    bluemix apim api-delete --name <API_NAME>
    ```
    {:codeblock}
    Elimina la pasarela de la API. Ya no está gestionada.
    Importante: Si suprime una API de Cloud Foundry, la app de Cloud Foundry base permanece en el servicio de {{site.data.keyword.Bluemix_notm}}, pero ya no está gestionada. Una API de OpenWhisk suprimida elimina todas las interacciones entre las acciones individuales de OpenWhisk. Una vez que se suprima la API de OpenWhisk, debe volver a crearse si desea utilizarla de nuevo.
    
Consulte [Mandatos de la interfaz de línea de mandatos](../../cli/plugins/api-management-cliplugin/index.html) para obtener la lista completa de mandatos de gestión de la API y sus opciones.

