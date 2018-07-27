---



copyright:

  years: 2017
lastupdated: "2017-06-26"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

# Mandatos de gestión de API de Bluemix
{: #apimgt_cli}

Versión: 1.0.0

Puede instalar el plug-in de la interfaz de línea de mandatos (CLI) de gestión de la API de {{site.data.keyword.Bluemix_notm}} para completar acciones de gestión comunes en sus API con scripts. La información siguiente muestra los mandatos que se incluyen con el plug-in de CLI de gestión de la API, incluidos sus nombres, opciones, uso, requisitos previos, descripciones y ejemplos.
{:shortdesc}

**Nota:** **Requisitos previos** lista las acciones que son necesarias antes de utilizar el mandato. Los mandatos que no requieren acciones
previas aparecen en la lista como **Ninguno**. De lo contrario, los requisitos previos pueden incluir una o varias de las acciones siguientes:

**Nota:** Puede utilizar el formato corto de mandatos bluemix; por ejemplo, `bx apim` es la abreviatura de `bluemix apim`.

Utilice los índices de la tabla siguiente para referirse a los mandatos de gestión de la API utilizados frecuentemente.

<table summary="Mandatos de gestión de la API.">
<caption>Tabla 1. Mandatos de gestión de la API</caption>
 <thead>
 <th colspan="5">Mandatos de gestión de la API</th>
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
 
  
## Ayuda de gestión de la API
{: #apim_help}
Mostrar la ayuda general para mandatos incorporados de primer nivel y espacios de nombres soportados de la CLI de gestión de API, o la ayuda para un espacio de nombres o mandato incorporado específico.

### Sintaxis

```
bluemix apim help <object-action>
```
{: codeblock}

### Opciones de mandatos

   <dl>
   <dt>object-action (opcional)</dt>
   <dd>El mandato para el que se muestra la ayuda. Si no se especifica, se mostrará la ayuda general para la CLI de gestión de la API.</dd>
   </dl>

### Ejemplos

Mostrar la ayuda general para la CLI de gestión de la API:

```
bluemix apim help
```

Mostrar la ayuda para el mandato `api-create`:

```
bluemix apim help api-create
```



## bluemix apim api
{: #apim_api}
Mostrar las propiedades de una API gestionada.

### Sintaxis
```
bluemix apim api --name <API_NAME> [--swagger]
```
{: codeblock}

### Distintivo necesario
   <dl>
   <dt>--name</dt>
   <dd>Especifica el nombre de la API gestionada</dd>
   </dl>


### Opciones de mandatos
   <dl>
   <dt>--swagger</dt>
   <dd>Muestra la información del documento de definición de Open API en la salida</dd>
   </dl>

### Salida

El mandato genera una tabla que muestra la siguiente información sobre la API especificada:

   <dl>
     <dt>Nombre</dt>
	 <dd>El nombre de la API.</dd>
	 <dt>Tipo</dt>
	 <dd>El tipo de API. Las entradas válidas son <em>whisk</em>, <em>cf-apps</em> o <em>user-defined</em></dd>
	 <dt>Gestionado</dt>
	 <dd>Si el valor es true, indica que el punto final se ha descubierto pero no se ha expuesto en la pasarela.</dd>
	 <dt>Expuesto</dt>
	 <dd>Indica si la API está activa en la pasarela (<em>true</em>), o no (<em>false</em>).
	 <dt>Compartido</dt>
	 <dd>Indica si la API se comparte fuera de su organización Bluemix (<em>true</em>) o no (<em>true</em>).</dd>
	 <dt>URL gestionado</dt>
	 <dd>Especifica la ubicación de la versión compartida de la API.</dd>
   </dl>

   
### Ejemplos

Visualizar las propiedades de la API denominada cloudfound1:

```
bluemix apim api cloudfound1
```

Visualizar las propiedades y la definición del contenido de archivos para la API denominada api2:

```
bluemix apim api api2 --swagger
```


## bluemix apim apis
{: #apim_apis}


Lista de las API que están disponibles e identificadas en el servidor de punto final identificado.

### Sintaxis
```
bluemix apim apis [--api-provider <API_PROVIDER>][--exposed][--shared]
```
{: codeblock}

### Opciones de mandatos

Nota: Si no se especifican opciones, la información para todas las API se devolverá.
   <dl>
   <dt>--api-provider </dt>
   <dd>Solo devuelve los tipos de API que especifique aquí. Las opciones válidas son <em>whisk</em> para API de Openwhisk, <em>cf-apps</em> para API de apps de Cloud Foundry, y <em>user-defined</em> para API no asociadas con Openwhisk ni Cloud Foundry.</dd>
   <dt>--exposed</dt>
   <dd>Solo devuelve las API que están expuestas.</dd>
   <dt>--shared</dt>
   <dd>Solo devuelve las API que se comparten fuera de la organización de {{site.data.keyword.Bluemix_notm}}.</dd>
   </dl>

### Salida

El mandato genera una tabla que muestra la siguiente información sobre las API especificadas:

   <dl>
     <dt>Nombre</dt>
	 <dd>El nombre de la API.</dd>
	 <dt>Tipo</dt>
	 <dd>El tipo de API. Las entradas válidas son <em>whisk</em>, <em>cf-apps</em> o <em>user-defined</em></dd>
	 <dt>Gestionado</dt>
	 <dd>Si el valor es true, indica que el punto final se ha descubierto pero no se ha expuesto en la pasarela.</dd>
	 <dt>Expuesto</dt>
	 <dd>Indica si la API está activa en la pasarela (<em>true</em>), o no (<em>false</em>).
	 <dt>Compartido</dt>
	 <dd>Indica si la API se comparte fuera de su organización Bluemix (<em>true</em>) o no (<em>false</em>).</dd>
	 <dt>URL gestionado</dt>
	 <dd>Especifica la ubicación de la versión compartida de la API si la API se expone. El valor es <em>undefined</em> cuando la API no está expuesta. </dd>
   </dl>


### Ejemplos

Devolver todas las API que están disponibles en el gestor de puntos finales:

```
bluemix apim apis 
```

Devolver todas las API de OpenWhisk que están disponibles:

```
bluemix apim apis --api-provider whisk
```

## bluemix apim api-create
{: #apim_api-create}


Convierte una API no gestionada existente en una API gestionada importando su archivo Swagger.

### Sintaxis

```
bluemix apim api-create --name <API_NAME> --file <PATH_TO_OPEN_API_DEFINITION_FILE> --provider cf-apps [--expose]
```
{: codeblock}

### Distintivos necesarios

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Especifica el nombre de la API que desea gestionar.</dd>
   <dt>--file</dt>
   <dd>Proporciona la vía de acceso al archivo de definición de la Open API, que está en formato YAML o JSON.</dd>
   <dt>--provider</dt>
   <dd>Especifica el tipo de API que está creando. Nota: La única entrada válida para esto es <em>cf-apps</em>.
   </dl>

### Opción de mandato

   <dl>
   <dt>--expose</dt>
   <dd>Exponer el punto final automáticamente después de crearlo.</dd>
   </dl>

### Salida

El mandato genera la siguiente información:
* Se ha creado satisfactoriamente
* Error (con descripción del error)

### Ejemplos

Gestionar una API de Cloud Foundry denominada apinumber1 que tenga un archivo de definición yaml denominado reservations1:

```
bluemix apim api-create --name apinumber1 --file ~/dev/apis/reservations1.yaml --provider cf-apps
```

Gestionar una app de Cloud Foundry denominada cfapi que tiene un archivo de definición json denominado definition1:

```
bluemix apim api-create --name cfapi --file ~/dev/apis/definition1.json --provider cf-apps
```

## bluemix apim api-delete
{: #apim_api-delete}

Elimina una API gestionada de la base de datos.

### Sintaxis

```
bluemix apim api-delete --name <API_NAME> --confirm
```
{: codeblock}

### Distintivos necesarios

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Especifica el nombre de la API que desea suprimir. **Importante:** La supresión de una API de Cloud Foundry elimina la API del estado gestionado, pero la app de Cloud Foundry no se suprime. La supresión de una API de OpenWhisk suprime toda la API, y debe volver a crearse una vez que se suprima.</dd>
   <dt>--confirm</dt>
   <dd>Confirma que el mandato debe completarse sin proporcionar una solicitud de confirmación.</dd>
   </dl>


### Salida

El mandato genera la siguiente información:
* Suprimido correctamente
* Error (con descripción del error)

### Ejemplos

Suprimir la API de Cloud Foundry cloudapi1:

```
bluemix apim api-delete --name cloudapi1 --confirm
```


## bluemix apim api-expose
{: #apim_api-expose}

Convierte a la API gestionada en visible para terceros dentro de mi organización de {{site.data.keyword.Bluemix_notm}}.

### Sintaxis
```
bluemix apim api-expose --name <API_NAME>
```
{: codeblock}

### Distintivo necesario

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Especifica el nombre de la API que desea exponer.</dd>
   </dl>

### Salida

El mandato genera la siguiente información:
* Expuesto correctamente
* Error (con descripción del error)

### Ejemplo

Exponer una API de Cloud Foundry denominada cloudfound1 con mi organización de {{site.data.keyword.Bluemix_notm}}:

```
bluemix apim api-expose --name cloudfound1
```


## bluemix apim api-share
{: #apim_api-share}


Convierte a una API gestionada en visible para terceros fuera de mi organización de {{site.data.keyword.Bluemix_notm}}.

### Sintaxis
```
bluemix apim api-share --name <API_NAME>
```
{: codeblock}

### Distintivo necesario

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Especifica el nombre de la API que desea compartir.</dd>
   </dl>

### Salida

El mandato genera la siguiente información:
* Se ha compartido satisfactoriamente
* Error (con descripción del error)

### Ejemplo

Compartir una API de Cloud Foundry denominada cloudfound1 fuera de mi organización de {{site.data.keyword.Bluemix_notm}}:
```
bluemix apim api-share --name cloudfound1
```


## bluemix apim api-unexpose
{: #apim_api-unexpose}


Convierte a una API gestionada que está visible para terceros dentro de su organización de {{site.data.keyword.Bluemix_notm}} en no visible para terceros.

### Sintaxis
```
bluemix apim api-unexpose --name <API_NAME>
```
{: codeblock}

### Distintivo necesario

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Especifica el nombre de la API que desea eliminar de la visibilidad de terceros en su organización de {{site.data.keyword.Bluemix_notm}}.</dd>
   </dl>

### Salida

El mandato genera la siguiente información:
* No expuesto correctamente
* Error (con descripción del error)

### Ejemplo

Eliminar una API de OpenWhisk denominada openwhisk1 de la vista a otros miembros de mi organización de {{site.data.keyword.Bluemix_notm}}:

```
bluemix apim api-unexpose --name openwhisk1
```


## bluemix apim api-unshare
{: #apim_api-unshare}


Elimina una API gestionada que está visible para terceros fuera de mi organización de {{site.data.keyword.Bluemix_notm}} de visibilidad.

### Sintaxis
```
bluemix apim api-unshare --name <API_NAME>
```
{: codeblock}

<strong>Distintivo necesario</strong>:

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Especifica el nombre de la API que desea dejar de compartir.</dd>
   </dl>

### Salida

El mandato genera la siguiente información:
* No compartido correctamente
* Error (con descripción del error)

### Ejemplo

Dejar de compartir una API de Cloud Foundry denominada cloudfound1 fuera de mi organización de {{site.data.keyword.Bluemix_notm}}:

```
bluemix apim api-unshare --name cloudfound1
```



## bluemix apim api-update
{: #apim_api-update}


Actualiza los valores de una API gestionada sustituyendo su archivo de definición. Importante: Esta es una sustitución completa de las definiciones existentes en la API con las definiciones en el archivo nuevo. Se eliminará de la definición cualquier entrada vacía o faltante del archivo nuevo que exista en el archivo existente.

### Sintaxis
```
bluemix apim api-update --name <API_NAME> --file <NEW_OPEN_API_DEFINITION_FILE>
```
{: codeblock}

### Distintivos necesarios

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Especifica el nombre de la API que desea actualizar.</dd>
   <dt>--file</dt>
   <dd>Proporciona la vía de acceso al archivo de definición de Open API de sustitución, que está en formato YAML o JSON.</dd>
   </dl>

### Salida

El mandato genera la siguiente información:
* Actualizado correctamente
* Error (con descripción del error)


### Ejemplo

Actualizar una API de OpenWhisk denominada whiskapi1 con un archivo de definición con el nombre definition1.json:

```
bluemix apim api-update --name whiskapi1 --filePath ~/path/definitions/definition1.json
```


## bluemix apim keys
{: #apim_api-keys}


Muestra las propiedades de claves asociadas con una API gestionada.

### Sintaxis
```
bluemix apim api-keys --name <API_NAME> --bluemix|--external
```
{: codeblock}

### Distintivos necesarios

   <dl>
   <dt>--name <i>API_NAME</i></dt>
   <dd>Especifica el nombre de la API que desea exponer.</dd>
   <dt>--bluemix</dt>
   <dd>Lista las claves de API de {{site.data.keyword.Bluemix_notm}} para la API especificada.</dd>
   <dt>--external</dt>
   <dd>Lista las claves de API externas para la API especificada.</dd>
   </dl>

### Salida

El mandato genera una tabla que muestra la siguiente información sobre las API especificadas:


   <dl>
     <dt>Nombre de clave</dt>
	 <dd>El nombre de la clave de API.</dd>
	 <dt>Tipo de clave</dt>
	 <dd>El tipo de clave de API. Las entradas válidas son <em>bluemix</em> y <em>external</em>.</dd>
	 <dt>ID de cliente</dt>
	 <dd>El nombre del cliente identificado con la clave.</dd>
	 <dt>Secreto proporcionado</dt>
	 <dd>Indica si el secreto de la API se proporciona para la API. Los valores posibles son <em>true</em> si hay un secreto, y <em>false</em> si no lo hay.
   </dl>


### Ejemplos

Devolver todas las claves externas asociadas con la API denominada cloudfound1.

```
bluemix apim --name cloudfound1 --external
```

Devolver las claves que permiten a las personas dentro de mi organización de {{site.data.keyword.Bluemix_notm}} ver mi API denominada myapi1.

```
bluemix apim --name myapi1 --bluemix 
```
 
