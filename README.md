# API REST con NodeJS en Docker


## Índice
- [Instalacion Docker](#1-instalación-docker).
- [Iniciar proyecto NodeJS](#2-iniciar-proyecto-nodejs).
- [Instalacion paquetes necesarios](#paquetes-necesarios).
- [Configuración de rutas](#configurar-rutas).
- [Creación Dockerfile](#docker-file).
- [Configuración dockeringore](#docker-ignore).
- [Cambiar inicio de la aplicación](#script-inicio).
- [Creación imagen docker](#docker-image).
- [Comandos docker utiles](#comandos-docker).
- [Ejecución imagen docker]($ejecutar-image-docker).
- [Entrar a contenedor docker](#entrar-docker).
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
      <pre><code>$ npm init</code></pre>
