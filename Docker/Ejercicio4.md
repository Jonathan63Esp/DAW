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



