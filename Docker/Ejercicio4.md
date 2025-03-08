# Ejemplo 1: Despliegue de la aplicación Guestbook

En este ejemplo vamos a desplegar una aplicación web que requiere de dos servicios (servicio web y servicio de base de datos) para su ejecución. 

Los dos contenedores tienen que estar en la misma red y deben tener acceso por nombres (resolución DNS) ya que de principio no sabemos que ip va a coger cada contenedor. Por lo tanto vamos a crear los contenedores en la misma red con el comando ```docker network create red_guestbook```

![creando contenedores en la misma red](https://github.com/user-attachments/assets/2cd2e7f8-ed90-422d-aaa7-ae851900d149)


Y ejecutamos los contenedores usando los siguientes comandos

```docker run -d --name redis --network red_guestbook -v /opt/redis:/data redis redis-server --appendonly yes ```

![1](https://github.com/user-attachments/assets/3bb945d3-03ed-4ed9-9180-a6d9ba4fae3d)

```docker run -d -p 80:5000 --name guestbook --network red_guestbook iesgn/guestbook```

![2](https://github.com/user-attachments/assets/cf3036d6-d4fc-41fe-a69a-d59887b1eae4)

Si nos vamos a localhost podemos ver la página

![localhost](https://github.com/user-attachments/assets/ad657858-e4b2-4ad4-8a13-ed1e4a015be0)

# Ejemplo 2: Despliegue de la aplicación Temperaturas

Vamos a hacer un despliegue completo de una aplicación llamada Temperaturas. Esta aplicación nos permite consultar la temperatura mínima y máxima de todos los municipios de España. Esta aplicación está formada por dos microservicios:

- frontend: Es una aplicación escrita en Python que nos ofrece una página web para hacer las búsquedas y visualizar los resultados. Este microservicio hará peticiones HTTP al segundo microservicio para obtener la información. Este microservicio ofrece el servicio en el puerto 3000/tcp. Usaremos la imagen iesgn/temperaturas_frontend.
- backend: Es el segundo microservicio que nos ofrece un servicio web de tipo API Restful. A esta API Web podemos hacerles consultas sobre los municipios y sobre las temperaturas. En este caso, se utiliza el puerto 5000/tcp para ofrecer el servicio. Usaremos la imagen iesgn/temperaturas_backend.

Para ello creamos una red para conectar los dos contenedores que necesita

```docker network create red_temperaturas```

![image](https://github.com/user-attachments/assets/492a938e-e83e-465e-8fb7-1b271ddb5f88)

Y al igual que antes ejecutamos los dos contenedores

```

docker run -d --name temperaturas-backend --network red_temperaturas iesgn/temperaturas_backend

docker run -d -p 80:3000 --name temperaturas-frontend --network red_temperaturas iesgn/temperaturas_frontend

```

![1](https://github.com/user-attachments/assets/59ab4eeb-d6c6-4a74-8cf1-ee43be2602d1)

![2](https://github.com/user-attachments/assets/34c12535-e593-4b61-9036-08a029ff892e)

Al entrar en localhost veremos a la aplicación en ejecución

![image](https://github.com/user-attachments/assets/2681c360-7478-47f1-882a-f5126ad5046c)

# Ejemplo 3:  Despliegue de Wordpress + mariadb

Para la instalación de WordPress necesitamos dos contenedores: la base de datos (imagen mariadb) y el servidor web con la aplicación (imagen wordpress). Los dos contenedores tienen que estar en la misma red y deben tener acceso por nombres (resolución DNS) ya que de principio no sabemos que ip va a coger cada contenedor. Por lo tanto vamos a crear los contenedores en la misma red:

```docker network create red_wp```

![image](https://github.com/user-attachments/assets/0aed9790-dfb5-4b52-81af-b4a247a1170a)


Siguiendo la documentación de la imagen mariadb y la imagen wordpress podemos ejecutar los siguientes comandos para crear los dos contenedores:

```
docker run -d --name servidor_mysql --network red_wp -v /opt/mysql_wp:/var/lib/mysql -e MYSQL_DATABASE=bd_wp -e MYSQL_USER=user_wp -e MYSQL_PASSWORD=asdasd -e MYSQL_ROOT_PASSWORD=asdasd mariadb

```

![image](https://github.com/user-attachments/assets/fb54aa10-a060-489b-8227-4051054c136e)

```              
docker run -d --name servidor_wp --network red_wp -v /opt/wordpress:/var/www/html/wp-content -e WORDPRESS_DB_HOST=servidor_mysql -e WORDPRESS_DB_USER=user_wp -e WORDPRESS_DB_PASSWORD=asdasd -e WORDPRESS_DB_NAME=bd_wp -p 80:80 wordpress

```

![image](https://github.com/user-attachments/assets/79ba316b-3a1c-4a57-b90c-cf07b7e1590d)

```

docker ps

```

![image](https://github.com/user-attachments/assets/dbab0390-14a0-49a8-88a0-7efe99ce1014)

