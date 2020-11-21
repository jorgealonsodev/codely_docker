# Variables de entorno

Añadimos la variable de entorno en el Dockerfile:
```bash
ENV DISPLAY_ERRORS="On"
```
Y ponemos en php.ini la variable en el parametro que queramos modificar.
```bash
display_errors = "${DISPLAY_ERRORS}"
```
 Creación del contenedor
 
```bash
$ docker build -t "hello-php-env" . 
```
 Lanzamos el contenedor con la variable de entorno que queremos modificar

```bash
$ docker run --rm -e DISPLAY_ERRORS=Off -p 8000:80 "hello-php-env" 
```

Ahora ya no muestra los errores.
