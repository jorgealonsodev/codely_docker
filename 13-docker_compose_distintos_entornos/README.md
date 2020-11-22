# Usar docker compose en diferente entornos

Modificamos las variables de entorno para que las obtenga automáticamente de las que están definidas en el sistema.

```
version: '2.3'
services:
  app:
    build:
      context: ${PWD}
      dockerfile: Dockerfile
# Si configuramos asi el environment, coje los datos del sistema en donde los alojamos
    environment:
      - DISPLAY_ERRORS
      - MYSQL_HOST
      - MYSQL_USER
      - MYSQL_PASSWORD
    ports:
      - 8000:80
    depends_on: 
      - mysql

  mysql:
    image: mysql:5.7
    environment:
# Utiliza como passwor el del usuario de mysql que ya se encuentra funcionando en el sistema.
      - MYSQL_ROOT_PASSWORD=${MYSQL_USER}
    volumes:
      - ${PWD}/migrations:/docker-entrypoint-initdb.d
      - ${PWD}/mycustom.cnf:/etc/mysql/conf.d/custom.cnf
  adminer:
    image: adminer
    ports:
      - 8080:8080
    depends_on: 
      - mysql
```
Podemos añadir un archivo .env con las variables de entorno

```
DISPLAY_ERRORS=ON
MYSQL_HOST=mysql 
MYSQL_USER=root
MYSQL_PASSWORD=root
```