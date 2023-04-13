# 1.1. Configuracion de Red
A continuacion, vamos a presentar de manera breve, como asignar una direccion IP estatica en el sistema operativo Ubuntu

## Consulta de informacion de interfaces de red

Antes de iniciar nuesto proceso de asignacion de una direccion IP estatica a nuestra maquina virtual, es necesario indagar en nuestro sistema, cuantas interfaces de red tiene instaladas y el nombre de cada una de ellas, esta informacion la podemos obtener mediante la ejecucion del comando: 

```sudo ip addr```

![información de las interfaces de red](https://github.com/hernandopena/Wazuh/blob/8426080e775bb4f0b0c31403d0a7da1b2abd5300/1.%20Instalaci%C3%B3n%20Ubuntu%2022.10/imagenes/informacion_interfaces.jpg)

Una vez ejecutado, nos presentara las interfaces de red disponibles, y para este caso, podemos observar que cuenta con una interfaz loopbak, y una interfaz de red denominada: **enp0s17** la cual es la que se conectara a la red local, ahora, con la ayuda de la consola del sistema, vamos a navegar hasta el directorio donde se encuentra los archivos de configuracion de la red, en este caso ```/etc/netplan/```, con el uso del siguiente comando

```cd /etc/netplan/```

El cual nos ubicara en dicho directorio, y podremos listar los archivos que existen a traves del comando ```ls```, como se muestra en la siguiente imagen

![listado archivos de configuración de red](https://github.com/hernandopena/Wazuh/blob/8426080e775bb4f0b0c31403d0a7da1b2abd5300/1.%20Instalaci%C3%B3n%20Ubuntu%2022.10/imagenes/ruta_configuracion_red.jpg)

En este momento ya hemos terminado el proceso de instalacion del sistema operativo Ubuntu.
