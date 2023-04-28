# Registro de Agentes

## Agente Linux (Ubuntu)

Para agregar un agente (Dispositivo, servidor, maquina virtual), se debe de dirigir al menu **Agentes**

IMG_MENU_AGENTES

Al ingresar a este modulo, podremos seleccionar la opcion **Deploy a new agent**, como se presenta a continuacion

IMG_Opcion_nuevo_agente

El cual nos presentara un asistente, mediante el cual podremos establecer las caracteristicas de este nuevo agente, empezando por el sistema operativo

IMG_Nuevo_agente_1

A continuacion y dependiendo de la opcion anteriormente seleccionada, podremos seleccionar la version del sistema operativo de este agente

img_Nuevo_agente_2

A continuacion, podremos seleccionar la arquitectura del mismo

img_Nuevo_agente_3

A continuacion en el paso 4, debemos informar, cual es la direccion IP del servidor principal o el nodo al que se conectara este agente

img_Nuevo_agente_4

En el siguiente paso 5, debemos de informar el nombre del agente y podremos clasificarlo mediante grupos que hayamos definido previamente (si aun no se definen los grupos, estos se pueden generar en el menu de wazuh y asignar posteriormente)


img_Nuevo_agente_5

A continuacion, nos presentara un comando que debemos de copiar y ejecutar en una consola de comandos de nuestro agente a registrar, mediante un usuario con privilegios.

img_Nuevo_agente_6

Finalmente, si la instalacion se ejecuto exitosamente, podremos configurar el servicio para que se inicie cada vez que arranca el sistema asi como iniciar el agente inmediatamente.

img_Nuevo_agente_7

Con lo anterior, ya podremos visualizar en el listado de agentes, que este ya aparece registrado y se encuentra en linea y reportando informacion.

img_Nuevo_agente_8






















A continuacion, nos presentara un comando que debemos de copiar y ejecutar en una consola de comandos de nuestro agente a registrar, mediante un usuario con privilegios.




 Antes de iniciar nuestro proceso de asignación de una dirección IP estática a nuestra máquina virtual, es necesario indagar en nuestro sistema, cuantas interfaces de red tiene instaladas y el nombre de cada una de ellas, esta informacion la podemos obtener mediante la ejecución del comando:

```sudo ip addr```

![Información de las interfaces de red](https://github.com/hernandopena/Wazuh/blob/3ec8094755ce619d9f574ea5abd49d3d29b8dbcf/1.%20Instalaci%C3%B3n%20Ubuntu%2022.04/imagenes/informacion_interfaces.jpg)

Una vez ejecutado, nos presentara las interfaces de red disponibles, y para este caso, podemos observar que cuenta con una interfaz loopback, y una interfaz de red denominada: **enp0s17** la cual es la que se conectara a la red local, ahora, con la ayuda de la consola del sistema, vamos a navegar hasta el directorio donde se encuentra los archivos de configuración de la red, en este caso ```/etc/netplan/```, con el uso del siguiente comando

```cd /etc/netplan/```

El cual nos ubicará en dicho directorio, y podremos listar los archivos que existen a traves del comando ```ls```, como se muestra en la siguiente imagen

![Listado archivos de configuración de red](https://github.com/hernandopena/Wazuh/blob/3ec8094755ce619d9f574ea5abd49d3d29b8dbcf/1.%20Instalaci%C3%B3n%20Ubuntu%2022.04/imagenes/ruta_configuracion_red.jpg)

Podemos ver que existe un archivo llamado **00-installer-config.yaml**, del cual vamos a crear una copia de seguridad, con el comando ```sudo cp 00-installer-config.yaml 00-installer-config.yaml_bak```

![Backup archivo de configuración de red](https://github.com/hernandopena/Wazuh/blob/3ec8094755ce619d9f574ea5abd49d3d29b8dbcf/1.%20Instalaci%C3%B3n%20Ubuntu%2022.04/imagenes/backup_archivo_red.jpg)


## Modificación de la configuración de red

Ahora con la ayuda del editor **nano** vamos a editar el archivo de configuración de la interfaz de red para la parametrización de la siguiente manera: ```sudo nano 00-installer-config.yaml``` y remplazamos el contenido por el siguiente fragmento de instrucciones:

```
network:
ethernets:
# interface name
enp0s17:
dhcp4: false
addresses: [192.168.1.100/24]
routes:
- to: default
via: 192.168.1.254
metric: 100
nameservers:
addresses: [200.13.249.101,190.248.0.8]
# DNS search base
search: [localdomain]
dhcp6: false
version: 2
```

quedando el archivo de configuración como se presenta en la siguiente imagen

![Edición archivo de configuración de red](https://github.com/hernandopena/Wazuh/blob/3ec8094755ce619d9f574ea5abd49d3d29b8dbcf/1.%20Instalaci%C3%B3n%20Ubuntu%2022.04/imagenes/edit_conf_red.jpg)

Guardamos los cambios y salimos del editor, y aplicamos los cambios realizados con el comando ```sudo netplan apply``` verificando que a nueva configuración se vea reflejada con el comando ```sudo ip addr```, como se muestra a continuación

![Verificación de la nueva configuración de red](https://github.com/hernandopena/Wazuh/blob/3ec8094755ce619d9f574ea5abd49d3d29b8dbcf/1.%20Instalaci%C3%B3n%20Ubuntu%2022.04/imagenes/verificacion_netplan.jpg)

En este momento ya hemos realizado la configuración de la ip estática en nuestro servidor linux con sistema operativo Ubuntu.
