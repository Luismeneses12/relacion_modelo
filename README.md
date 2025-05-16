# 📚 Classroom API - Spring Boot Project

Este proyecto es una API RESTful desarrollada con **Spring Boot** orientada a la gestión académica. Incluye el manejo de usuarios, estudiantes, docentes, materias, cursos, asistencias, calificaciones e inscripciones.

## 🚀 Tecnologías Utilizadas

* **Spring Boot** como framework principal
* **Maven** como entorno de construcción
* **Spring Data JPA** para la conexión y manipulación de bases de datos
* **MySQL** como base de datos principal
* **H2** para pruebas en memoria
* **IntelliJ IDEA Community** como entorno de desarrollo
* **XAMPP** para gestión de base de datos local con MySQL

---

## 🧱 Estructura del Proyecto

El proyecto está organizado en paquetes que siguen el patrón MVC (Modelo-Vista-Controlador), y cada entidad principal tiene su propia capa:

```
com.example.classRoomApi
🔼── controller/
│   └── EstudianteController.java, DocenteController.java, ...
🔼── model/
│   └── Usuario.java, Estudiante.java, Materia.java, ...
🔼── repository/
│   └── EstudianteRepository.java, CursoRepository.java, ...
🔼── service/
│   └── EstudianteService.java, CursoService.java, ...
🔼── utils/
    └── Help.java, TipoUsuario.java (Enum), ...
```

### ✅ Cada entidad tiene:

* Su propia clase `@Entity`
* Un `Repository` que extiende `JpaRepository`
* Un `Service` para la lógica de negocio
* Un `Controller` con los endpoints REST

---

## 🔁 Relaciones entre Entidades

* **Usuario** tiene una relación `@OneToOne` con `Estudiante` y `Docente`.
* **Estudiante** tiene relaciones:

  * `@OneToMany` con `Asistencia`, `Inscripcion`, `Calificaciones`
* **Docente** tiene relación `@OneToMany` con `Curso`
* **Curso** se relaciona con `Materia`, `Docente`, `Estudiante`
* **Materia** tiene relación con `Curso` y `Calificaciones`
* **Inscripcion** enlaza a `Estudiante` y `Curso`

Estas relaciones permiten una navegación fluida entre entidades para consultas complejas.

---

## 🧠 Componentes Especiales

### 🔧 `Help.java`

Clase utilitaria para brindar soporte y ayuda dentro del sistema (por ejemplo, mensajes, validaciones o conversiones comunes).

### 📁 `Enum` TipoUsuario

Se utiliza para definir y verificar el tipo de usuario (`ESTUDIANTE`, `DOCENTE`, etc.), aportando validación adicional a través de anotaciones `@Enumerated`.

---

## 💻 Conexión a la Base de Datos

Se usó **XAMPP + MySQL** como servidor de base de datos. La conexión se configuró en el archivo `application.properties`:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/classroom
spring.datasource.username=root
spring.datasource.password=
spring.jpa.hibernate.ddl-auto=update
```

          
