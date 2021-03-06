# Redes en docker compose

Archivo de docker compose con redes asignadas a mano

```
version: '2.3'
services:
  app:
    build:
      context: ${PWD}
      dockerfile: Dockerfile
    environment:
      - DISPLAY_ERRORS=On
      - MYSQL_HOST=mysql
      - MYSQL_USER=root
      - MYSQL_PASSWORD=root
    ports:
      - 8000:80
    networks: 
      - application
    depends_on: 
      - mysql

  mysql:
    image: mysql:5.7
    environment:
      - MYSQL_ROOT_PASSWORD=root
    volumes:
      - ${PWD}/migrations:/docker-entrypoint-initdb.d
      - ${PWD}/mycustom.cnf:/etc/mysql/conf.d/custom.cnf
    networks: 
      - admin
  
  adminer:
    image: adminer
    ports:
      - 8080:8080
    networks: 
      - admin
    depends_on: 
      - mysql

networks:
  admin:
  application: 
```

Para añadir un red creada anteriormente con

```
docker network create jorge_net  
```
Modificamos el archivo docker-compose.yaml

```version: '2.3'
services:
  app:
    build:
      context: ${PWD}
      dockerfile: Dockerfile
    environment:
      - DISPLAY_ERRORS=On
      - MYSQL_HOST=mysql
      - MYSQL_USER=root
      - MYSQL_PASSWORD=root
    ports:
      - 8000:80
    networks: 
      - application
      - jorge_net
    depends_on: 
      - mysql
      

  mysql:
    image: mysql:5.7
    environment:
      - MYSQL_ROOT_PASSWORD=root
    volumes:
      - ${PWD}/migrations:/docker-entrypoint-initdb.d
      - ${PWD}/mycustom.cnf:/etc/mysql/conf.d/custom.cnf
    networks: 
      - admin
      - jorge_net
  
  adminer:
    image: adminer
    ports:
      - 8080:8080
    networks: 
      - admin
    depends_on: 
      - mysql
      

networks:
# Aquí añadimos la red que creamos con docker network create jorge_net 
  jorge_net:
    external:
      name: jorge_net
  admin:
  application:  
```