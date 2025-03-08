# 1. Descargar la imagen de ubuntu

En powershell usamos el comando ```docker pull ubuntu```

![ubuntu](https://github.com/user-attachments/assets/a5441733-ae80-48d6-ab14-89b7d529ed2d)


# 2. Descargar la imagen de hello-world

usamos el comando ```docker pull hello-world```

![hello-world](https://github.com/user-attachments/assets/dab36b10-586f-4f69-a075-125a824a7f8c)

# 3. Descargar la imagen de nginx

usamos el comando ```docker pull nginx```

![nginx](https://github.com/user-attachments/assets/33fa7226-0f65-4731-9dfc-5bc6923c65cc)

# 4. Listado de todas las imágenes

usamos el comando ```docker images```

![images](https://github.com/user-attachments/assets/5aebeb2b-125d-4ef8-b853-915205be088b)

# 5. Ejecutar un contenedor de Hello-World y darle el nombre “myhello1”

Para ejecutar un contenedor basado en la imagen hello-world y darle el nombre myhello1, usa el siguiente comando

```docker run --name myhello1 hello-world```

![myhello1](https://github.com/user-attachments/assets/fc17e488-2ca5-4150-88a1-929999628ea2)

# 6. Ejecutar un contenedor de Hello-World y darle el nombre “myhello2”

Para ejecutar un contenedor basado en la imagen hello-world y darle el nombre myhello2, usa el siguiente comando

```docker run --name myhello2 hello-world```

![myhello2](https://github.com/user-attachments/assets/7485ea9c-8c44-49b2-a7e4-fccb9a20691d)

# 7. Ejecutar un contenedor de Hello-World y darle el nombre “myhello3”

Para ejecutar un contenedor basado en la imagen hello-world y darle el nombre myhello3, usa el siguiente comando

```docker run --name myhello3 hello-world```

![myhello3](https://github.com/user-attachments/assets/d204fdbe-24da-4b07-a653-48159e9b7b01)

# 8. Mostrar los contenedores que se están ejecutando

con docker ```docker ps``` vemos los contenedores que se estan ejecutando, pero los contenedores de Hello-World (y otros contenedores basados en imágenes similares) se detienen automáticamente después de ejecutar su tarea, porque están diseñados para ser contenedores efímeros o contenedores de una sola ejecución.

# 9. Detener los contenedores "myhello1" , "myhello2" , "myhello3"

con los comandos 

```docker stop myhello1```
```docker stop myhello2```
```docker stop myhello3```

detenemos los contenedores myhello1 , myhello2 y myhello3 si estuvieran en ejecucion. 

![docker stop](https://github.com/user-attachments/assets/f3e74773-125b-439b-8881-898d8c819bce)

# 10. Eliminar todos los contenedores

Primero usamos ```docker ps -q | ForEach-Object { docker stop $_ }``` para parar todos los contenedores en ejecucion

![detener](https://github.com/user-attachments/assets/f7a33a6e-2042-45a8-91a6-f22afd616062)


Y luego usamos ```docker image prune -a -f``` para eliminarlos a la fuerza y sin confirmar

![eliminar](https://github.com/user-attachments/assets/7b943885-7f36-4eac-894f-ee9639703871)




