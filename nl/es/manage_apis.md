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

En algunos ejemplos, puede que desee un dominio personalizado o dominio "de vanidad" en lugar del dominio predeterminado de la pasarela de la API. La capacidad de gestión de la API da soporte a las API frontales con un nombre de dominio de su elección.

Siga los pasos siguientes para configurar inicialmente el dominio personalizado. Si ha completado anteriormente los pasos para configurar el dominio, consulte [Utilización de un dominio personalizado con las API](manage_apis.html#custom_domains_bind).

Los dominios personalizados no están aislados en una sola API, sino que abarcan un grupo de API definidas por:
- Servicio {{site.data.keyword.Bluemix_notm}} de origen (por ejemplo, {{site.data.keyword.openwhisk_short}})
- Espacio de Cloud Foundry

Por ejemplo, un dominio personalizado abarcaría todas las API de {{site.data.keyword.openwhisk_short}} creadas en el espacio "dev" de Cloud Foundry.

### Configuración

Para empezar, cree una nueva API en un servicio {{site.data.keyword.Bluemix_notm}} que admita la función de gestión de API integrada, o cree un proxy de API mediante la consola de API de {{site.data.keyword.Bluemix_notm}}.

#### Preparar certificados

Para registrar un dominio personalizado, se deben proporcionar certificados TLS válidos durante la configuración. Utilice el servicio de [Certificate Manager](../services/certificate-manager) para cargar un certificado y una clave privada.

*Nota: las invocaciones de API solo están disponibles mediante TLS (puerto 443). El HTTP sin formato no está soportado.*

### Utilización de un dominio personalizado con las API
{: #custom_domains_bind}

Una vez que se haya completado la configuración inicial, enlace una o varias API al dominio registrado desde la sección **Dominios personalizados** de la consola de API de {{site.data.keyword.Bluemix_notm}} siguiendo estos pasos:

1. En la lista de destinos disponibles, localice el servicio o el dominio predeterminado al que se debe adjuntar el dominio personalizado.
2. En un separador o ventana de navegador independiente, navegue a la página de valores del proveedor de DNS y cree un registro CNAME para el dominio deseado. Utilice el valor de la columna **Dominio predeterminado/Alias** en la página de gestión del dominio personalizado de {{site.data.keyword.Bluemix_notm}} como destino de CNAME, y luego guarde los valores de DNS.
  
    *Nota: Los cambios de DNS pueden tardar hasta 48 horas en propagarse, aunque los cambios se suelen producir antes de ese plazo.*
  
3. En la página de dominios personalizados, pulse los tres puntos de la fila que contiene el destino "dominio predeterminado" y seleccione **Editar** en el menú.
4. En el cuadro de diálogo resultante, marque el recuadro de selección **Asignar un dominio personalizado**.
5. Especifique el dominio personalizado deseado en el campo **Nombre de dominio** (por ejemplo, *api.mycompany.com*)
6. Copie el nombre de recurso de nube (CRN) de Certificate Manager del certificado que se ha cargado durante la configuración inicial.
7. Pegue el CRN que ha copiado en el campo **CRN de certificado**.
8. Pulse **Guardar**. El nombre de dominio especificado debe aparecer en la fila situada junto al dominio predeterminado, lo que indica que se ha aplicado correctamente.

*Nota: Antes de aplicar el dominio personalizado, el puntero de DNS será verificado para garantizar que el CNAME del dominio personalizado apunte al dominio predeterminado asociado con las API. Si la configuración de DNS no se ha completado o los cambios de DNS del paso 2 no se han propagado todavía, aparecerá un error y no se guardarán los valores del dominio. Si esto ocurre, inténtelo de nuevo periódicamente hasta 48 horas después de haber cambiado los valores de DNS. Si el error continúa pasadas 48 horas, verifique los valores de DNS o póngase en contacto con el equipo de soporte de {{site.data.keyword.Bluemix_notm}}.*
