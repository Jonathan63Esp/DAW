# Instalación de Wordpress en instancia Debian(o Ubuntu) EC2 con soporte de base de datos RDS y EFS

La idea de este manual es configurar un servidor web apache montado en una instancia EC2 Debian (o Ubuntu) con un sistema de almacenamiento en EFS y la base de datos que esté gestionada por RDS en una subred privada.

Para ello necesitaremos primeramente un VPC que tenga dos subredes públicas y dos privadas.
El objeto de crear dos subredes públicas es construir al final del ejercicio un balanceador de carga que permita servir contenidos en función de la carga de los servidores.

## Paso 1 Creación de las VPCs

Primero, debemos diseñar la estructura de nuestra red, incluyendo las distintas instancias y los servicios EFS y RDS. Nuestra VPC estará compuesta por cuatro subredes: dos públicas y dos privadas. Para crearlas, accedemos a nuestro laboratorio de AWS, buscamos "VPC" en el buscador y seleccionamos la opción correspondiente.

![Buscamos VPC](imagenes/Captura0.PNG)

Una vez que estemos dentro de la sección de VPC le daremos al boton de "Crear VPC"

![Botón de Crear VPC](imagenes/Captura1.PNG)

En la parte de Crear VPC, Ponemos los siguientes datos como en las imagenes

![Datos1](imagenes/Captura2.PNG)
![Datos2](imagenes/Captura3.PNG)
![Datos3](imagenes/Captura4.PNG)

Una vez puesto todos los datos le damos al boton de Crear VPC

![Boton para Crear las VPCs](imagenes/Captura5.PNG)

Y veremos como se esta creado nuestra VPC

![Flujo de Creacion de las VPCs](imagenes/Captura6.PNG)

Cuando termine de hacerse le daremos a Ver VPC para asi ver los detalles

![Detalles de las VPCs](imagenes/Sintítulo.png)

## Paso 2 Creación de la Instancia EC2

Una vez hecho esto lanzaremos una instancia en EC2, la cual tendra los siguientes datos

![Detalles de la instancia1](imagenes/Sintítulo2.PNG)
![Detalles de la instancia2](imagenes/Sintítulo3.PNG)
![Detalles de la instancia3](imagenes/Sintítulo4.PNG)
![Detalles de la instancia4](imagenes/Sintítulo5.PNG)
![Detalles de la instancia5](imagenes/Sintítulo6.PNG)

Una vez hecho le daremos al boton de Lanzar instancia y nos saldrá una ventana que nos indicara el progreso de la creacion de la instancia, el cual cuando termine nos dira que esta todo correcto

![Instancia realizada correctamente](imagenes/Sintítulo7.PNG)

Le podemos dar al boton de Ver todas las instancias para ver nuestra estancia creada

![Instancia creada](imagenes/Sintítulo8.PNG)

Con nuestra instancia creada la marcaremos y le daremos al boton de conectar

![Marcamos la instancia y le damos a conectar](imagenes/Sintítulo9.png)

En esta nueva seccion le daremos a conectar para poder conectarnos directamente con nuestra instancia

![Conectarse a la instancia](imagenes/Sintítulo10.PNG)
![Dentro de la instancia](imagenes/Sintítulo11.PNG)

## Paso 3 Instalación de Apache2

Ahora que estamos dentro de la estancia actualizaremos los paquetes que tenemos en el sistema, para ello ejecutaremos el siguiente comando

```sudo apt update && sudo apt upgrade -y```

![Instalando Apache](imagenes/Sintítulo17.PNG)

Una vez actualizados todos los paquetes procederemos a la instalación de Apache con el siguiente codigo

```sudo apt install apache2```

![Apache instalandose](imagenes/Sintítulo13.PNG)

Cuando se haya instalado ejecutaremos el siguiente codigo para ver si esta ejecutandose o no

```sudo systemctl status```

en caso contrario ejecutaremos ```sudo systemctl start apache2```

![Apache corriendo](imagenes/Sintítulo14.PNG)


Ahora abriremos un navegador o pestaña aparte y pondremos la IP publica de nuestra estancia para comprobar que efectivamente esta instalado y ejecutandose Apache

![Apache corriendo en el servidor de la instancia publicamente](imagenes/Sintítulo15.PNG)

## Paso 4 Instalación del módulo de PHP

El siguiente paso es instalar PHP mediante el modulo de Apache2, para ello ejecutaremos el siguiente código

```sudo apt install php libapache2-mod-php php-cli```

![Instalando PHP](imagenes/Sintítulo16.PNG)

Y una vez instalado pondremos ```php -v ``` para comprobar que efectivamente php esta instalado y a la ultima version disponible

![Comprobando la versión de PHP](imagenes/Sintítulo18.PNG)

## Paso 5 Instalación del módulo de MySQL


