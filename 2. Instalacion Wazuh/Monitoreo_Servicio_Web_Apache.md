# Monitoreo de Servicios

## Apache Web Server

Para monitorear servicios web en plataformas como **Apache**, basta con realizar la instalacion del agente de wazuh en dicho sistema [Ver...](https://github.com/hernandopena/Wazuh/blob/a1f9b4870ffc4d6ff81a4ab6dcd14e9dd4281ece/2.%20Instalacion%20Wazuh/Registro_Agente_Linux.md)

y Realizar los ajustes en su configuracion, para que realice la ingesta de los Logs generados por el servicio, esto nos permitira identificar peticiones no deseadas, inyecciones y ataques comunes en aplicaciones web.

## Verificiacion de los logs ingestados por el agente 

Para verificar cuales son los origentes de logs que estan siendo entregados por cada uno de los agentes de wazuh, podemos consultarlo desde la consola de aenres, haciendo click sobre el agente que vamos a veriricar.

Agente_ver_logs_1

Al hacer click sobre el agente, nos desplegara la informacion recolectada y que es procesada de acuerdo a los modulos cargaso o componentes configurados; en esta ventana, vamos a hacer click en la opcion **Configuracion** que se encuentra en la esquina superior derecha.

Agente_ver_logs_2

Ahora nos presentara todas las opciones para realizar configuracion del agente, y nos vamos a dirigir al grupo titulado: **Log data analysis** y entre sus opciones vamos a seleccionar: **Log Collection**.

Agente_ver_logs_3

Este modulo, nos permite consultar todas las fuentes de datos provenientes del agente y la ruta desde donde se consultan.

Agente_ver_logs_4

Y podremos consultar los logs del servidor web para los correspondientes analisis.

Agente_ver_logs_5

## Como bloquear trafico entrante





 

------------------------------------------------


,  Para agregar un agente (Dispositivo, servidor, máquina virtual), se debe de dirigir al menú **Agentes**

![Acceso a menú Agentes](https://github.com/hernandopena/Wazuh/blob/974cd436841b3a41840e771cb3a3393a4289ad4e/2.%20Instalacion%20Wazuh/imagenes/Menu_Agentes.jpg)

Al ingresar a este módulo, podremos seleccionar la opción **Deploy a new agent**, como se presenta a continuación

![Opción nuevo Agentes](https://github.com/hernandopena/Wazuh/blob/974cd436841b3a41840e771cb3a3393a4289ad4e/2.%20Instalacion%20Wazuh/imagenes/Opcion_nuevo_agente.jpg)

El cual nos presentara un asistente, mediante el cual podremos establecer las características de este nuevo agente, empezando por el sistema operativo

![Selección Sistema Operativo](https://github.com/hernandopena/Wazuh/blob/7f8ac032d6f7de9d09b21e56101388e88a1cb133/2.%20Instalacion%20Wazuh/imagenes/Nuevo_agente_win_1.jpg)

A continuación, y dependiendo de la opción anteriormente seleccionada, podremos seleccionar la versión del sistema operativo de este agente, en este caso vamos a instalar en un sistema windows 10

![Selección versión del Sistema Operativo](https://github.com/hernandopena/Wazuh/blob/7f8ac032d6f7de9d09b21e56101388e88a1cb133/2.%20Instalacion%20Wazuh/imagenes/Nuevo_agente_win_2.jpg)

A continuación, podremos seleccionar la arquitectura del mismo

![Selección Arquitectura del Sistema Operativo](https://github.com/hernandopena/Wazuh/blob/7f8ac032d6f7de9d09b21e56101388e88a1cb133/2.%20Instalacion%20Wazuh/imagenes/Nuevo_agente_win_3.jpg)

A continuación, en el paso 4, debemos informar, cual es la dirección IP del servidor principal de wazuh o el nodo al que se conectara este agente

![Informacion del Servidor de Wazuh](https://github.com/hernandopena/Wazuh/blob/974cd436841b3a41840e771cb3a3393a4289ad4e/2.%20Instalacion%20Wazuh/imagenes/Nuevo_agente_4.jpg)

En el siguiente paso 5, debemos de informar el nombre del agente y podremos clasificarlo mediante grupos que hayamos definido previamente (si aún no se definen los grupos, estos se pueden generar en el menú de wazuh y asignar posteriormente)

![Nombre del Agente y Grupos](https://github.com/hernandopena/Wazuh/blob/7f8ac032d6f7de9d09b21e56101388e88a1cb133/2.%20Instalacion%20Wazuh/imagenes/Nuevo_agente_win_5.jpg)

A continuación, nos presentara un comando que debemos de copiar y ejecutar en una consola de comandos PowerShell de nuestro agente a registrar con privilegios de administrador, mediante un usuario con privilegios, el ejemplo del comando es:

````
Invoke-WebRequest -Uri https://packages.wazuh.com/4.x/windows/wazuh-agent-4.4.1-1.msi -OutFile ${env:tmp}\wazuh-agent.msi; msiexec.exe /i ${env:tmp}\wazuh-agent.msi /q WAZUH_MANAGER='192.168.1.100' WAZUH_REGISTRATION_SERVER='192.168.1.100' WAZUH_AGENT_GROUP='Windows' WAZUH_AGENT_NAME='ESTACION-01'
````

![Comando para instalacion](https://github.com/hernandopena/Wazuh/blob/7f8ac032d6f7de9d09b21e56101388e88a1cb133/2.%20Instalacion%20Wazuh/imagenes/Nuevo_agente_win_6.jpg)

Finalmente, si la instalación se ejecutó exitosamente, podremos configurar el servicio para que se inicie cada vez que arranca el sistema, así como iniciar el agente inmediatamente, con la ayuda de los siguientes comandos:

```
NET START WazuhSvc
```

![Comando iniciar el agente y configurar su arranque automatico](https://github.com/hernandopena/Wazuh/blob/a1f9b4870ffc4d6ff81a4ab6dcd14e9dd4281ece/2.%20Instalacion%20Wazuh/imagenes/Nuevo_agente_win_7.jpg)

Con lo anterior, ya podremos visualizar en el listado de agentes, que este ya aparece registrado y se encuentra en línea y reportando informacion.

![Verificación de instalación del agente en la plataforma de Wazuh](https://github.com/hernandopena/Wazuh/blob/a1f9b4870ffc4d6ff81a4ab6dcd14e9dd4281ece/2.%20Instalacion%20Wazuh/imagenes/Nuevo_agente_win_8.jpg)



A partir de este momento, ya podemos comenzar a realizar las configuraciones necesarias y que se ajustes a nuestros sistemas para realizar el correspondiente monitoreo.