# Bienvenido al coding-interview-backend-level-3

## Descripción
Este proyecto es una API REST que permite realizar operaciones CRUD sobre una entidad de tipo `Item`.

La entidad tiene 3 campos: `id`, `name` y `price`.

Tu tarea es completar la implementación de toda la funcionalidad de forma tal de que los tests e2e pasen exitosamente.


## Installation

# Configuración del Entorno de Desarrollo con .devcontainer

Este documento explica cómo configurar un entorno de desarrollo en **Visual Studio Code** utilizando un archivo **.devcontainer**, para gestionar **Node.js 20.18.1**

---

## **Requisitos previos**

Antes de comenzar, asegúrate de tener instalado:

1. [Docker](https://www.docker.com/)  
2. [Visual Studio Code](https://code.visualstudio.com/)  
3. Extensión de **Remote - Containers** en Visual Studio Code. Instálala desde [Visual Studio Code Extensions Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers).

---

## **Configuración del .devcontainer**

### 1. Crear el directorio `.devcontainer`

En tu proyecto, crea una carpeta llamada `.devcontainer` y dentro de esta, agrega los siguientes archivos:

#### **1.1. Archivo `devcontainer.json`**
Crea un archivo `devcontainer.json` con el siguiente contenido:

```json
{
	"name": "Coding Interview Backend Level 3",
	"build": {
	  "dockerfile": "Dockerfile",
	  "context": ".."
	},
	"forwardPorts": [3000],
	"postCreateCommand": "npm install",
	"remoteUser": "node",
	"features": {
	  "ghcr.io/devcontainers/features/node:1": {
		"version": "20.18.1"
	  }
	}
  }
```

#### **1.2. Archivo `Dockerfile`**
Crea un archivo `Dockerfile` con el siguiente contenido:

```bash
FROM node:20

# Install basic development tools
RUN apt update && apt install -y less man-db sudo

# Ensure default `node` user has access to `sudo`
ARG USERNAME=node
RUN echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# Set `DEVCONTAINER` environment variable to help with orientation
ENV DEVCONTAINER=true
```





```bash
# instalacion de dependencias
$ npm i
# o
$ yarn install

# creación del archivo .env basado en el archivo .env.example
$ cp .env.example .env

# ------ paso opcional -------
# si no tiene una base de datos, puede crear una docker-compose.yml 
# archivo basado en el docker-compose.yml.example archivo en el proyecto


# Nota: si se ejecuta directamente desde docker el backend el host de base de dato
# en el archivo ormconfig.json debe ir asi
# "host": "postgresql",
# si se encuentra en fuera de docker
# "host": "localhost",

$ cp docker-compose.yml.example docker-compose.yml
$ docker-compose up

# debe haber instalado previamente docker y docker-compose en
# tu ordenador, para que funcione correctamente, si todo está correcto
# debe tener lista la base de datos de su proyecto.
# ------ paso opcional -------

# ejecución de migraciones
$ npm run migrate:up
# o
$ yarn migrate:up

# ejecución de seeds
$ npm run seed:run

# ------ step optional -------
```

## Running the app

```bash
# development
$ npm run dev

# production mode
$ npm run build
$ npm run start
```

## Endpoints

```bash
# the default paths of the project are:
$ http://localhost:3000/api/v1/user              # POST
$ http://localhost:3000/api/v1/technical         # POST
$ http://localhost:3000/api/v1/service           # POST
$ http://localhost:3000/api/v1/orde              # POST
$ http://localhost:3000/api/v1/service           # GET
$ http://localhost:3000/api/v1/technical/orders  # GET

Documentación en Swagger 
$ http://localhost:3000/api/docs
```

## Test

```bash
# unit tests
$ npm run test
```