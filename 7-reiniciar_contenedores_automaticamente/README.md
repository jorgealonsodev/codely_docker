# Reiniciar contenedores automáticamente

Reiniciar contenedores vacíos automáticamente. 

```Bash
docker run  -it --restart=on-failure:10 mi-aplicacion-php 
```

Politicas: 

**no** - No hacer nada (por defecto)  

**always** - Cada vez que un contenedor falla o es parado se reinicia automáticamente. 

PPara pararlo primero actualizar el contenedor con --restart=no y después pararlo. 


```Bash
docker update --restart=no <container_id> 

docker stop <container_id>  
```

**unless-stopped** - Se reinicia automaticamente hasta que se para con el comando stop 

**on-failure:10** - Se reinicia un máximo de 10 veces en caso de fallo. 