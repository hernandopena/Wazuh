# Registro de Agentes

## Agente Windows 10

Para agregar un agente (Dispositivo, servidor, máquina virtual), se debe de dirigir al menú **Agentes**

![Acceso a menú Agentes](https://github.com/hernandopena/Wazuh/blob/974cd436841b3a41840e771cb3a3393a4289ad4e/2.%20Instalacion%20Wazuh/imagenes/Menu_Agentes.jpg)

Al ingresar a este módulo, podremos seleccionar la opción **Deploy a new agent**, como se presenta a continuación

![Opción nuevo Agentes](https://github.com/hernandopena/Wazuh/blob/974cd436841b3a41840e771cb3a3393a4289ad4e/2.%20Instalacion%20Wazuh/imagenes/Opcion_nuevo_agente.jpg)

El cual nos presentara un asistente, mediante el cual podremos establecer las características de este nuevo agente, empezando por el sistema operativo

![Selección Sistema Operativo](https://github.com/hernandopena/Wazuh/blob/974cd436841b3a41840e771cb3a3393a4289ad4e/2.%20Instalacion%20Wazuh/imagenes/Nuevo_agente_1.jpg)

A continuación, y dependiendo de la opción anteriormente seleccionada, podremos seleccionar la versión del sistema operativo de este agente

![Selección versión del Sistema Operativo](https://github.com/hernandopena/Wazuh/blob/974cd436841b3a41840e771cb3a3393a4289ad4e/2.%20Instalacion%20Wazuh/imagenes/Nuevo_agente_2.jpg)

A continuación, podremos seleccionar la arquitectura del mismo

![Selección Arquitectura del Sistema Operativo](https://github.com/hernandopena/Wazuh/blob/974cd436841b3a41840e771cb3a3393a4289ad4e/2.%20Instalacion%20Wazuh/imagenes/Nuevo_agente_3.jpg)

A continuación, en el paso 4, debemos informar, cual es la dirección IP del servidor principal de wazuh o el nodo al que se conectara este agente

![Informacion del Servidor de Wazuh](https://github.com/hernandopena/Wazuh/blob/974cd436841b3a41840e771cb3a3393a4289ad4e/2.%20Instalacion%20Wazuh/imagenes/Nuevo_agente_4.jpg)

En el siguiente paso 5, debemos de informar el nombre del agente y podremos clasificarlo mediante grupos que hayamos definido previamente (si aún no se definen los grupos, estos se pueden generar en el menú de wazuh y asignar posteriormente)

![Nombre del Agente y Grupos](https://github.com/hernandopena/Wazuh/blob/974cd436841b3a41840e771cb3a3393a4289ad4e/2.%20Instalacion%20Wazuh/imagenes/Nuevo_agente_5.jpg)

A continuación, nos presentara un comando que debemos de copiar y ejecutar en una consola de comandos de nuestro agente a registrar, mediante un usuario con privilegios, el ejemplo del comando es:

```
curl -so wazuh-agent.deb https://packages.wazuh.com/4.x/apt/pool/main/w/wazuh-agent/wazuh-agent_4.4.1-1_amd64.deb && sudo WAZUH_MANAGER='192.168.1.100' WAZUH_AGENT_GROUP='Servidores,Linux' WAZUH_AGENT_NAME='oculus' dpkg -i ./wazuh-agent.deb
```

![Comando para instalacion](https://github.com/hernandopena/Wazuh/blob/974cd436841b3a41840e771cb3a3393a4289ad4e/2.%20Instalacion%20Wazuh/imagenes/Nuevo_agente_6.jpg)

Finalmente, si la instalación se ejecutó exitosamente, podremos configurar el servicio para que se inicie cada vez que arranca el sistema, así como iniciar el agente inmediatamente, con la ayuda de los siguientes comandos:

```
sudo systemctl daemon-reload
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent
```

![Comando iniciar el agente y configurar su arranque automatico](https://github.com/hernandopena/Wazuh/blob/974cd436841b3a41840e771cb3a3393a4289ad4e/2.%20Instalacion%20Wazuh/imagenes/Nuevo_agente_7.jpg)

Con lo anterior, ya podremos visualizar en el listado de agentes, que este ya aparece registrado y se encuentra en línea y reportando informacion.

![Verificación de instalación del agente en la plataforma de Wazuh](https://github.com/hernandopena/Wazuh/blob/974cd436841b3a41840e771cb3a3393a4289ad4e/2.%20Instalacion%20Wazuh/imagenes/Nuevo_agente_8.jpg)



A partir de este momento, ya podemos comenzar a realizar las configuraciones necesarias y que se ajustes a nuestros sistemas para realizar el correspondiente monitoreo.