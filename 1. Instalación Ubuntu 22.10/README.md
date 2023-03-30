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

Si estamos en una maquina virtual, debemos de agregar la unidad virtual y ordenar al hypervisor (virtualbox, vmware, proxmox etc), para que inicie el boot desde la unidad que tiene la imagen ISO del sistema operativo.

A continuación, procedemos a iniciar la maquina y nos presentara el menú de boot, similar a la siguiente imagen:

![Menu Boot](https://github.com/hernandopena/Wazuh/blob/36d9c5a7015c57c9523cccf9264cfd82ce6972f8/1.%20Instalaci%C3%B3n%20Ubuntu%2022.10/imagenes/boot.jpg)

Después de iniciar un proceso de verificación y presentar muchas líneas, nos presentara la siguiente pantalla, en donde nos solicitara la elección del idioma, en el cual seleccionaremos el idioma que más se ajuste a nuestras necesidades y gustos.

IMG_IDIOMA

A continuación, nos presentara la pantalla, en donde nos preguntara por la configuración de la distribución del teclado, y seleccionaremos la que se ajuste también a nuestras necesidades y tipo de teclado.

IMG_TECLADO

A continuación, nos presentará la pantalla, en donde nos preguntará por el tipo de instalación que vamos a realizar, para este caso seleccionaremos la opción **Ubuntu Server**, como se muestra en la siguiente imagen

IMG_TIPO_INSTALACION












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
