# Monitoreo de Servicios

## Apache Web Server

Para monitorear servicios web en plataformas como **Apache**, basta con realizar la instalación del agente de wazuh en dicho sistema [Ver...](https://github.com/hernandopena/Wazuh/blob/a1f9b4870ffc4d6ff81a4ab6dcd14e9dd4281ece/2.%20Instalacion%20Wazuh/Registro_Agente_Linux.md)

y Realizar los ajustes en su configuración, para que realice la ingesta de los Logs generados por el servicio, esto nos permitirá identificar peticiones no deseadas, inyecciones y ataques comunes en aplicaciones web.


## Verificación de los logs ingestados por el agente 

Para verificar cuales son los orígenes de logs que están siendo entregados por cada uno de los agentes de wazuh, podemos consultarlo desde la consola de agentes, haciendo click sobre el agente que vamos a verificar.

![Seleccionar el agente](https://github.com/hernandopena/Wazuh/blob/304d4c4733cfb9f654778dec54ea7ee69b51a40b/2.%20Instalacion%20Wazuh/imagenes/Agente_ver_logs_1.jpg)

Al hacer click sobre el agente, nos desplegara la informacion recolectada y que es procesada de acuerdo a los módulos cargados o componentes configurados; en esta ventana, vamos a hacer click en la opción **Configuración** que se encuentra en la esquina superior derecha.

![Ir a configuracion](https://github.com/hernandopena/Wazuh/blob/304d4c4733cfb9f654778dec54ea7ee69b51a40b/2.%20Instalacion%20Wazuh/imagenes/Agente_ver_logs_2.jpg)

Ahora nos presentara todas las opciones para realizar configuración del agente, y nos vamos a dirigir al grupo titulado: **Log data analysis** y entre sus opciones vamos a seleccionar: **Log Collection**.

![Consultar las fuentes de informacion](https://github.com/hernandopena/Wazuh/blob/304d4c4733cfb9f654778dec54ea7ee69b51a40b/2.%20Instalacion%20Wazuh/imagenes/Agente_ver_logs_3.jpg)

Este módulo, nos permite consultar todas las fuentes de datos provenientes del agente y la ruta desde donde se consultan.

![Consultar los detalles de las fuentes de informacion](https://github.com/hernandopena/Wazuh/blob/304d4c4733cfb9f654778dec54ea7ee69b51a40b/2.%20Instalacion%20Wazuh/imagenes/Agente_ver_logs_4.jpg)

Y podremos consultar los logs del servidor web para los correspondientes análisis.

![Analizar la informacion recibida](https://github.com/hernandopena/Wazuh/blob/304d4c4733cfb9f654778dec54ea7ee69b51a40b/2.%20Instalacion%20Wazuh/imagenes/Agente_ver_logs_5.jpg)


## Como bloquear tráfico entrante

Si requerimos realizar bloqueos de tráfico a partir de un análisis de eventos identificados en la ingesta de informacion, podemos realizar la configuración para que  wazuh bloquee el acceso a esta informacion, a partir de modulo **active-response**, para lo cual requerimos:

En el servidor de wazuh realizar la configuración en el archivo **/var/ossec/etc/ossec.conf** y agregar las siguientes líneas:

```
<active-response>
    <command>firewall-drop</command>
    <location>local</location>
    <rules_id>31106</rules_id>
    <timeout>1800</timeout>
</active-response>
```
![Edición del bloqueo](https://github.com/hernandopena/Wazuh/blob/9386700cb5dbb13b6cc94b23c71062792790bf02/2.%20Instalacion%20Wazuh/imagenes/Agente_bloqueo_logs_1.jpg)

En donde:
```
- **<active-response>**: Instrucción para la ejecución de actividades a partir de una condición.
- **<command>firewall-drop</command>**: Instrucción para indicar que borre la peticion realizada por un usuario.
- **<location>local</location>**: Realiza la gestión en un agente (endpoint)
- **<rules_id>31106</rules_id>**: Indica sobre cuales acciones se aplicará estas acciones.
- **<timeout>1800</timeout>**: Tiempo en pausa, el cual puede ser usado para el desarrollo de alguna acción.
```

A continuación, podemos reiniciar el servidor de wazuh, con los comandos:

```
systemctl restart wazuh-manager 
```

Y en este momento, este tráfico ya está bloqueado

![Revisión del bloqueo](https://github.com/hernandopena/Wazuh/blob/9386700cb5dbb13b6cc94b23c71062792790bf02/2.%20Instalacion%20Wazuh/imagenes/Agente_bloqueo_logs_2.jpg)
