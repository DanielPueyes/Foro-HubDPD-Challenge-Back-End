# 💬 Challenge ForoHub - Alura Latam | ONE Oracle Next Education

**Estado:** En desarrollo  
**Lenguaje:** Java 17  
**Release Date:** Agosto

---

## 🚀 Descripción del Proyecto
**ForoHub** es una API REST desarrollada en **Java 17** con **Spring Boot**, como parte del programa **Java Backend Developer** de **Oracle Next Education** y **Alura Latam**.  
El objetivo es implementar una plataforma para la gestión de tópicos de discusión, aplicando autenticación con **JWT** y operaciones CRUD seguras, siguiendo buenas prácticas de arquitectura y desarrollo backend.

---

## ⚙️ Funcionalidades
- **🔐 Autenticación de Usuario (Login)** → Obtención de **JSON Web Token (JWT)** para acceder a las funciones protegidas.
- **➕ Registrar Tópicos** → `POST /topicos` para agregar nuevos datos a la base de datos.
- **📋 Listar Tópicos** → `GET /topicos` para obtener todos los registros.
- **✏️ Actualizar Tópico** → `PUT /topicos/{id}` para modificar un tópico existente.
- **🗑️ Eliminar Tópico** → `DELETE /topicos/{id}` para eliminar un registro.

> **Nota:** Todas las operaciones (excepto el login) requieren autenticación mediante JWT en la cabecera de la petición.

---

## 🛠️ Flujo de Ejecución de la Aplicación

1. El usuario se registra o inicia sesión mediante `/login`.
2. El servidor responde con un **JWT** válido.
3. El usuario utiliza el token en la cabecera `Authorization: Bearer {token}` para acceder a los endpoints protegidos.
4. Dependiendo del método HTTP:
    - **GET:** Obtiene la lista de tópicos.
    - **POST:** Crea un nuevo tópico.
    - **PUT:** Actualiza un tópico por su `id`.
    - **DELETE:** Elimina un tópico por su `id`.
5. El servidor responde con datos en formato **JSON**.

---

## 📌 Ejemplos de Uso de la API

### 1️⃣ Login de Usuario
**POST** `/login`  
**Request:**
```json
{
  "email": "usuario@example.com",
  "password": "123456"
}
Response:


{
  "token": "eyJhbGciOiJIUzI1NiIsInR..."
}
2️⃣ Registrar un Tópico
POST /topicos
Headers:
Authorization: Bearer {token}
Request:


{
  "titulo": "Error al iniciar sesión en la plataforma",
  "mensaje": "No puedo acceder con mi cuenta, muestra error 403.",
  "autor": "Juan Pérez",
  "curso": "Java Backend"
}
Response:


{
  "id": 1,
  "titulo": "Error al iniciar sesión en la plataforma",
  "mensaje": "No puedo acceder con mi cuenta, muestra error 403.",
  "autor": "Juan Pérez",
  "curso": "Java Backend",
  "fechaCreacion": "2025-08-12T14:30:00"
}
3️⃣ Listar Tópicos
GET /topicos
Headers:
Authorization: Bearer {token}
Response:


[
  {
    "id": 1,
    "titulo": "Error al iniciar sesión en la plataforma",
    "mensaje": "No puedo acceder con mi cuenta, muestra error 403.",
    "autor": "Juan Pérez",
    "curso": "Java Backend",
    "fechaCreacion": "2025-08-12T14:30:00"
  },
  {
    "id": 2,
    "titulo": "Problema con la base de datos",
    "mensaje": "La conexión con MySQL se pierde después de 5 minutos.",
    "autor": "María López",
    "curso": "Spring Boot"
  }
]
4️⃣ Actualizar un Tópico
PUT /topicos/{id}
Headers:
Authorization: Bearer {token}
Request:



{
  "titulo": "Error al iniciar sesión - Corregido",
  "mensaje": "Problema resuelto, era un error de credenciales."
}
Response:


{
  "id": 1,
  "titulo": "Error al iniciar sesión - Corregido",
  "mensaje": "Problema resuelto, era un error de credenciales.",
  "autor": "Juan Pérez",
  "curso": "Java Backend",
  "fechaCreacion": "2025-08-12T14:30:00"
}
5️⃣ Eliminar un Tópico
DELETE /topicos/{id}
Headers:
Authorization: Bearer {token}
Response:


{
  "mensaje": "Tópico eliminado correctamente"
}
🏗️ Arquitectura del Proyecto
La aplicación sigue una arquitectura en capas para mantener la separación de responsabilidades:


src/
 ├── controller/       → Controladores REST que manejan las peticiones HTTP.
 ├── domain/           → Entidades y modelos de datos.
 ├── repository/       → Interfaces para acceso a datos con Spring Data JPA.
 ├── service/          → Lógica de negocio.
 ├── security/         → Configuración de seguridad y autenticación JWT.
 └── configuration/    → Configuración global de la aplicación.
Flujo general:

El cliente envía una petición HTTP.

El Controller recibe la solicitud y la pasa al Service.

El Service ejecuta la lógica de negocio y llama al Repository para interactuar con la base de datos.

El resultado se devuelve al cliente en formato JSON.

📜 Documentación de la API (Swagger)
La API cuenta con documentación interactiva generada automáticamente con SpringDoc OpenAPI.

Acceso a la documentación:


http://localhost:8080/swagger-ui.html
Funcionalidades de Swagger:

Probar endpoints desde el navegador.

Ver modelos de datos y ejemplos de respuesta.

Consultar parámetros y requerimientos de autenticación.

🔐 Seguridad con JWT
La API utiliza Spring Security y JWT para proteger los endpoints.
Proceso de autenticación:

El usuario envía credenciales en /login.

El servidor valida y genera un token JWT.

El cliente envía el token en la cabecera de cada petición protegida.

El servidor valida el token antes de procesar la solicitud.

🗄️ Base de Datos
RDBMS: MySQL

ORM: Spring Data JPA

Tablas principales:

usuarios

topicos

respuestas (si se implementa funcionalidad de respuestas)

✔️ Tecnologías Utilizadas
Java 17

Spring Boot

Spring Security + JWT

Spring Data JPA

Maven

MySQL

Insomnia (para pruebas de API)

Swagger / OpenAPI (documentación)

📌 Autor
Daniel Pueyes Díaz
💻 Técnico en Soporte y Desarrollo Backend
📌 Proyecto desarrollado para el programa ONE - Oracle Next Education con Alura Latam.