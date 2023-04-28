# Configuración de la Zona Horaria
A continuación, vamos a presentar de manera de como consultar la zona horaria del sistema con sistema operativo Ubuntu

## Verificación de la Zona Horaria Actual

Para consultar la zona horaria configurada actualmente en el sistema operativo, basta con ejecutar el comando ```timedatectl```, el cual presentara la informacion de la siguiente manera:

![Consulta del uso horario actual](https://github.com/hernandopena/Wazuh/blob/77b177a414b9ebba0404a31f9c194241db9bc060/1.%20Instalaci%C3%B3n%20Ubuntu%2022.10/imagenes/consulta_zona_horaria.jpg)

En el ejemplo anterior, podemos ver que se encuentra configurado bajo una zona horario UTC+0.

## Modificación de la Zona Horaria

Para hacer cambios en la zona horaria del sistema, podemos usar el comando ```sudo timedatectl set-timezone America/Bogota```, el cual configurara el sistema a una zona horaria UTC-5.

![Modificación del uso horario](https://github.com/hernandopena/Wazuh/blob/77b177a414b9ebba0404a31f9c194241db9bc060/1.%20Instalaci%C3%B3n%20Ubuntu%2022.10/imagenes/modificacion_zona_horaria.jpg)

Al realizar la consulta de la zona horaria, podremos ver reflejado el cambio en el uso horario.

Si se requiere cambiar el uso horario a una zona diferente, basta con consultar a traves del comando ```timedatectl list-timezones```

Es importante que todos los dispositivos que hacen parte de la infraestructura tecnológica estén bajo el mismo uso horario, eso permitirá correlacionar la informacion bajo la misma hora.
