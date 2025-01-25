# Proyecto de Microservicios con NestJS

Este proyecto está construido utilizando [NestJS](https://nestjs.com/) y está organizado en dos repositorios separados para promover la modularidad y reutilización a través de microservicios backend.

## Repositorios

1. **services-common**
2. **services-api**

### 1. services-common

Contiene funcionalidades y utilidades comunes que pueden ser reutilizadas en múltiples microservicios backend.

#### Estructura de Directorios

services-common/ 
└── src/ 
    ├── auth-decorators/ 
    ├── filters/ 
    ├── guards/ 
    ├── models/ 
    ├── pipes/ 
    ├── roles/ 
    ├── logger/ 
    ├── constants.ts 
    ├── index.ts 
    └── swagger.config.ts



#### Descripción

- **auth-decorators/**: Decoradores personalizados para autenticación.
- **filters/**: Filtros de excepciones globales.
- **guards/**: Guards de autenticación y autorización.
- **models/**: Modelos de datos compartidos.
- **pipes/**: Pipes de validación y transformación.
- **roles/**: Utilidades para control de acceso basado en roles.
- **logger/**: Utilidades de registro de logs.
- **constants.ts**: Constantes compartidas.
- **index.ts**: Punto de entrada para exportar módulos y servicios comunes.
- **swagger.config.ts**: Configuración de Swagger para documentación de la API.

### 2. services-api

El microservicio API principal que utiliza los repo common proporcionados por `services-common`.

#### Estructura de Directorios

services-api/ 
    └── src/ 
        ├── models/ 
        │ └── user/ 
        │      ├── user.entity.ts 
        │      └── user.repository.ts 
        ├── dtos/ 
        │     └── user/ 
        │          └── user.dto.ts 
        ├── schemas/ 
        │      └── user/ 
        │          └── user.schema.ts 
        ├── modules/ 
        │      └── user/ 
        │            ├── user.controller.ts 
        │            ├── user.service.ts 
        │            ├── use-case/ 
        │            │     ├── user.create.usecase.ts 
        │            │     ├── user.update.usecase.ts 
        │            │     └── user.delete.usecase.ts 
        │            └── user.module.ts 
        ├── app.module.ts 
        └── main.ts

#### Descripción

- **models/user/**: Contiene la entidad User y el repositorio para interacciones con la base de datos.
- **dtos/user/**: Data Transfer Objects para operaciones relacionadas con usuarios.
- **schemas/user/**: Definiciones de esquemas de Mongoose u otros para el modelo User.
- **modules/user/**:
  - **user.controller.ts**: Maneja las solicitudes HTTP relacionadas con usuarios.
  - **user.service.ts**: Contiene la lógica de negocio para operaciones de usuarios.
  - **use-case/**: Implementaciones específicas de casos de uso para crear, actualizar y eliminar usuarios.
  - **user.module.ts**: Define el módulo de Usuario y sus dependencias.
- **app.module.ts**: Módulo raíz de la aplicación.
- **main.ts**: Punto de entrada de la aplicación.

## Inicio Rápido

### Prerrequisitos

- [Node.js](https://nodejs.org/) (v14 o superior)
- [npm](https://www.npmjs.com/) o [Yarn](https://yarnpkg.com/)
- [Git](https://git-scm.com/)

### Instalación

1. **Clonar los Repositorios**

   ```bash
   git clone https://github.com/tuusuario/services-common.git
   git clone https://github.com/tuusuario/services-api.git


