---

copyright:
  years: 2017,2018
lastupdated: "2018-03-28"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Gestión de API
{: #manage_apis}

Después de integrar su API para que la gestione y supervise el sistema de gestión de API, puede ver y modificar los valores de la API. Si no ha integrado la API, debe integrarla siguiendo el procedimiento de [Creación de API desde acciones de {{site.data.keyword.openwhisk_short}}](manage_openwhisk_apis.html) o [Habilitación de puntos finales gestionados de API](manage_cf_apis.html). 

Para gestionar los valores de la API, siga los pasos siguientes:

Si ha creado una API nueva, y ya está abierta en la interfaz, puede omitir los tres primeros pasos.

1. Seleccione la API que desea gestionar desde el panel de control de {{site.data.keyword.Bluemix}} seleccionando una acción en el panel de control del servicio {{site.data.keyword.openwhisk_short}}, si la información sobre la API aún no se muestra.
2. Pulse **Gestión de API** en la navegación o seleccione el separador **API** si es una acción de {{site.data.keyword.openwhisk_short}}.
3. Seleccione la API que desea gestionar, si es necesario. Cuando se establezca una conexión, podrá ver y actualizar las selecciones siguientes:
    * Resumen
    * Definición
    * Compartición
    * Explorador de API
4. Seleccione el graduador Exponer API gestionadas para activarlo y exponer sus API. Nota: algunos de los valores no se pueden definir si la API no está expuesta.  

## Resumen de valores correspondientes a las API
{: #overview_api}

El separador Resumen se selecciona de forma predeterminada cuando se selecciona una API y está dividido en dos secciones:
* Propiedades - En la sección Propiedades, puede ver la información siguiente:
    * Información básica sobre la API
	* Políticas de seguridad
	* Información sobre la tasa límite
    * Detalles del uso compartido
* Sección Análisis y registro - En la sección Análisis y registro, puede ver las siguientes estadísticas:
	* Número de respuestas y tiempo medio de respuesta durante el último intervalo de tiempo especificado
    * Número de llamadas de API por minuto en formato gráfico
    * 100 últimas respuestas en la tabla Registro de respuestas
	
El gráfico *Respuestas* muestra una representación rápida del modo en que se recibe su API y un desglose del estado de las respuestas. Esto le puede ayudar a determinar si está recibiendo una mayoría de respuestas de error. Una mayoría de respuestas de error puede indicar que tiene más tráfico del que ha permitido en los valores de tasa. Puede ver un desglose numérico de las respuestas por código de respuesta pasando el puntero del ratón sobre el icono de información. Son comunes los siguientes códigos de respuesta:
* 200  Correcto
* 201  Creado
* 302  Encontrado
* 304  No modificado
* 400  Solicitud incorrecta
* 401  No autorizado
* 403  Prohibido
* 500  Error interno del servidor
* 503  Servicio no disponible

La tabla Registro de respuestas contiene detalles individuales de las 100 últimas respuestas. Puede clasificar la información de acuerdo con las entradas de una columna seleccionando la cabecera de la columna. Puede buscar entradas específicas en la tabla Registro de respuestas mediante la barra *Buscar respuestas*. Para ver más información sobre un suceso, selecciónelo o seleccione **Ver detalles** en la lista del menú de opciones (tres puntos verticales) que hay junto a la entrada.


## Edición de los valores de la API
{: #settings_api}

En el separador **Definición**, puede actualizar la información básica sobre la API. Esta información incluye documentación, nombre y URL base. Utilice la sección Seguridad y limitación de tasa para especificar un límite de llamadas y de intervalo para asegurarse de que solo se realicen una determinada cantidad de llamadas por segundo, por minuto o por hora. También puede hacer que se necesite autenticación para crear llamadas de API, con el fin de evitar un uso no deseado de sus datos o para obtener estadísticas sobre las API.

Para cambiar los valores correspondientes a una API, siga estos pasos:

1. En el panel de control de gestión de API, pulse el separador **Definición**.
2. Puede asignar un nombre o actualizar el nombre de la API e importar una definición de API en la sección Información de API.
3. En la sección Seguridad y limitación de tasa, puede actualizar las políticas siguientes:
    * Requerir clave de API- Especifica si la llamada de API sólo se puede procesar si se especifica la clave de API correcta. El valor predeterminado no requiere una clave adicional.
    * Método de seguridad - Cuando la opción Clave de API está seleccionada, especifica si para procesar la API solo se necesita la API de clave o si se necesita tanto la clave de API como el secreto de API.
    * Ubicación de la clave y el secreto de API - En función del valor correspondiente al método, especifica cómo se incluye la seguridad de API en la llamada. Los nombres de invocación especifican cómo se identifica la información de seguridad. Para obtener más información sobre cómo trabajar con claves y secretos, consulte [Gestionar claves y secretos](keys_secrets.html).
    * Limitar la tasa de llamadas de API - Establece el número de llamadas de API permitido durante un determinado intervalo de tiempo, con la opción de definirlo para cada clave. Tenga en cuenta que se utiliza un método burst-type (tipo de ráfaga) de limitación de tasa. La tasa media de llamadas de API se calcula durante el intervalo de tiempo total que especifique en la tasa. Si la tasa de llamadas de API durante un intervalo supera la tasa media de llamadas de API, podría haber un periodo de llamadas denegadas hasta alcanzar el límite de tiempo especificado en la tasa.   
    * Proveedor de OAuth - Garantiza que los usuarios con los parámetros de seguridad correctos puedan acceder a sus API, aplicando OAuth mediante credenciales de inicio de sesión social de proveedores como Google, Facebook, IBM App ID y GitHub.
	    **Nota:** Debe especificar una instancia de servicio App ID existente que esté configurada en {{site.data.keyword.Bluemix_notm}} para proporcionar los datos de identificación cuando utilice **App ID** como proveedor de OAuth. Si no tiene ningún servicio App ID existente, puede seleccionar **Crear** en la sección OAuth para crear uno en una nueva ventana y volver para especificarlo en la gestión de API. También puede seleccionar **Editar** para cambiar una instancia de servicio seleccionada.
4. Habilitar CORS - CORS (Cross-origin Requests) permite algunas solicitudes limitadas procedentes de otro dominio.
5. Pulse **Guardar**.

## Compartición de API
{: #share_api}

Puede compartir sus API con otros usuarios dentro o fuera de la organización de {{site.data.keyword.Bluemix_notm}}. 

Cuando comparte API con otros, dentro o fuera de su organización de {{site.data.keyword.Bluemix_notm}}, puede crear claves y secretos para sus API. Cada API gestionada permite 5 claves que se pueden crear y a asignar a dicha API. Si envía una clave exclusiva a un individuo o empresa, puede realizar un seguimiento de algunas estadísticas sobre el modo en que se utiliza la API. Por ejemplo, puede realizar un seguimiento del número de llamadas a la API realizadas por dicha persona o empresa. También puede inhabilitar una clave o limitar las llamadas desde una clave. Este puede resultar útil durante las pruebas, el equilibrio de la carga de trabajo, la supervisión o para resolver algunas situaciones de seguridad.

Una *clave* es una serie exclusiva de caracteres que está asociada con la API. Puede asignar más de una clave para una API, lo que le ayuda a realizar un seguimiento del uso de la API que hace cada cliente. Por ejemplo, dé una clave a un cliente, y otra clave a otro cliente. Cada vez que los clientes invoquen a la API, incluirán su clave asignada. Al realizar el seguimiento de dicha clave, sabrá qué cliente ha invocado la API.

Hay dos tipos de claves:

* Claves para compartir la API con los clientes que tienen acceso a la organización de {{site.data.keyword.Bluemix_notm}}. 
* Claves para compartir la API con los clientes que no tienen acceso a la organización de {{site.data.keyword.Bluemix_notm}}. 

Los distintos tipos de claves se crean, se mantienen y se suprimen de la misma forma. La única diferencia es quién puede utilizar las claves.

Después de crear una o varias claves para la API, puede limitar la tasa de llamadas a la API por clave. Al habilitar el control deslizante **Limitar velocidad de llamada de API por clave** en el separador *Definición*, el número de llamadas para cada clave que cree estará limitado al límite de tasa que establezca.   

Un *secreto* es similar a una clave, ya que se utiliza para mantener el acceso a la propia API. Un secreto es personalizable y se puede modificar sin cambiar la clave. No puede haber un secreto si no hay clave. Por ejemplo, solo alguien con el secreto correcto puede cargar una nueva versión de la API. Puede requerir una API y un secreto para las llamadas de API, o solo utilizar una clave. Los secretos pueden ser útiles si necesita cambiar el secreto, pero no desea cambiar la clave. 

1. En el panel de control de gestión de API, pulse el separador **Compartición**.
2. Dentro del área "Compartir dentro de la organización de {{site.data.keyword.Bluemix_notm}}", seleccione **Exponer API gestionada** si desea que la API esté disponible para otros usuarios con acceso a su organización de {{site.data.keyword.Bluemix_notm}}. Esta opción debe estar seleccionada para generar una clave.
3. Pulse **Crear clave de API** para crear una clave exclusiva para la API. Aparece el recuadro de diálogo Crear clave de API. La clave API se genera automáticamente.
4. Utilice la API clave para determinar qué usuario accede a la API mediante el envío al usuario de una clave exclusiva. La pasarela puede determinar qué clave (cliente) genera la llamada.
5. Pulse el icono **Menú** (tres puntos verticales) que hay junto a la clave para editar o suprimir esta clave de API.

En la sección Compartición fuera de la organización de {{site.data.keyword.Bluemix_notm}}, puede compartir su API con usuarios que no tengan una cuenta de {{site.data.keyword.Bluemix_notm}}. Este método para compartir proporciona un enlace directo para ver información acerca de la API en el Explorador de API. La API contiene un botón para ejecutar la API en la vista del Explorador de API. Para solicitar un enlace para la API, siga los pasos siguientes:

1. En la sección "Compartición fuera de la organización de {{site.data.keyword.Bluemix_notm}}", pulse **Crear clave de API**. Aparece el recuadro de diálogo Crear clave de API.
     Tenga en cuenta que el usuario tiene un secreto que usted no puede controlar.
2. Especifique un nombre exclusivo para la clave de API.
3. Seleccione **Crear clave**. 
4. Envíe el enlace del portal de la API al cliente que no tiene cuenta de {{site.data.keyword.Bluemix_notm}}. La clave y el secreto de la API (si se utiliza) se incluyen en el enlace, por lo que puede determinar qué clave ha generado el enlace.
  
El enlace a la documentación de la API abre la API en el separador **Explorador de API**.

Para obtener más información sobre cómo trabajar con claves y secretos, consulte [Gestionar claves y secretos](keys_secrets.html).

## Visualización y prueba con el Explorador de API
{: #explore_api}

Seleccione el separador Explorador de API para ver el HTML generado a partir del documento Swagger. 

El Explorador de API muestra todas las acciones de la API y la documentación que se aplica a la API. Puede ver las operaciones y las acciones y sus descripciones y probar la API desde la interfaz de usuario. También puede descargar el documento Swagger para reutilizar su contenido.

Para probar la API, siga los pasos siguientes:
1. *Ejemplos* está seleccionado de forma predeterminada. Muestra un ejemplo del código correspondiente a la API seleccionada.
2. Cambie el formato del ejemplo, si es necesario, seleccionando un lenguaje en el menú que se encuentra junto al lenguaje especificado. 
3. Seleccione **Probarlo**.
4. Seleccione **Llamar operación**. 

Se muestra la respuesta a la solicitud. 

## Dominios personalizados
{: #custom_domains}

En algunos ejemplos, puede que desee un dominio personalizado o dominio "de vanidad" en lugar del dominio predeterminado de la pasarela de la API. La capacidad de gestión de la API da soporte a las API frontales con dominios personalizados, siempre que el dominio esté registrado en su entorno de {{site.data.keyword.Bluemix_notm}}.

Siga los pasos siguientes para configurar inicialmente el dominio personalizado. Si ha completado anteriormente los pasos para configurar el dominio, consulte [Utilización de un dominio personalizado con las API](manage_apis.html#custom_domains_bind).

### Configuración

Para colocar un dominio personalizado enfrente de una API, registre en primer lugar el dominio con {{site.data.keyword.Bluemix_notm}}. Esto puede realizarse desde la pantalla de gestión de la organización:

1. Desde el selector de organización de la cabecera de {{site.data.keyword.Bluemix_notm}}, seleccione **Gestionar organizaciones**.
2. Localice la organización deseada en la que se debe registrar el dominio y seleccione **Ver detalles**.
3. Pulse el enlace **Editar organización** junto al nombre de la organización.
4. Seleccione el separador **Dominios**.
5. Pulse **Añadir dominio** y especifique el nombre de dominio.
6. Después de que el dominio aparezca en la lista, seleccione **Guardar** en la parte superior de la pantalla.
7. Cargue un certificado SSL para este dominio. Esto puede hacerse seleccionando el icono **Cargar** junto al nombre de dominio. Tanto el certificado público como la clave privada correspondiente son necesarios.  
	**Notas:**
	* La pasarela de gestión de la API solo soporta el tráfico en el protocolo HTTPS, por lo que se debe proporcionar un certificado SSL.
	* Las cuentas de prueba de {{site.data.keyword.Bluemix_notm}} están limitadas a un único certificado SSL por organización. Si se necesitan más certificados, debe actualizar la cuenta a un nivel de pago o de suscripción.
	* Si tiene previsto utilizar uno o varios subdominios para el tráfico de la API, se necesitará un certificado de comodines o un certificado que contenga los SAN (*Subject Alternative Names*) deseados.
8. Configure los valores de DNS del dominio. 
9. Cree un registro de CNAME para el dominio que se dirige a uno de los siguientes puntos finales seguros en función de la región que aloja la API de destino:
	- **EE.UU. sur:** secure.us-south.bluemix.net.
	- **Reino Unido:** secure.eu-gb.bluemix.net.
	- **Frankfurt:** secure.eu-de.bluemix.net.
	- **Sídney:** secure.au-syd.bluemix.net.

### Utilización de un dominio personalizado con las API
{: #custom_domains_bind}

Una vez que se haya completado la configuración inicial, enlace una o varias API al dominio registrado desde la sección **Definición** de la API siguiendo los pasos siguientes:
1. En *Aspectos básicos de la API*, seleccione el menú Dominio de la API, y elija un dominio personalizado desde los dominios que ha configurado en los pasos anteriores.

2. Opcional: Proporcione un subdominio exclusivo para esta API.
	**Nota**: Para utilizar un subdominio, el certificado SSL que se ha cargado en el Paso 7 de `Configuración` debe contener una configuración de comodines válida *o* cada subdominio debe estar listado como un SAN (Subject Alternative Name).

3. Guarde la API. Los valores de dominio pueden tardar varios minutos en convertirse en activos.

Para obtener más información, consulte:
[Gestión de dominios](../admin/manageorg.html#managedomains) o
[Creación y utilización de un dominio personalizado](../manageapps/updapps.html#domain).
