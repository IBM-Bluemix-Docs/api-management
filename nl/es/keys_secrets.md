---

copyright:
  years: 2017
lastupdated: "2017-11-09"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Gestionar claves y secretos
{: #keys_secrets}

Cuando las API están gestionadas por la gestión de API, puede utilizar claves y secretos para controlar el acceso a las API.

## Creación de una clave y secreto
{: #create_key_secret}

Para añadir una clave para la API, siga los pasos siguientes:

1. Abra la aplicación de Cloud Foundry o la API de OpenWhisk, si no está ya abierta.

2. Seleccione *Gestión de API* en la navegación.

3. Seleccione el separador de Compartición y claves para acceder a las claves para dicha aplicación o API. *Nota: No puede ver los separadores hasta que guarde la aplicación o la API por primera vez.*

4. Asegúrese de que el control deslizante **Exponer API gestionada** esté establecido en la posición *on*. La API debe estar expuesta para poder asignar claves.

5. Cree una clave para un cliente que tenga acceso a su organización de {{site.data.keyword.Bluemix_notm}}.
  1. Seleccione **Crear clave de API +** en la sección *Compartir dentro de la organización de {{site.data.keyword.Bluemix_notm}}*. Una clave y un secreto se crean automáticamente y se introducen en los campos correctos. No puede actualizar la clave ni el secreto para este tipo de clave. 
  2. Especifique un nombre para la clave y secreto para ayudarle a identificarlo. Por ejemplo, el nombre del cliente que la utilizará.
  3. Seleccione **Guardar** para guardar la nueva clave.
  4. Puede repetir los pasos *a* a *c* para obtener claves adicionales, si es necesario. Puede tener un máximo de 5 claves en esta sección por API.

6. Cree una clave para un cliente que no es un miembro de la Organización de {{site.data.keyword.Bluemix_notm}}.
  1. Seleccione **Crear clave de API +** en la sección *Compartir fuera de la organización de {{site.data.keyword.Bluemix_notm}}*. Una clave se crea automáticamente y se introduce en el campo correcto. No hay ningún secreto que se muestre inicialmente para este tipo de clave. No puede actualizar la clave. 
  2. Especifique un nombre para la clave para que le ayude a identificarla. Por ejemplo, el nombre del cliente que la utilizará.
  3. Opcional: Si desea añadir un secreto a la clave, seleccione el **Enlace con portal de la API** para la clave a la que desee añadir el secreto y seleccione **Establecer secreto de API**.
  4. Seleccione **Guardar** para guardar la nueva clave.
  5. Puede repetir los pasos *a* a *d* para obtener claves adicionales, si es necesario. Puede tener un máximo de 5 claves en esta sección por API.
Las claves se enumeran para la API cuando está seleccionado el separador Compartición y claves.

## Especificación de una clave y un secreto en una llamada de API
{: #spec_key_secret}

Los clientes solo pueden llamar a la API si incluyen la clave correcta, el secreto correcto, o ambos, en la cabecera de la llamada. Para llamar a la API, deben incluir la clave y el secreto en la llamada a la API como se muestra en el ejemplo siguiente:
```
curl --request PUT \
  --url https://appidtest.mybluemix.net/ \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --header 'x-ibm-client-secret: add_secret_here' \
  --data '{"id":999999999999999}'
```
{: codeblock}
Donde *add_secret_here* se sustituye por el secreto de la clave correcta. 

## Supresión de una clave de API
{: #delete_key}

En algún momento, deseará eliminar una clave. Puede que un cliente que utilizara la API cree su propia API y ya no necesite la suya. Para garantizar que ninguno de sus clientes siga utilizando la API, puede suprimir la clave. Para suprimir una clave del servicio, siga los pasos siguientes:

1. Abra la aplicación de Cloud Foundry o la API de OpenWhisk, si no está ya abierta.

2. Seleccione *Gestión de API* en la navegación.

3. Seleccione el separador *Compartición y claves*.

4. Busque la clave que desea suprimir. Sugerencia: Aquí es cuando es útil poner un nombre a las claves para que se identifiquen fácilmente.

5. Seleccione el icono de opciones, que es tres puntos verticales, junto a la clave que desea suprimir. 

6. Seleccione **Suprimir clave**.

7. Confirme la supresión para eliminar la clave.
