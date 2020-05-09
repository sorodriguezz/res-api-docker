# API REST con NodeJS en Docker

  **API Rest simple con NodeJS, para ver el funcionamiento de express, docker y nodejs. El proyecto trata de los inios de la creacion de un server en backend, mostrando funcionamientos sencillos para entender con mejor detalle la funcion de cada linea de codigo.**

## Índice
- [Instalacion Docker](#1-instalación-docker).
- [Iniciar proyecto NodeJS](#2-iniciar-proyecto-nodejs).
- [Instalacion paquetes necesarios](#3-instalación-de-paquetes-necesarios).
- [Creación Dockerfile](#4-creación-dockerfile).
- [Configuración dockeringore](#5-configuración-dockerignore).
- [Cambiar inicio de la aplicación](#6-cambiar-inicio-de-la-aplicación).
- [Creación imagen docker](#7-creación-imagen-docker).
- [Comandos docker utiles](#8-comandos-docker-utiles).
- [Muestras](#muestras).


### 1. Instalación Docker
  - En Windows:
    - Registrarse a docker hub en https://hub.docker.com/signup.
    - Descargar Docker Desktop desde https://hub.docker.com/editions/community/docker-ce-desktop-windows/.
    - Requisitos: 
      - Tener Hyper-V instalado.
      - Tener la virtualización habilitada.
    - En `cmd` ejecutar:
    <pre><code>$ docker version </code></pre>
  
  - En Linux (Ubuntu):
    - Primero, actualice su lista de paquetes existente:
    <pre><code>$ sudo apt update</code></pre>
    - Intalar paquetes:
    <pre>
        $ sudo apt-get install \
          apt-transport-https \
          ca-certificates \
          curl \
          gnupg-agent \
          software-properties-common
    </pre>
    - Agregue la clave GPG oficial de Docker:
    <pre><code> $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - </code></pre>
    - Verifique que ahora tiene la clave con la huella digital 9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88, buscando los últimos 8 caracteres de la huella digital.
    <pre>
      $ sudo apt-key fingerprint 0EBFCD88
      
         pub   rsa4096 2017-02-22 [SCEA]
               9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
         uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
         sub   rsa4096 2017-02-22 [S]
    </pre>
    - Use el siguiente comando para configurar el repositorio estable:
    <pre>
      $ sudo add-apt-repository \
          "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
          $(lsb_release -cs) \
          stable"
    </pre>
    - Actualice el aptíndice del paquete:
    <pre><code> sudo apt-get update </code></pre>
    - Instale la última versión de Docker Engine y del contenedor:
    <pre><code> $ sudo apt-get install docker-ce docker-ce-cli containerd.io </code></pre>
    - Pruebe la instalación con:
    <pre><code>$ sudo docker version </code></pre>
    - Verifique que Docker Engine esté instalado correctamente ejecutando la  imagen `hello-world`:
    <pre><code>$ sudo docker run hello-world </code></pre>
    - Si desea utilizar Docker como usuario no root, ahora debería considerar agregar a su usuario al grupo "docker" con algo como:
    <pre><code>$ sudo usermod -aG docker your-user</code></pre>
    
    
### 2. Iniciar proyecto NodeJS
  - Abrir `cmd`, ubicarse en el directorio del proyecto y usar el comando:
  <pre><code>$ npm init -y</code></pre>
  *Creará un archivo package.json que tendrá todas las configuraciones y dependencias del proyecto*
 
### 3. Instalación de paquetes necesarios
  - Instalar `morgan` para registrar las solicitudes realizadas al servidor:
  <pre><code>$ npm install morgan</code></pre>
  - Instalar el framework `express` que esta basado en `http` para NodeJS:
  <pre><code>$ npm install express</code></pre>
  
### 4. Creación Dockerfile
  - Crear archivo llamado `Dockerfile` en la raíz del proyecto para darle parametro para la creacion de una imagen.
  - Puedes encontrar mas información en https://docs.docker.com/engine/reference/builder/
  
### 5. Configuración dockerignore
  - Pruedes crear un archivo `.dockerignore` en la raíz del proyecto para que a la hora de crear la imagen docker no cuente las carpetas y archivos descritos en ese archivo.
  - Más información en https://docs.docker.com/engine/reference/builder/#dockerignore-file

### 6. Cambiar inicio de la aplicación
  - Para cambiar el comando de ejecucion del proyecto a `npm start`, debes dirigirte a `package.json` y en el apartado `scripts` dirá     <pre><code> "test": "mensaje-aqui" </code></pre>
  - Debes cambiar lo que esta en `"test"` por `"start"` y el `"mensaje_aqui"` por `"node src/index.js"`, el cual es el archivo con el que se ejecuta tu proyecto. Una vez configurado, puedes arracar el proyeto con `npm start`.
 
### 7. Creación imagen docker
  - Para crear una imagen desde un archivo `Dockerfile` se ocupa: 
  <pre><code>$ docker build -t node-api .</code></pre>
  - El `.` para especificar en que directorio esta el archivo `Dockerfile` y el `node-api` sera el nombre de la imagen.
  - Una vez creada la imagen puedes usar el comando `docker images` para visualizar las imagenes creadas en docker.
  - Para ejecutar o arrancar un contenedor con la imagen creada usar:
  <pre><code>docker run -it -p 4000:3000 name_image</code></pre>
    - El parametro `-it` es para arrancar por consola el contenedor, en caso de arrancar el contenedor como servicio usar `-d`.
    - El parametro `-p` indica el puerto que transformará fuera del contenedor, en este caso dentro del contenedor arrancara en el puerto `3000`, para ingresa desde afuera se le indica el puerto `4000`.
    - Una vez ejecutandose el comando, puedes visualizar el contenedor en ejecución con `docker ps` y `docker stop name_container` para detenerlo.
    
  
### 8. Comandos docker utiles
  - Para entrar por consola a un contenedor en ejecución: 
  <pre><code>$ docker container exec -it name_container /bin/bash</code></pre>
  - Para descargar imagenes: 
  <pre><code>$ docker pull name_image</code></pre>
  - Mostrar imagenes descargadas: 
  <pre><code>$ docker images</code></pre>
  - Para eliminar una imagen: 
  <pre><code>$ docker rmi  id_container</code></pre>
  - Mostrar informacion del contenedor:
   <pre><code>$docker inspect id_container</code></pre>
  - Para eliminar un contenedor (`-f` para forzar):
  <pre><code>$ docker rm -f id_container</code></pre>
  
### 9. Muestras
![alt text](https://raw.githubusercontent.com/soRodriguezz/res-api-docker/master/muestra.png)

*Link de referencia:* https://nodejs.org/fr/docs/guides/nodejs-docker-webapp/
