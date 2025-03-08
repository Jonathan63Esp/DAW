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

Ahora usamos el comando ```docker-compose up p``` r, que aunque es igual que docker ps la diferencia es que hay que ejecutar este comandoen el directorio donde esta el archivo docker-compose.yml y al hacerlo verás una lista de los contenedores que se están ejecutando, junto con la siguiente información:

- Nombre del contenedor
- Estado del contenedor (ej., "Up", "Exited", etc.)
- Puertos mapeados (si se ha configurado algún puerto en el docker-compose.yml)
- Comando ejecutado (lo que está haciendo el contenedor)

![image](https://github.com/user-attachments/assets/b75262be-32c8-485a-9727-1faaa5cf1319)
