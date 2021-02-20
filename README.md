# IAW - Práctica PrestaShop
>IES Celia Viñas (Almería) - Curso 2020/2021   
>Módulo: IAW - Implantación de Aplicaciones Web   
>Ciclo: CFGS Administración de Sistemas Informáticos en Red 

## Contenido
1.Práctica: Instalación de PrestaShop usando contenedores Docker y Docker Compose
1.1. Tareas a realizar
1.2. Requisitos del archivo docker-compose.yml
2.1. Networks
2.2. Docker restart policies
2.3. Variables de entorno
2.4. Orden en el que se inician los servicios
2.Referencias


## 1 Práctica: Instalación de PrestaShop usando contenedores Docker y Docker Compose

En esta práctica tendremos que realizar la implantación de un sitio [PrestaShop](https://www.prestashop.com/es) en [Amazon Web Services (AWS)](https://aws.amazon.com/es/) haciendo uso de contenedores [Docker](https://www.docker.com/) y la herramienta [Docker Compose](https://docs.docker.com/compose/).

### 1.1 Tareas a realizar

A continuación se describen muy brevemente algunas de las tareas que tendrá que realizar.

1. Crear una máquina virtual [Amazon EC2](https://aws.amazon.com/es/). 
> Para evitar posibles problemas con el instalador de PrestaShop asegúrese que su máquina virtual tiene al menos 2 GB de memoria RAM 

3. Instalar y configurar [Docker](https://www.docker.com/) y [Docker Compose](https://docs.docker.com/compose/) en la máquina virtual.
```apt install docker```
```apt install docker-compose```

5. Crear un archivo **docker-compose.yml** para poder desplegar los servicios de **PrestaShop**, **MySQL** y **phpMyAdmin**. Deberá utilizar las imágenes oficiales de [Docker Hub](https://hub.docker.com/).

7. Buscar cuál es la dirección IP pública de su instancia en AWS y comprobar que puede acceder a los servicios de **PrestaShop** y **phpMyAdmin** desde una navegador web.

### 1.2 Requisitos del archivo docker-compose.yml
#### 1.2.1 Networks
Los servicios definidos en el archivo **docker-compose.yml** deberán usar dos redes:

- frontend-network
- backend-network

En la red frontend-network estarán los servicios:

- **PrestaShop**
- **phpMyAdmin**

Y en la red backend-network sólo estará el servicio:

- **MySQL**

Sólo los servicios que están en la red frontend-network expondrán sus puertos en el host. Por lo tanto, el servicio de **MySQL** no deberá estar accesible desde el host.

A continuación se muestra un diagrama con las redes y los servicios que tiene que crear:

![image1](images/índice.png "Indice")


#### 1.2.2 Docker restart policies
Deberá utilizar alguna política de reinicio para que los contenedores se reinicien cada vez que se detengan de forma inesperada.

#### 1.2.3 Variables de entorno
Deberá hacer uso de un archivo .env para almacenar todas las variables de entorno que necesite en el archivo **docker-compose.yml**.

#### 1.2.4 Orden en el que se inician los servicios

Deberá indicar el orden en el que se deben iniciar los servicios con la opción depends_on. Se recomienda la lectura del artículo [Control startup and shutdown order in Compose](https://docs.docker.com/compose/startup-order/).

## 2 Referencias
- [José Juan Sanchez](https://josejuansanchez.org/iaw/practica-prestashop/index.html)
- [Curso de introducción a Docker.](https://josejuansanchez.org/curso-docker/)
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- [Control startup and shutdown order in Compose](https://docs.docker.com/compose/startup-order/)
