# 2. Instalacion Wazuh
A continuacion, presentaremos una guia de instalacion de Wazuh en el sistema operativo Ubuntu 22.10.


Todos los pasos que se describen a continuacion, estan basados en la documentacion de Wazuh, la cual pueden eoncntrar en su sitio web oficial: [Instalación de Wazuh](https://documentation.wazuh.com/current/installation-guide/index.html).

## Preparación del servidor
A continuación, presentamos los requerimientos necesarios para la instalacion de Wazuh:
- Sistema Operativo Linux: 
  - Amazon Linux 2
  - CentOS 7, 8
  - Red Hat Enterprise Linux 7, 8, 9
  - Ubuntu 16.04, 18.04, 20.04, 22.04
- Navegador web (Firefox, chrome o edge)
- Cliente SSH [Putty](https://the.earth.li/~sgtatham/putty/latest/w64/putty.exe)
- Memoria RAM, CPU y Almacenamiento, de acuerdo a la cantidad de agentes(endpoint) a instalar

| Agentes | CPU | RAM | Almacenamiento (90 dias) |
|-----------|-----------|-----------|-----------|
| 1-25 | 4 vCPU | 8 GiB | 50 GB |
| 25-50 | 8 vCPU | 8 GiB | 100 GB |
| 50-10 | 8 vCPU | 8 GiB | 200 GB |


## Proceso de instalación
Abrir una consola de conexion SSH haciendo uso del programa putty, y establecer conexion con la maquina virtual creada para alojar el servidor de wazuh, a traves de la conexion: admon@192.168.1.100 y la contraseña asignada en el proceso de instalacion.

![Conexion a traves de Putty](https://github.com/hernandopena/Wazuh/blob/f088487f5339447e9d956de680fe8ced8d50eb16/2.%20Instalacion%20Wazuh/imagenes/conexion_putty.jpg)

En la linea de comandos vamos a ejecutar el siguiente comando que realizara la descarga del instalador e inmediatamente realizara la instalacion del software wazuh:

```sudo curl -sO https://packages.wazuh.com/4.4/wazuh-install.sh && sudo bash ./wazuh-install.sh -a```

IMIG_INSTALACION_WAZUH_ADVERTENCIA

Para el caso del presente laborario, nuestra maquina no cuenta con los requerimientos minimos exigos para la operacion, asi que nos presentara una advertencia por falta de recursos.

Si deseamos continuar con la instalacion haciendo caso omiso de la advertencia, basta con agregar el parametro ```-i``` a la anterior linea, y al ejecutarla iniciara inmediatamente la instalacion.

```sudo curl -sO https://packages.wazuh.com/4.4/wazuh-install.sh && sudo bash ./wazuh-install.sh -a -i```

IMG_INSTALACION_WAZUH.JPG

Al finalizar el proceso de instalacion, el cual puede durar entre 7 y 10 minutos


  

El comando anterior se encargara de iniciar la instalacion de los componentes necesarios para el funcionamiento de wazuh, y al finalizar la instalacion, presentara el nombre de usuario y contraseña para la administracion de la plataforma.




![Conexion a traves de Putty](https://github.com/hernandopena/Wazuh/blob/f088487f5339447e9d956de680fe8ced8d50eb16/2.%20Instalacion%20Wazuh/imagenes/conexion_putty.jpg)
IMG_INSTALACION:WAZUH

Una vez la instalacion finalice, podremos acceder a traves de un navegador web a la plataforma de wazuh: **https://192.168.1.100**, como se muestra a continuacion

