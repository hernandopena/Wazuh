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

IMG_CONEXION_PUTTY


En la linea de comandos vamos a ejecutar el siguiente comando que realizara la descarga del instalador llamado **wazuh-install.sh**

```curl -sO https://packages.wazuh.com/4.4/wazuh-install.sh```

Una vez se haya descargado el instalador, vamos a ejecutarlo con la siguiente instruccion, en donde **wazuh-1** sera el nombre del nodo principal:

```bash wazuh-install.sh --wazuh-server wazuh-1```

