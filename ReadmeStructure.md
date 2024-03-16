# User API en Java con Spring Boot

Este proyecto es una API REST creada con Spring Boot, Spring Data JPA, Spring Web y MySQL. Permite realizar operaciones CRUD para una entidad `User`.

## Tecnologías Utilizadas

- Java
- Spring Boot
- Spring Data JPA
- Spring Web
- MySQL
- Maven

## Requisitos

Para construir y ejecutar la aplicación necesitas:

- JDK 1.8 o superior
- Maven 3.x 
- MySQL 5.x o superior

## Configuración

### Base de Datos

Primero, crea una base de datos en MySQL:

```sql
CREATE DATABASE sd3;

use sd3;

CREATE TABLE `sd3`.`users` (
  `id` VARCHAR(36) NOT NULL,
  `name` VARCHAR(200) NOT NULL,
  `login` VARCHAR(20) NOT NULL,
  `password` VARCHAR(100) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE INDEX `id_UNIQUE` (`id` ASC) VISIBLE
);
```
### application-dev.properties
````
spring.datasource.url=jdbc:mysql://localhost:3306/sd3?useSSL=false
spring.datasource.username=<TU_USUARIO>
spring.datasource.password=<TU_CONTRASEÑA>
spring.jpa.hibernate.ddl-auto=update
````
## Structure
````
📦src
┣ 📂main
┃ ┣ 📂java
┃ ┃ ┣ 📂jala
┃ ┃ ┃ ┣ 📂university
┃ ┃ ┃ ┃ ┣ 📂api
┃ ┃ ┃ ┃ ┃ ┣ 📂controller
┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜UserController.java       # Controlador para las operaciones del CRUD.
┃ ┃ ┃ ┃ ┃ ┣ 📂dto
┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜UserDTO.java             # Objeto de transferencia de datos para User.
┃ ┃ ┃ ┃ ┃ ┣ 📂model
┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜User.java               # Entidad JPA para User.
┃ ┃ ┃ ┃ ┃ ┣ 📂repository
┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜UserRepository.java      # Repositorio JPA para operaciones de base de datos.
┃ ┃ ┃ ┃ ┃ ┣ 📂service
┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜UserService.java        # Servicio con lógica de negocio para User.
┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜UserServiceImpl.java    # Implementación del servicio de User.
┃ ┃ ┃ ┃ ┃ ┗ 📂util
┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜UserMapper.java         # Mapper para convertir entidades en DTOs y viceversa.
┃ ┃ ┃ ┃ ┗ 📜UserApiJavaApplication.java # Clase principal de la aplicación Spring Boot.
┃ ┣ 📂resources
┃ ┃ ┣ 📜application.properties          # Configuración de la aplicación Spring Boot.

````
## Ejecución
Para ejecutar la aplicación, usa el siguiente comando en la raíz del proyecto:
````shell
mvn spring-boot:run
````

### Ejemplo de Api Rest en Java

https://gitlab.com/RodrigoML/market-spring.git
https://github.com/mariazevedo88/travels-java-api.git

# Users API Documentation

## Endpoints

La siguiente documentación describe cómo interactuar con la API de usuarios.

### Obtener Todos los Usuarios

**GET /users/all**

Este endpoint retorna todos los usuarios registrados en la base de datos.

Ejemplo de uso con `curl`:

````http request
curl -X GET http://localhost:8090/users-rest/api/users/all
````

### Obtener Usuario por ID

**GET /users/details/{id}**

Obtiene un usuario específico por su ID único.

Ejemplo de uso con `curl`:

````http request
curl -X GET http://localhost:8090/users-rest/api/users/details/1
````

### Crear Nuevo Usuario

**POST /users/save**

Crea un nuevo usuario con la información proporcionada.

Ejemplo de uso con `curl` y un payload de muestra:

````http request
curl -X POST http://localhost:8090/users-rest/api/users/save
-H "Content-Type: application/json"
-d '{"name":"John Doe", "login":"johndoe", "password":"securepassword"}'
````

### Actualizar Usuario

**PUT /users/update/{id}**

Actualiza la información del usuario con el ID proporcionado.

Ejemplo de uso con `curl` y un payload de muestra:

````http request
curl -X PUT http://localhost:8090/users-rest/api/users/update/1
-H "Content-Type: application/json"
-d '{"name":"John Doe Updated", "login":"johndoeupdated", "password":"newsecurepassword"}'
````

### Eliminar Usuario

**DELETE /users/delete/{id}**

Elimina el usuario con el ID especificado.

Ejemplo de uso con `curl`:

````http request
curl -X DELETE http://localhost:8090/users-rest/api/users/delete/1
````
