# Universidad Tecnológica de Durango
## Desarrollo en Gestión de Software  
### Administración de Base de Datos  
### Proyecto

---

### Alumnos
- Alvarado Gutiérrez Edith Alejandra  
- Meraz Marrufo Raquel Yolanda  
- Bonilla Domínguez María Fernanda  
- Muñoz Torres Mónica Mariana  
- Valles Yáñez Gael Emmanuel  

**8°A**  

**Docente:**  
- Ing. Antonio Alberto Vásquez Orozco  

---

## Índice
1. [Resumen](#resumen)  
2. [Introducción](#introducción)  
3. [Análisis y Requerimientos](#análisis-y-requerimientos)  
4. [Diseño de la Base de Datos](#diseño-de-la-base-de-datos)  
5. [Tecnologías y Herramientas](#tecnologías-y-herramientas)  
6. [Implementación](#implementación)  
7. [Seguridad y Respaldo](#seguridad-y-respaldo)  
8. [Conclusiones y Recomendaciones](#conclusiones-y-recomendaciones)  
9. [Anexos](#anexos)  
10. [Referencias](#referencias)  

---

## Resumen

### Breve introducción al propósito del documento
Este documento tiene como objetivo describir la estructura inicial de la base de datos desarrollada en PostgreSQL. Se detallará el diseño de las tablas, sus relaciones y estrategias de optimización, seguridad y escalabilidad para garantizar un sistema eficiente y robusto.

La base de datos gestionará información de productos, usuarios y operaciones relacionadas dentro de un e-commerce.

### Resumen de los principales hallazgos

1. **Estructura inicial bien definida:** Tablas principales: `productos`, `usuario`, `carrito`, `inventario`, `disponibilidad`, `estatus`, `cita`.
2. **Optimización y rendimiento:** Se implementarán índices en columnas clave como `id_producto`, `id_usuario`, `id_carrito`, `estatus`.
3. **Gestión de inventario y disponibilidad:** Relaciones entre `productos`, `inventario` y `disponibilidad` para reflejar el stock en tiempo real.

### Rendimiento y optimización
- **Índices en columnas clave:** `id_producto`, `id_usuario`, `id_carrito`, `id_inventario`, `estatus`.
- **Normalización de datos:** Se aplicará 1FN, 2FN y 3FN para reducir redundancia y asegurar integridad.

---

## Introducción

### Objetivo del documento
Proveer una descripción técnica de la base de datos del sitio web administrable. Servirá como guía para su diseño e implementación en PostgreSQL, enfocándose en estructura, seguridad y escalabilidad.

### Alcance del proyecto
La base de datos gestionará:
- Usuarios y permisos
- Páginas y contenido
- Configuración del sitio
- Registros de auditoría

### Beneficios esperados
- Gestión eficiente de contenido
- Seguridad en el acceso
- Escalabilidad para futuras funciones

### Público objetivo
- Administradores del sitio
- Usuarios visitantes
- Contenido orientado a mujeres y chicas (moda, salud, bienestar)

---

## Análisis y Requerimientos

### Descripción y necesidad de la base de datos
La base de datos será la infraestructura central para el almacenamiento y gestión de toda la información del sitio web administrable, brindando una estructura organizada y eficiente para todos los datos que se generarán, procesarán y consumen dentro del sitio.

#### Función principal
La base de datos almacenará información crítica para el funcionamiento del sitio, incluyendo:
•	Datos de usuarios (tales como registros, autenticaciones, roles y permisos).
•	Contenido del sitio web (páginas, artículos, imágenes, videos, y otros recursos multimedia).

#### Necesidades clave
1.	Centralización de la información: La DB reunirá toda la información clave del sitio en un solo lugar, lo que facilitará el acceso y la gestión eficiente del contenido y de los datos de los usuarios. 
2.	Control y personalización del contenido: La DB permitirá que los administradores y editores gestionen el contenido del sitio de manera eficiente, ajustando temas, creando nuevas publicaciones, modificando secciones específicas y organizando artículos según el público objetivo del sitio.
3.	Seguridad y gestión de accesos: Dado que el sitio administra información sensible de los usuarios y contenido privado, la base de datos debe garantizar niveles de seguridad adecuados. 
4.	Auditoría y trazabilidad: La base de datos deberá incluir registros detallados de los cambios realizados en el contenido y configuración del sitio, lo cual es crucial para la gestión adecuada del sitio y para la transparencia de las acciones de los administradores y editores.
 

### Requerimientos funcionales

- **Gestión de usuarios y roles:** Creación de cuentas con distintos niveles de acceso (administrador, visitante).
- **Administración de contenido:** Creación, edición y eliminación de páginas y secciones del sitio.
- **Configuración del sitio:** Modificación de temas, estilos y preferencias de funcionamiento.
- **Registro de actividad:** Almacenamiento de acciones realizadas por los usuarios administradores.
- **Soporte multimedia:** Carga y almacenamiento de imágenes y archivos utilizados en el contenido.

### Requerimientos no funcionales

- **Disponibilidad:** El sistema debe estar operativo 24/7 con un alto tiempo de actividad.
- **Escalabilidad:** La base de datos debe permitir la expansión del sitio sin pérdida de rendimiento.
- **Seguridad:** Implementación de cifrado de datos y restricciones de acceso para proteger información sensible.
- **Optimización de consultas:** Uso de índices y estrategias de caché para mejorar la velocidad de carga del sitio.
- **Compatibilidad:** Debe ser posible integrar la base de datos con otras herramientas de administración o análisis.

### Seguridad y acceso a la información

Para proteger la integridad y privacidad de los datos almacenados, se aplicarán las siguientes medidas:

- **Control de acceso basado en roles:** Solo los administradores tendrán permisos completos, mientras que los editores y usuarios tendrán accesos limitados.
- **Respaldo y recuperación de datos:** Mecanismos automáticos de Backus para prevenir pérdida de información en caso de fallos.
- **Protección contra inyección SQL:** Uso de consultas parametrizadas para evitar ataques de seguridad.


---

## Diseño de la Base de Datos

![image](https://github.com/user-attachments/assets/951375c1-d821-4f3e-b5c2-20664f5f979a)

### Diccionario de Datos

#### Tabla: `usuarios`
| Campo       | Tipo de dato     | Descripción                         |
|-------------|------------------|-------------------------------------|
| id_usuario  | SERIAL (PK)      | Identificador único                 |
| nombre      | VARCHAR(255)     | Nombre completo                     |
| correo      | VARCHAR(255)     | Correo electrónico (único)          |
| telefono    | VARCHAR(12)      | Teléfono de contacto                |
| password    | VARCHAR(255)     | Contraseña encriptada               |
| fecha       | TIMESTAMP        | Fecha de registro                   |
| rol         | BOOLEAN          | Rol (true: admin, false: cliente)   |

#### Tabla: `vestidos`
| Campo         | Tipo de dato     | Descripción               |
|---------------|------------------|---------------------------|
| id_vestido    | SERIAL (PK)      | ID del vestido            |
| nombre        | VARCHAR(255)     | Nombre del vestido        |
| precio        | NUMERIC(10,2)    | Precio                    |
| tallas        | VARCHAR(50)      | Tallas disponibles        |
| categoria     | VARCHAR(100)     | Categoría (boda, fiesta)  |
| marca         | VARCHAR(100)     | Marca del vestido         |
| imagen        | VARCHAR(255)     | URL de imagen             |
| descripcion   | TEXT             | Descripción del vestido   |
| disponibilidad| BOOLEAN          | Disponibilidad en stock   |

#### Tabla: `carrito`
| Campo       | Tipo de dato     | Descripción               |
|-------------|------------------|---------------------------|
| id_carrito  | SERIAL (PK)      | ID del carrito            |
| id_usuario  | INTEGER (FK)     | Usuario dueño             |
| agregado    | TIMESTAMP        | Fecha de creación         |

#### Tabla: `carrito_productos`
| Campo        | Tipo de dato     | Descripción               |
|--------------|------------------|---------------------------|
| id_carrito   | INTEGER (FK)     | ID del carrito            |
| id_vestido   | INTEGER (FK)     | ID del vestido            |
| cantidad     | INTEGER          | Cantidad de unidades      |

#### Tabla: `citas`
| Campo        | Tipo de dato     | Descripción               |
|--------------|------------------|---------------------------|
| id_cita      | SERIAL (PK)      | ID de la cita             |
| id_usuario   | INTEGER (FK)     | Usuario que agenda        |
| fecha_cita   | DATE             | Fecha programada          |
| hora         | TIME             | Hora de la cita           |

#### Tabla: `cita_productos`
| Campo      | Tipo de dato     | Descripción               |
|------------|------------------|---------------------------|
| id_cita    | INTEGER (FK)     | ID de la cita             |
| id_vestido | INTEGER (FK)     | Vestido reservado         |
| cantidad   | INTEGER          | Cantidad reservada        |

#### Tabla: `movimientos_inventario`
| Campo         | Tipo de dato     | Descripción               |
|---------------|------------------|---------------------------|
| id_movimiento | SERIAL (PK)      | ID del movimiento         |
| id_vestido    | INTEGER (FK)     | Vestido afectado          |
| tipo          | TEXT             | 'entrada' o 'salida'      |
| cantidad      | INTEGER          | Cantidad de vestidos      |
| fecha         | TIMESTAMP        | Fecha del movimiento      |

### Normalización y optimización
•	1FN: Todas las tablas tienen valores atómicos (no repetidos).
•	2FN: Todos los atributos dependen completamente de la clave primaria.
•	3FN: No existen dependencias transitivas.
•	Se utilizaron claves foráneas para mantener integridad referencial.
•	Tablas intermedias (carrito_productos, cita_productos) para relaciones muchos-a-muchos.
•	Se recomienda crear índices en campos como id_usuario, id_vestido y id_cita para acelerar consultas.
 
---

## Tecnologías y Herramientas

### Sistema de Gestión de Bases de Datos
**PostgreSQL**  
PostgreSQL, es una base de datos de código abierto que tiene una sólida reputación por su fiabilidad, flexibilidad y soporte de estándares técnicos abiertos. A diferencia de otros RDMBS (sistemas de gestión de bases de datos relacionales), PostgreSQL (enlace externo a ibm.com) soporta tipos de datos relacionales y no relacionales. Esto la convierte en una de las bases de datos relacionales más compatibles, estables y maduras disponibles actualmente.

Desarrollada originalmente en 1986 como continuación de INGRES POSTGRES, ahora conocida como PostgreSQL, fue una creación de Michael Stonebraker, profesor de informática en Berkeley. En 1994, el proyecto agregó soporte para SQL y, poco después, surgió PostgreSQL.

Hoy, PostgreSQL continúa evolucionando, mantenido por un equipo internacional apasionado por mejorar con regularidad este proyecto de base de datos de código abierto y gratuito. 
Mantener sistemas de bases de datos dinámicos es fundamental en el panorama digital actual, especialmente considerando la velocidad a la que surgen nuevas tecnologías. PostgreSQL es expandible y versátil, por lo que puede soportar rápidamente una variedad de casos de uso especializados con un poderoso ecosistema de extensión, que abarca desde tipos de datos de series de tiempo hasta análisis geoespaciales.
Su diseño versátil y accesible convierte a PostgreSQL en una solución de "talla única" para muchas empresas que buscan formas rentables y eficientes de mejorar sus sistemas de gestión de bases de datos. Creada como una solución de base de datos de código abierto (enlace externo a ibm.com), PostgreSQL está completamente libre de restricciones de licencia, potencial de bloqueo de proveedores o riesgo de implementación excesiva. Los desarrolladores expertos y las empresas comerciales que son conscientes de las limitaciones de los sistemas de bases de datos tradicionales apoyan firmemente PostgreSQL. Trabajan diligentemente para proporcionar el mejor sistema en su clase de gestión de bases de datos relacionales probado sobre el terreno.

**Ventajas:**
- Libre de licencias restrictivas
- Compatible con extensiones especializadas
- Ideal para sistemas escalables y dinámicos

### Lenguajes y frameworks relacionados

**Lenguajes compatibles:**
- SQL  
- Python (Psycopg2)  
- JavaScript / Node.js (Sequelize)  
- Java (Hibernate)  
- PHP (Laravel - Eloquent)  
- Ruby (Ruby on Rails)

**Frameworks y herramientas para trabajar con PostgreSQL:**
- Django (Python)
- Flask + SQLAlchemy (Python)
- Express.js + Sequelize (Node.js)
- Laravel (PHP)

---
## Instalación y configuración del SGBD

### Instalación de PostgreSQL
# Guía de Instalación de PostgreSQL

Este proyecto utiliza **PostgreSQL** como sistema de gestión de base de datos relacional (RDBMS). 
A continuación, se describen los pasos para su instalación en diferentes sistemas operativos.

---

## Descargar el Instalador

1. Ve a la página oficial de PostgreSQL:  
[https://www.postgresql.org/download/](https://www.postgresql.org/download/)

2. Selecciona tu sistema operativo (por ejemplo, **Windows**).

3. Descarga el instalador de la última versión disponible.

---

## Ejecutar el Instalador

1. Abre el archivo `.exe` descargado.
2. Sigue las instrucciones del asistente de instalación.

### Componentes recomendados:

-  PostgreSQL Server  
- pgAdmin (interfaz gráfica)  
- Stack Builder (opcional)

---

## Configurar la Instalación

- Elige la carpeta de instalación (puedes dejar la predeterminada).
- Establece una **contraseña para el usuario `postgres`** (¡guárdala bien!).
- Selecciona el puerto de conexión (por defecto es `5432`).
- Finaliza la instalación.

---

## Verificar la Instalación

1. Abre **pgAdmin** desde el menú de inicio.
2. Conéctate usando el usuario `postgres` y la contraseña que configuraste.

---


   ![image](https://github.com/user-attachments/assets/1d0f0d97-762f-4d55-8c3a-36e75e553ea8)

### Creación de la estructura de la DB (scripts o esquemas)
```sql
-- Tabla: usuarios
CREATE TABLE usuarios (
    id_usuario SERIAL PRIMARY KEY,
    nombre VARCHAR(255) NOT NULL,
    correo VARCHAR(255) UNIQUE NOT NULL,
    telefono VARCHAR(12),
    password VARCHAR(255) NOT NULL,
    fecha TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    rol BOOLEAN NOT NULL
);

-- Tabla: vestidos
CREATE TABLE vestidos (
    id_vestido SERIAL PRIMARY KEY,
    nombre VARCHAR(255) NOT NULL,
    precio NUMERIC(10,2) NOT NULL,
    tallas VARCHAR(50),
    categoria VARCHAR(100),
    marca VARCHAR(100),
    imagen VARCHAR(255),
    descripcion TEXT,
    disponibilidad BOOLEAN NOT NULL
);

-- Tabla: carrito
CREATE TABLE carrito (
    id_carrito SERIAL PRIMARY KEY,
    id_usuario INTEGER NOT NULL,
    agregado TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (id_usuario) REFERENCES usuarios(id_usuario) ON DELETE CASCADE
);

-- Tabla: carrito_productos
CREATE TABLE carrito_productos (
    id_carrito INTEGER NOT NULL,
    id_vestido INTEGER NOT NULL,
    cantidad INTEGER NOT NULL CHECK (cantidad > 0),
    PRIMARY KEY (id_carrito, id_vestido),
    FOREIGN KEY (id_carrito) REFERENCES carrito(id_carrito) ON DELETE CASCADE,
    FOREIGN KEY (id_vestido) REFERENCES vestidos(id_vestido) ON DELETE CASCADE
);

-- Tabla: citas
CREATE TABLE citas (
    id_cita SERIAL PRIMARY KEY,
    id_usuario INTEGER NOT NULL,
    fecha_cita DATE NOT NULL,
    hora TIME NOT NULL,
    FOREIGN KEY (id_usuario) REFERENCES usuarios(id_usuario) ON DELETE CASCADE
);

-- Tabla: cita_productos
CREATE TABLE cita_productos (
    id_cita INTEGER NOT NULL,
    id_vestido INTEGER NOT NULL,
    cantidad INTEGER NOT NULL CHECK (cantidad > 0),
    PRIMARY KEY (id_cita, id_vestido),
    FOREIGN KEY (id_cita) REFERENCES citas(id_cita) ON DELETE CASCADE,
    FOREIGN KEY (id_vestido) REFERENCES vestidos(id_vestido) ON DELETE CASCADE
);

-- Tabla: movimientos_inventario
CREATE TABLE movimientos_inventario (
    id_movimiento SERIAL PRIMARY KEY,
    id_vestido INTEGER NOT NULL,
    tipo TEXT CHECK (tipo IN ('entrada', 'salida')) NOT NULL,
    cantidad INTEGER NOT NULL CHECK (cantidad > 0),
    fecha TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (id_vestido) REFERENCES vestidos(id_vestido) ON DELETE CASCADE
);
```
###Pruebas de Inserción y Consulta de Datos


### 1. Inserción de Datos de Prueba

Se ingresaron registros de prueba para verificar el correcto funcionamiento de las relaciones entre las tablas y las restricciones de integridad. A continuación, un resumen de las acciones realizadas:

- **Usuarios**: Se insertaron dos usuarios, uno con rol de administrador y otro como cliente.
- **Vestidos**: Se agregaron vestidos con distintas tallas, precios, categorías y marcas.
- **Carrito**: Se creó un carrito vinculado a un usuario específico.
- **Carrito Productos**: Se agregaron vestidos al carrito con cantidades válidas.
- **Citas**: Se registraron citas con fecha y hora asignadas a usuarios.
- **Cita Productos**: Se asociaron vestidos específicos a cada cita.
- **Movimientos de Inventario**: Se realizaron registros de entrada de inventario para controlar el stock.

### 2. Consultas Realizadas para Verificación

Se realizaron consultas básicas para validar que los datos se insertaron correctamente y las relaciones funcionen según lo esperado:

- Consulta de todos los usuarios registrados.
- Consulta de vestidos disponibles (disponibilidad = true).
- Consulta del contenido del carrito por usuario (unión entre varias tablas).
- Consulta de citas agendadas por usuario, incluyendo fecha y hora.
- Consulta del historial de movimientos de inventario, ordenado por fecha.

Estas pruebas confirmaron que la estructura de la base de datos funciona correctamente con los tipos de datos y claves foráneas definidas, y que las inserciones cumplen con las restricciones (por ejemplo, cantidades positivas).

