# Configuración de Red
A continuación, vamos a presentar de manera breve, como asignar una dirección IP estática en el sistema operativo Ubuntu

## Consulta de informacion de interfaces de red

Antes de iniciar nuestro proceso de asignación de una dirección IP estática a nuestra máquina virtual, es necesario indagar en nuestro sistema, cuantas interfaces de red tiene instaladas y el nombre de cada una de ellas, esta informacion la podemos obtener mediante la ejecución del comando:

```sudo ip addr```

![información de las interfaces de red](https://github.com/hernandopena/Wazuh/blob/8426080e775bb4f0b0c31403d0a7da1b2abd5300/1.%20Instalaci%C3%B3n%20Ubuntu%2022.10/imagenes/informacion_interfaces.jpg)

Una vez ejecutado, nos presentara las interfaces de red disponibles, y para este caso, podemos observar que cuenta con una interfaz loopback, y una interfaz de red denominada: **enp0s17** la cual es la que se conectara a la red local, ahora, con la ayuda de la consola del sistema, vamos a navegar hasta el directorio donde se encuentra los archivos de configuración de la red, en este caso ```/etc/netplan/```, con el uso del siguiente comando

```cd /etc/netplan/```

El cual nos ubicara en dicho directorio, y podremos listar los archivos que existen a traves del comando ```ls```, como se muestra en la siguiente imagen

![listado archivos de configuración de red](https://github.com/hernandopena/Wazuh/blob/8426080e775bb4f0b0c31403d0a7da1b2abd5300/1.%20Instalaci%C3%B3n%20Ubuntu%2022.10/imagenes/ruta_configuracion_red.jpg)

Podemos ver que existe un archivo llamado **00-installer-config.yaml**, del cual vamos a crear una copia de seguridad, con el comando ```sudo cp 00-installer-config.yaml 00-installer-config.yaml_bak```

![Backup archivo de configuración de red](https://github.com/hernandopena/Wazuh/blob/ecbbc2a40ca300232e9099d6a0abfb5daea4e070/1.%20Instalaci%C3%B3n%20Ubuntu%2022.10/imagenes/backup_archivo_red.jpg)

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

![Edición archivo de configuración de red](https://github.com/hernandopena/Wazuh/blob/678452528edf6100fa4b535af85fd5b067acf630/1.%20Instalaci%C3%B3n%20Ubuntu%2022.10/imagenes/edit_conf_red.jpg)

Guardamos los cambios y salimos del editor, y aplicamos los cambios realizados con el comando ```sudo netplan apply``` verificando que a nueva configuración se vea reflejada con el comando ```sudo ip addr```, como se muestra a continuación

![Verificación de la nueva configuración de red](https://github.com/hernandopena/Wazuh/blob/678452528edf6100fa4b535af85fd5b067acf630/1.%20Instalaci%C3%B3n%20Ubuntu%2022.10/imagenes/verificacion_netplan.jpg)

En este momento ya hemos realizado la configuración de la ip estática en nuestro servidor linux con sistema operativo Ubuntu.
