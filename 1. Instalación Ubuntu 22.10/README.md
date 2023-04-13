# 1. Instalación Ubuntu 22.10
Guía de instalación de Ubuntu 22.10

La presente guía, busca presentar de manera rápida y ligera la instalación del sistema operativo Linux Ubuntu 22.10 para alojar la solución Wazuh.

Requisitos:

- Contar con una imagen del sistema operativo Linux Ubuntu 22.10 que a la fecha es la más actualizada y descargada desde su sitio web oficial: [Ubuntu](https://ubuntu.com).
- Contar con los recursos hardware que pueden ser físicos o virtuales mínimos sugeridos, como son:
  - Memoria RAM: 4 GB.
  - Almacenamiento: 40 GB para este laboratorio (en entornos de producción se debe tener presente la cantidad de informacion a procesar).
  - Conexión a internet


## Proceso de Instalación

Para iniciar la instalación del sistema operativo Linux Ubuntu, debemos de insertar el medio de instalación, si estamos en una maquia física será un DVD o una unidad USB cargada con la imagen del sistema operativo descargado de su sitio oficial.

Si estamos en una máquina virtual, debemos de agregar la unidad virtual y ordenar al hypervisor (virtualbox, vmware, proxmox etc), para que inicie el boot desde la unidad que tiene la imagen ISO del sistema operativo.

A continuación, procedemos a iniciar la maquina y nos presentara el menú de boot, similar a la siguiente imagen:

![Menu Boot](https://github.com/hernandopena/Wazuh/blob/36d9c5a7015c57c9523cccf9264cfd82ce6972f8/1.%20Instalaci%C3%B3n%20Ubuntu%2022.10/imagenes/boot.jpg)

Después de iniciar un proceso de verificación y presentar muchas líneas, nos presentara la siguiente pantalla, en donde nos solicitara la elección del idioma, en el cual seleccionaremos el idioma que más se ajuste a nuestras necesidades y gustos.

IMG_IDIOMA 

A continuación, nos presentara la pantalla, en donde nos preguntara por la configuración de la distribución del teclado, y seleccionaremos la que se ajuste también a nuestras necesidades y tipo de teclado.

IMG_TECLADO

A continuación, nos presentará la pantalla, en donde nos preguntará por el tipo de instalación que vamos a realizar, para este caso seleccionaremos la opción **Ubuntu Server**, como se muestra en la siguiente imagen

IMG_TIPO_INSTALACION

A continuación, nos presentara las opciones para que nuestra máquina virtual se conectara a la red, bien sea local o hacia internet, en este paso podemos configurar nuestra interfaz de red para que reciba una dirección desde nuestro servidor DHCP de nuestra red local, más adelante realizaremos la configuración de una dirección IP estática, como se puede apreciar en la siguiente imagen.

IMG_CONFIG_RED

Una vez configuremos la interfaz para que reciba una dirección IP automática vía DHCP, podremos ver ha recibido un direccionamiento de nuestra red, como se presenta a continuación.

IMG_RED_DHCP

una vez tengamos dirección IP, podemos continuar con el siguiente paso, en donde nos preguntara si para acceder a internet hacemos uso de un Servidor Proxy, en donde se debe de ingresar la informacion del proxy en caso de contar con este servicio, en caso contrario se puede dejar vacío para ninguno, como se aprecia en la siguiente imagen.

IMG_PROXY

A continuación, nos presentará por defecto el repositorio desde donde descargará los archivos de instalación del sistema operativo Ubuntu, podemos trabajar con los que nos presenta la instalación.

IMG_SERVIDOR_PAQUETES

A continuación, vamos a configurar las particiones del disco duro para la instalación, para el caso de este laboratorio por ser únicamente para un laboratorio de demostración, vamos a trabajar con todo el disco duro en una sola partición, para casos de producción se recomienda tener presente una distribución del espacio personalizado.

IMG_PARTICIONES_DISCO

El asistente de instalación realizara los cálculos para optimizar el almacenamiento, el cual debemos de confirmarlo para que se guarden los cambios y actualice la tabla de particionamiento, a lo cual debemos de responder afirmativamente para continuar.

IMG_CONFIRMACION_PARTICION

En este momento, vamos a crear el usuario administrador para el sistema, para este caso crearemos el usuario **admon** con la contraseña **Admon123**.

IMG_USUARIO_ADMINISTRADOR

Posteriormente, el instalador nos preguntara si deseamos instalar el servicio SSH para acceder remotamente al servidor, para nuestro caso de laboratorio vamos a indicar que, si lo vamos a instalar marcando la casilla, y continuamos.

IMG_INSTALACION_SSH

Ahora nos presentara un listado de paquetes incluidos en el instalador del sistema operativo, para que seleccionemos aquellos que deseamos instalar, para este caso no seleccionaremos ninguno y continuamos con el proceso de instalación.

IMG_ PAQUETES_ADICIONALES

En este momento, el instalador inicia el proceso de descarga e instalación de paquetes, lo cual puede tomar un tiempo dependiendo de sus capacidades tecnológicas y de su conexión a internet.

IMG_PROCESO_INSTALACION

Una vez, el instalador descargue e instale los paquetes en nuestro computador, el sistema nos informara que ha terminado y se habilita la opción para reiniciar nuestro computador.

IMG_FINALIZACION_INSTALACION

El sistema se reiniciará, presentará cierta informacion del sistema, únicamente debemos estar atentos a que no haya mensajes de error que nos alerten sobre algún problema en la instalación.

IMG_PRIMER_BOOT

Finalmente, nos presentara en la consola la instrucción para ingresar, en donde ingresaremos la informacion de usuario y contraseña

IMG_INGRESO_CONSOLA

Una vez ingresemos, nos presentara un resumen del sistema, y podremos ver la dirección ip que le fue asignada en la red.

IMG_INFORMACION_SISTEMA










- **Elemento 1**: Descripción del elemento 1
- *Elemento 2*: _Descripción del elemento 2_


- Elemento 1
- Elemento 2
  - Subelemento 2.1
    - Sub-subelemento 2.1.1
    - Sub-subelemento 2.1.2
  - Subelemento 2.2
    1. Sub-subelemento 2.2.1
    2. Sub-subelemento 2.2.2
- Elemento 3
  - Subelemento 3.1
    - Sub-subelemento 3.1.1
      - Sub-sub-subelemento 3.1.1.1
      - Sub-sub-subelemento 3.1.1.2
    - Sub-subelemento 3.1.2
  - Subelemento 3.2
    - Sub-subelemento 3.2.1
