# Creación de imágenes en docker

# Ejemplo 1: Construcción de imágenes con una página estática

En este ejemplo vamos a crear una imagen con una página estática. Vamos a crear tres versiones de la imagen, y puedes encontrar los ficheros en este directorio del repositorio.

https://github.com/josedom24/curso_docker_ies/tree/main/ejemplos/modulo5/ejemplo1

## Version 1: Desde una imagen base

Nos bajamos la version 1 y metemos los archivos dentro de una carpeta, en mi caso la carpeta se llama docker1

![image](https://github.com/user-attachments/assets/5fc285ae-ce6c-43b4-bf9d-098293a1e7df)

Montamos la build

```docker build -t jonathan63esp/ejemplo1:v1 .```

![image](https://github.com/user-attachments/assets/999f7457-a0b0-45ab-9af6-b0cf5d0aa3e6)

Comprobamos la imagen creada con ```docker images```

![image](https://github.com/user-attachments/assets/ee654725-7b7e-43c8-ab27-7433cb9e22db)

Y creamos un contenedor

```docker run -d -p 80:80 --name ejemplo1 jonathan63esp/ejemplo1:v1```

![image](https://github.com/user-attachments/assets/c8094f57-f5f6-4984-a3ba-9d6b2f953af1)

Si vamos a localhost sale la pagina

![image](https://github.com/user-attachments/assets/6156fe36-9439-4634-9b46-ae07ecf86b06)
