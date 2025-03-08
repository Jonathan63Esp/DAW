# Ejercicios de Docker usando Windows

## Get Started 1

### 2.1. Ejecutar la Imagen de Hello World

Lo primero que haremos será ir al PowerShell y ejecutar el comando ```docker run hello-world``` para que nos descargue el contenedor y lo instale, al finalizar nos saldra el mensaje de "Hello from Docker!"

![Ejecutamos el comando](https://github.com/user-attachments/assets/ab6e0ec9-835e-4b09-b2c4-91084a6ef70d)

Podemos ir a la aplicación en la parte de images y podemos ver que estara dicho contenedor tambien

![Docker en la aplicación](https://github.com/user-attachments/assets/36788107-8645-4881-81ed-24f758a7aaef)

Si ejecutamos el docker veremos el mismo mensaje, solo hay que darle al boton de Run

![Docker ejecutandose](https://github.com/user-attachments/assets/ade4af83-1228-46e1-9388-6cbbc8b47f23)

### 2.2. Muestra las imágenes Docker instaladas

En el apartado de images de docker podemos ver las imagenes docker instaladas, en este caso solo vemos la de hello-world

![images de docker](https://github.com/user-attachments/assets/797610a9-0b6f-4ab7-926c-86807b1952e1)

### 2.3. Muestra los contenedores Docker

Para ver los contenedores docker que están en ejecución o si deseamos ver todos los contenedores (en ejecución y detenidos) se puede usar docker ps-a o ir a containers en la aplicación

![image](https://github.com/user-attachments/assets/5dec1135-6315-481a-8167-680b668caf67)


## Get Started 2

Lo que nos pide el ejercicio es primero hacer un clon del siguiente repositorio, lo haremos desde Powershell y habiendo tenido git previamente instalado

```git clone https://github.com/docker/getting-started-app.git```

![clonando repositorio](https://github.com/user-attachments/assets/b1ee7c8d-8dbe-4494-ba7b-189966862e7c)

Los archivos se me alojaron en C:\Users\Jonathan\getting-started-app

![archivos alojados](https://github.com/user-attachments/assets/afba2851-03f3-452d-909b-f0dd1a22d038)

En esta misma carpeta que es donde esta el package.json creamos un archivo llamado Dockerfile

![Dockerfile](https://github.com/user-attachments/assets/88a018e0-c4c0-4891-8e7b-ab51abb4a2da)

Y le pegamos el siguiente contenido
```
# syntax=docker/dockerfile:1

FROM node:lts-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
```
![image](https://github.com/user-attachments/assets/a92576b8-acd9-4e8b-a41e-f93be2e3e2a3)



Ponemos en la barra de direcciones powershell y se nos abrira la terminal con la ubicacion del archivo

![powershell](https://github.com/user-attachments/assets/9b866198-2147-42ca-bedc-0d18528da899)
![powershell abierto](https://github.com/user-attachments/assets/25d45d64-35ca-463e-b54e-d5781abaf8bc)

Ahora ponemos docker 

![image](https://github.com/user-attachments/assets/00099d49-b279-4fb1-b904-3be658adfd84)






