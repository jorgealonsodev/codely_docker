# Volúmenes y almacenamiento 

Listar volúmenes

```Bash
docker volume ls 
```
Crea un volumen nuevo

```Bash
docker volume create nuevo_volume 
```
Con el siguiente comando le pedimos a docker que cree un nuevo volumen que lo va a montar dentro de filesystem de la imagen de ubuntu  en la ruta /data. 

```Bash
docker run -it --name vol-test -v /data ubuntu 
```
Le decimos el volumen donde lo va a montar

```Bash
docker run -it --name vol-test -v mi_volumen:/data ubuntu 
```
Le indicamos la ruta donde va guardar el contenido del contenendor. 

```Bash
docker run -it --name vol-test -v {$PWD}:/data ubuntu 

docker run -it --name vol-test -v /mnt/mi_volumen:/data ubuntu
```
Con este comando Docker guardará el contenido de esa carpeta dentro del contenedor en una carpeta del servidor. 

```Bash
VOLUME /data
```

 