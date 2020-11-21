# Exponer puertos

 ```bash
docker run --rm -it -p 80 mi-aplicacion-php 
```
Asigna el puerto de salida automaticamente y el puerto para acceder se puede consultar con Docker ps.  

```bash
docker run --rm -it -P mi-aplicacion-php 
```
Busca en el Dockerfile que puerto tiene que exponer.


```bash
doker run --rm it -p 80000:80 mi-aplicacion-php 
```
Le decimos los puertos a utilizar.



