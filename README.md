<div align="center">

# 📋 Freedom · Sistema de Gestión de Tareas

### *Aplicación web para la creación, organización y seguimiento de tareas de equipos de trabajo*

![Java](https://img.shields.io/badge/Java-21-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.5-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring%20Security-JWT-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-3.8-C71A36?style=for-the-badge&logo=apache-maven&logoColor=white)
![Licencia](https://img.shields.io/badge/Licencia-MIT-22C55E?style=for-the-badge&logo=open-source-initiative&logoColor=white)

</div>

---

## 📑 Tabla de contenidos

- [📌 Descripción](#descripcion)
- [✨ Características principales](#caracteristicas)
- [🔑 Credenciales de demostración](#credenciales)
- [🛠️ Tecnologías utilizadas](#tecnologias)
- [🏗️ Arquitectura](#arquitectura)
- [📁 Estructura del proyecto](#estructura)
- [📋 Requisitos previos](#requisitos)
- [⚙️ Configuración](#configuracion)
- [🚀 Ejecución](#ejecucion)
- [✅ Verificación](#verificacion)
- [🤝 Contribución](#contribucion)
- [📄 Licencia](#licencia)

---

<h2 id="descripcion">📌 Descripción</h2>

**Freedom · Sistema de Gestión de Tareas** es una aplicación web full-stack construida con **Spring Boot** que permite a los equipos crear, organizar y dar seguimiento a sus tareas de forma eficiente. Cada usuario administra sus propias tareas con prioridades, estados y etiquetas, apoya su planificación mediante un calendario interactivo y un sistema de alertas, y cuenta con un panel de administración para la gestión integral de usuarios.

Incluye autenticación segura con **Spring Security y tokens JWT**, diferenciando roles de **usuario** y **administrador**.

---

<h2 id="caracteristicas">✨ Características principales</h2>

- **CRUD completo de tareas**: creación, edición, actualización y eliminación.
- **Prioridad, estado y etiquetas**: clasificación de tareas (Alta/Media/Baja, Pendiente/En Proceso/Completada) y etiquetas personalizadas.
- **Búsqueda, filtros y ordenación**: filtrado por título, estado, prioridad y etiqueta; orden dinámico por cualquier columna.
- **Calendario interactivo**: visualización de tareas por fecha de vencimiento con colores según estado y prioridad.
- **Alertas de vencimiento**: notificaciones de tareas próximas a vencer o vencidas en la barra de navegación.
- **Panel de resumen**: estadísticas de tareas totales, completadas y pendientes en la página principal.
- **Papelera de reciclaje**: eliminación suave, restauración y borrado permanente de tareas.
- **Limpieza automática**: tarea programada que elimina permanentemente las tareas que superan los 20 días en la papelera.
- **Gestión de usuarios y roles**: registro de usuarios, edición de perfil y asignación de rol administrador.
- **Panel de administración**: administra usuarios y sus tareas desde una interfaz exclusiva.
- **Tema claro/oscuro**: modo visual configurable por el usuario.

---

<h2 id="credenciales">🔑 Credenciales de demostración</h2>

Al iniciar la aplicación por primera vez, el sistema crea automáticamente los siguientes usuarios de demostración:

| Usuario | Contraseña | Rol |
|---------|------------|-----|
| `admin` | `Admin123!` | Administrador |
| `demo1` | `Demo123!` | Usuario |
| `demo2` | `Demo123!` | Usuario |

---

<h2 id="tecnologias">🛠️ Tecnologías utilizadas</h2>

| Tecnología | Propósito |
|------------|-----------|
| **Java 21** | Lenguaje de programación |
| **Spring Boot 3.5** | Framework de la aplicación |
| **Spring MVC** | Manejo de controladores y vistas |
| **Spring Security** | Autenticación y autorización |
| **JWT (jjwt 0.12)** | Emisión y validación de tokens |
| **Spring Data JPA / Hibernate** | Persistencia y mapeo objeto-relacional |
| **MySQL 8** | Base de datos relacional |
| **Thymeleaf** | Motor de plantillas del lado del servidor |
| **Bootstrap 4 / Font Awesome** | Interfaz de usuario y estilos |
| **FullCalendar** | Calendario interactivo de tareas |
| **Maven** | Gestión de dependencias y build |

---

<h2 id="arquitectura">🏗️ Arquitectura</h2>

La aplicación sigue una **arquitectura en capas** (estilo MVC), con separación clara de responsabilidades:

```
Controller  →  Service  →  Repository  →  Entidad (JPA)
```

- **Controller**: gestiona las peticiones HTTP, la autenticación y devuelve vistas o respuestas JSON.
- **Service**: contiene la lógica de negocio, validaciones y transacciones.
- **Repository**: abstracción de acceso a datos con Spring Data JPA.
- **Security**: doble cadena de filtros — una *stateless* con **JWT** para los endpoints `/api/**` y una basada en **sesión HTTP** para la aplicación web.
- **DTO**: objetos de transferencia de datos entre la API y el frontend.

Además, se utilizan **tareas programadas** (`@Scheduled`) para la limpieza automática de la papelera.

---

<h2 id="estructura">📁 Estructura del proyecto</h2>

```
📁 Raíz del proyecto
├── pom.xml                     # Configuración de Maven y dependencias
├── .env.example                # Plantilla de credenciales locales (.env)
└── src/
    └── main/
        ├── java/com/freedom/tareas/
        │   ├── TareasApplication.java          # Clase principal
        │   ├── config/                         # Configuración (Security, PasswordEncoder, DataLoader)
        │   ├── controller/                     # Controladores MVC y REST
        │   ├── model/                          # Entidades JPA (User, Task, Role)
        │   ├── repository/                     # Repositorios Spring Data
        │   ├── security/                       # Filtros y utilidades JWT
        │   ├── service/                        # Lógica de negocio
        │   └── dto/                            # Objetos de transferencia de datos
        └── resources/
            ├── application.properties.example  # Plantilla de configuración
            ├── static/                         # CSS, JavaScript e imágenes
            └── templates/                      # Vistas Thymeleaf
```

---

<h2 id="requisitos">📋 Requisitos previos</h2>

| Requisito | Versión mínima |
|-----------|----------------|
| Java JDK | 21 |
| Maven | 3.8+ (o usar el wrapper `mvnw` incluido) |
| MySQL | 8.0+ |

---

<h2 id="configuracion">⚙️ Configuración</h2>

1. **Crear la base de datos**: la URL de conexión incluye `createDatabaseIfNotExist=true`, por lo que la base de datos `freedombd` se crea automáticamente al primer arranque. Las tablas se generan mediante Hibernate (`ddl-auto=update`).

   > [!TIP]
   > No es necesario crear la base de datos manualmente: la aplicación la genera y actualiza el esquema en el primer inicio.

2. **Crear el archivo de configuración local** a partir de la plantilla:

```bash
cp src/main/resources/application.properties.example src/main/resources/application.properties
```

3. **Crear el archivo `.env`** en la raíz del proyecto (junto al `pom.xml`) a partir de la plantilla `.env.example`, y completar los valores de tu entorno local:

```bash
cp .env.example .env
```

   | Variable | Descripción | Ejemplo |
   |----------|-------------|---------|
   | `JWT_SECRET` | Clave secreta para firmar los tokens JWT | `openssl rand -base64 48` |
   | `DB_USERNAME` | Usuario de MySQL | `root` |
   | `DB_PASSWORD` | Contraseña de MySQL | `root` |

   > [!WARNING]
   > `.env` está en `.gitignore`, por lo que tus credenciales nunca se suben a GitHub. Solo la plantilla `.env.example` se versiona.

---

<h2 id="ejecucion">🚀 Ejecución</h2>

### Opción 1: Con el wrapper de Maven (recomendado)

```bash
# Compilar el proyecto
./mvnw clean compile

# Ejecutar la aplicación
./mvnw spring-boot:run
```

### Opción 2: Con Maven instalado

```bash
mvn clean compile
mvn spring-boot:run
```

### Opción 3: Generar el JAR ejecutable

```bash
./mvnw clean package
java -jar target/freedom-task-manager-1.0.0.jar
```

> [!NOTE]
> Una vez iniciada, la aplicación estará disponible en **http://localhost:8080**.

---

<h2 id="verificacion">✅ Verificación</h2>

- Accede a `http://localhost:8080`.
- Inicia sesión con las credenciales de demostración (ver sección anterior).
- Explora las secciones **Inicio**, **Mis Tareas**, **Nueva Tarea**, **Calendario** y **Papelera**.
- Inicia sesión como `admin` para acceder al **Modo Admin**.

---

<h2 id="contribucion">🤝 Contribución</h2>

1. Haz un *fork* del repositorio.
2. Crea una rama para tu funcionalidad: `git checkout -b feature/nueva-funcionalidad`.
3. Realiza los cambios y haz *commit*.
4. Envía tus cambios: `git push origin feature/nueva-funcionalidad`.
5. Abre un *Pull Request*.

---

<h2 id="licencia">📄 Licencia</h2>

Este proyecto está bajo la licencia **MIT**. Consulta el archivo [LICENSE](LICENSE) para más información.

---

<div align="center">

**Freedom · Sistema de Gestión de Tareas** · Desarrollado por [Jeanpierre Chipa](https://github.com/devjtd)

Hecho con ❤️ y ☕ usando **Spring Boot**

</div>
