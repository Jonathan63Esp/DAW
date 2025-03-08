# Creando escenarios multicontenedor con Docker Compose

# Ejemplo 1: Despliegue de la aplicación guestbook

Primero descargamos el fichero docker-compose.yaml desde esta página

https://github.com/josedom24/curso_docker_ies/tree/main/ejemplos/modulo4/ejemplo1

![image](https://github.com/user-attachments/assets/2b3c9430-7bbc-4ce5-8bce-38a5a89e771a)

Con el fichero docker-compose.yaml vamos a definir el escenario. El comando docker compose se debe ejecutar en el directorio donde este ese fichero.

![image](https://github.com/user-attachments/assets/601c6ef1-8a21-4e2d-9e50-3311d9a67d76)

![image](https://github.com/user-attachments/assets/3b7232dc-b295-40f1-a619-5ee844056491)


```docker compose up -d```

![image](https://github.com/user-attachments/assets/c1fb4e46-bf05-4c0f-aaa9-9306533d233b)

Ahora usamos el comando ```docker-compose ps``` r, que aunque es igual que docker ps la diferencia es que hay que ejecutar este comandoen el directorio donde esta el archivo docker-compose.yml y al hacerlo verás una lista de los contenedores que se están ejecutando, junto con la siguiente información:

- Nombre del contenedor
- Estado del contenedor (ej., "Up", "Exited", etc.)
- Puertos mapeados (si se ha configurado algún puerto en el docker-compose.yml)
- Comando ejecutado (lo que está haciendo el contenedor)

![image](https://github.com/user-attachments/assets/b75262be-32c8-485a-9727-1faaa5cf1319)

Si nos vamos a localhost:8080 vemos que la aplicación esta activo

![image](https://github.com/user-attachments/assets/e61acf06-738b-41ae-ab1b-ba86d63f6d47)

Si queremos parar los contenedores usamos ```docker compose stop```

y si queremos eliminar el escenario usamos ```docker compose down```

![image](https://github.com/user-attachments/assets/97d7d468-6af4-48fb-94df-f00848ff7394)

# Ejemplo 2: Despliegue de la aplicación Temperature

Igual que antes nos bajamos el archivo docker-compose.yaml de este enlace y lo ponemos en la carpeta de antes, sustituyendo al anterior archivo

https://github.com/josedom24/curso_docker_ies/tree/main/ejemplos/modulo4/ejemplo2

![image](https://github.com/user-attachments/assets/5ca507be-9271-42e5-90f5-2d1c498b3961)

Una vez hecho ejecutamos ```docker compose up -d``` para montarmo y ```docker-compose ps```para ver que estan los contenedores

![image](https://github.com/user-attachments/assets/ec07a504-4cc2-42bf-af6b-7ef829b60f4b)

Y si nos vamos a localhost:8081 esta la aplicacion

![image](https://github.com/user-attachments/assets/3d81bf93-0387-4506-8e6d-16a7dc992226)

Igual que antes:

Si queremos parar los contenedores usamos ```docker compose stop```

y si queremos eliminar el escenario usamos ```docker compose down```

![image](https://github.com/user-attachments/assets/e00a8e76-1529-4e1a-b3a6-7ff31d5e2f5e)


# Ejemplo 3: Despliegue de WordPress + Mariadb

Para esto modificaremos el archivo docker-compose.yaml con lo siguiente

```

version: '3.1'
services:
  wordpress:
    container_name: servidor_wp
    image: wordpress
    restart: always
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: user_wp
      WORDPRESS_DB_PASSWORD: asdasd
      WORDPRESS_DB_NAME: bd_wp
    ports:
      - 80:80
    volumes:
      - wordpress_data:/var/www/html/wp-content
  db:
    container_name: servidor_mysql
    image: mariadb
    restart: always
    environment:
      MYSQL_DATABASE: bd_wp
      MYSQL_USER: user_wp
      MYSQL_PASSWORD: asdasd
      MYSQL_ROOT_PASSWORD: asdasd
    volumes:
      - mariadb_data:/var/lib/mysql
volumes:
    wordpress_data:
    mariadb_data:

```

Lo modificamos usando un editor de codigo como Visual Studio Code

![image](https://github.com/user-attachments/assets/b15f0c4e-0206-4d4d-9dfe-7ca40bf6944b)

Una vez hecho ejecutamos ```docker compose up -d``` para montarmo y ```docker-compose ps```para ver que estan los contenedores

![image](https://github.com/user-attachments/assets/83242340-9526-47ce-bdb3-4838df4afb99)

Y si nos vamos a localhost:80 esta la aplicacion

![image](https://github.com/user-attachments/assets/00f34361-8db7-428d-9e65-a3cfd01ae338)

Igual que antes:

Si queremos parar los contenedores usamos ```docker compose stop```

y si queremos eliminar el escenario usamos ```docker compose down```

![image](https://github.com/user-attachments/assets/aa940cb5-26bc-4b3a-b213-542f6ff2d76c)




