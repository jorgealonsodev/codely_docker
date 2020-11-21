# Variables de entorno

Añadimos la variable de entorno en el Dockerfile:

>ENV DISPLAY_ERRORS="On"

Y ponemos en php.ini la variable en el parametro que queramos modificar.

>display_errors = "${DISPLAY_ERRORS}"

 Creación del contenedor

>$ docker build -t "hello-php-env" . 

 Lanzamos el contenedor con la variable de entorno que queremos modificar

>$ docker run --rm -e DISPLAY_ERRORS=Off -p 8000:80 "hello-php-env" 

Ahora ya no muestra los errores.
