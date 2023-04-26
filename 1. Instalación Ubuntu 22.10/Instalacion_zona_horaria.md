# Configuracion de la Zona Horaria
A continuación, vamos a presentar de manera de como consultar la zona horaria del sistema con sistema operativo Ubuntu

## Verificacion de la Zona Horaria Actual

Para consultar la zona horaria configurada actualmente en el sistema operativo, basta con ejecutar el comando ```timedatectl```, el cual presentara la informacion de la siguiente manera:

IMG_CONSULTA_ZONA_HORARIA

En el ejemplo anterior, podemos ver que se encuentra configurado bajo una zona horario UTC+0.

## Modificacion de la Zona Horaria

Para hacer cambios en la zona horaria del sistema, podemos usar el comando ```sudo timedatectl set-timezone America/Bogota```, el cual configurara el sistema a una zona horaria UTC-5.

IMG_MODIFICACION_ZONA_HORARIA

Al realizar la consulta de la zona horaria, podremos ver reflejado el cambio en el uso horario.

Si se requiere cambiar el uso horario a una zona diferente, basta con consultar a traves del comando ```timedatectl list-timezones```

Es importante que todos los dispositivos que hacen parte de la infraestructura tecnologica esten bajo el mismo uso horario, eso permitira correlacionar la informacion bajo la misma hora


![Actualización de catálogos de software](https://github.com/hernandopena/Wazuh/blob/c8c6d2eaca4a4b4daac4db5d6fb7daab3ac70ce9/1.%20Instalaci%C3%B3n%20Ubuntu%2022.10/imagenes/apt_update.jpg)



Una vez ejecutado este comando, podremos instalar el editor nano, con el siguiente comando:

```sudo apt install nano```

![Instalación editor nano](https://github.com/hernandopena/Wazuh/blob/c8c6d2eaca4a4b4daac4db5d6fb7daab3ac70ce9/1.%20Instalaci%C3%B3n%20Ubuntu%2022.10/imagenes/apt_install_nano.jpg)

En este momento ya hemos instalado el editor nano en nuestro sistema, y cada vez que necesitemos editar un archivo, basta con ejecutar el comando ```sudo nano archivo_a_editar```
