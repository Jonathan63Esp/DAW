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

Paramos con ```docker stop ejemplo1``` y pasamos al siguiente ejemplo


# Ejemplo 2: Desde una imagen con apache2

Nos bajamos los archivos de aqui

https://github.com/josedom24/curso_docker_ies/tree/main/ejemplos/modulo5/ejemplo1/version2

Y desde el powershell en otra carpeta Montamos la build

```docker build -t jonathan63esp/ejemplo2:v1 .```

![image](https://github.com/user-attachments/assets/740e6761-d4ea-43e6-a437-fe318db0bf32)


Y creamos un contenedor

```docker run -d -p 80:80 --name ejemplo2 jonathan63esp/ejemplo2:v1```

![image](https://github.com/user-attachments/assets/cbd7282b-e63a-4ec6-9599-b48be8f1162e)

Si nos vamos a localhost veremos la aplicacion, que es la misma

![image](https://github.com/user-attachments/assets/4a20cb3e-cdac-4d7e-bd52-0b74f436ae8f)

Como punto extra, si miramos el archivo Dockerfile veremos que ha cambiado y que se ejecuta ahora con apache2

![image](https://github.com/user-attachments/assets/5c9225dd-3b87-411a-a486-141fa33b01f0)

Paramos con ```docker stop ejemplo2``` y pasamos al siguiente ejemplo

# Ejemplo 3: Desde una imagen con apache2




