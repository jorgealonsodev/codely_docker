# Limitar CPU y Memoria 

```Bash
docker run  -it --memory=500m --restart=on-failure:10 -P mi-aplicacion-php 

docker run  -it --cpus=1.5 --memory=500m --restart=on-failure:10 -P mi-aplicacion-php 

docker run  -it --cpu-shares=2048 --cpus=1.5 --memory=500m --restart=on-failure:10 -P mi-aplicacion-php 
```

1 --memory=500m  

Si la aplicación llega al limite marcado, se cierra y si la política marcada es always, se vuelve a abrir. 

2 --cpus=1.5  

El container puede ocupar un máximo de 1.5 cores 

3 --cpu-shares 

Indica el peso del container a la hora de competir por cantidad de cpu, por defecto es 1024, pero se puede incrementar para que un contenedor tenga prioridad sobre otro. 

 

[Documentación CPU y Memoria docker](https://docs.docker.com/config/containers/resource_constraints)