# API REST con NodeJS en Docker


## Índice
- [Instalacion Docker](#instalacion-docker).
- [Iniciar proyecto NodeJS](#iniciar-proyecto-nodejs).
- [Instalacion paquetes necesarios](#paquetes-necesarios).
- [Configuración de rutas](#configurar-rutas).
- [Creación Dockerfile](#docker-file).
- [Configuración dockeringore](#docker-ignore).
- [Cambiar inicio de la aplicación](#script-inicio).
- [Creación imagen docker](#docker-image).
- [Comandos docker utiles](#comandos-docker).
- [Ejecución imagen docker]($ejecutar-image-docker).
- [Entrar a contenedor docker](#entrar-docker).
- [muestras](#muestras).


### 1.Instalación Docker
  - En Windows:
  
  - En Linux:
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

### Iniciar proyecto NodeJS
