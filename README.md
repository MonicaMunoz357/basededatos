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

1. **Estructura inicial bien definida:** La base de datos cuenta con una estructura lógica clara, compuesta por tablas fundamentales como usuarios, vestidos, tallas, carrito, carrito_productos, inventario_vestidos, movimientos_inventario, citas y cita_productos, permitiendo una gestión integral del sistema de renta/venta de vestidos.
2. **Optimización y rendimiento:** Se implementarán índices en columnas clave como `id_vestido`, `id_inventario`, `id_cita`, `id_usuario`, `id_carrito`, `estatus`.
3. **Gestión de inventario y disponibilidad:** El control del stock se logra a través de la relación entre vestidos, tallas, inventario_vestidos y movimientos_inventario, lo que permite reflejar la disponibilidad en tiempo real y registrar cada entrada o salida del almacén.

### Rendimiento y optimización
- **Índices en columnas clave:** `id_producto`, `id_usuario`, `id_carrito`, `id_inventario`, `estatus`.
- **Normalización de datos:** Se aplicará 1FN, 2FN y 3FN para reducir redundancia y asegurar integridad.

---

## Introducción

### Objetivo del documento
Proveer una descripción técnica de la base de datos utilizada en el desarrollo del sitio web administrable. Este documento servirá como guía para su diseño, implementación y mantenimiento dentro del sistema, haciendo énfasis en su estructura relacional, normalización, integridad de datos, seguridad y escalabilidad. 

### Alcance del proyecto
La base de datos gestionará:
- Usuarios y permisos
- Páginas y contenido
- Configuración del sitio
- Registros de auditoría

### Beneficios esperados
- Manejo fácil y ordenado del contenido y la información del sitio.
- Mayor seguridad al controlar quién puede ver o modificar los datos.
- Capacidad para agregar nuevas funciones o partes al sistema en el futuro sin complicaciones.
- Base de datos bien organizada, siguiendo reglas que evitan errores o datos repetidos.
- Información clara y ordenada que facilita hacer búsquedas, reportes y darle mantenimiento al sistema.

### Público objetivo
- Administradores del sitio: personas encargadas de subir productos, revisar citas y controlar todo el sistema.
- Usuarios visitante: personas que entran al sitio para ver, rentar o comprar vestidos.
- Mujeres y chicas interesadas en temas como moda que son el público principal del contenido del sitio.
---

## Análisis y Requerimientos

### Descripción y necesidad de la base de datos
La base de datos será la infraestructura central para el almacenamiento y gestión de toda la información del sitio web administrable, brindando una estructura organizada y eficiente para todos los datos que se generarán, procesarán y consumen dentro del sitio.

#### Función principal
La base de datos almacenará información crítica para el funcionamiento del sitio, incluyendo:
•	Datos de usuarios (tales como registros, autenticaciones, roles y permisos).
•	Contenido del sitio web (páginas, artículos, imágenes y otros recursos multimedia).

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

- **Control de acceso basado en roles:** Solo los administradores tendrán permisos completos, mientras que los usuarios tendrán accesos limitados.
- **Respaldo y recuperación de datos:** Mecanismos automáticos de Backus para prevenir pérdida de información en caso de fallos.
- **Protección contra inyección SQL:** Uso de consultas parametrizadas para evitar ataques de seguridad.


---

## Diseño de la Base de Datos

## Diagrama de flujo

![diagrama de flujo](https://github.com/user-attachments/assets/1b7822a0-4fa1-4d3b-81ae-c4deed2bb3ac)

Como se puede observar en la imagen, el sistema inicia con el ingreso de credenciales y, una vez validadas, dirige al usuario según su rol. Si es un usuario común, puede acceder al catálogo, seleccionar vestidos, agregarlos al carrito y confirmar una cita. Si es administrador, se le muestra un panel con opciones para publicar, actualizar vestidos o consultar el inventario. Cada usuario accede solo a las funciones correspondientes a su perfil, asegurando un flujo controlado y eficiente.


![bd](https://github.com/user-attachments/assets/70f26813-059b-43fd-b3f3-4fc26cb98cfc)

La base de datos representa el sistema del sitio web administrativo para la gestión de renta o venta de vestidos, permitiendo el control de usuarios (clientes y administradores), productos, inventario por tallas, movimientos de stock, carritos de compra y citas para probarse vestidos. Está estructurada con relaciones claras entre tablas, permitiendo una gestión eficiente del catálogo, la disponibilidad de prendas y la interacción de los usuarios con el sistema, lo que la hace ideal para operaciones comerciales y logísticas dentro de una tienda de moda o boutique en línea.


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
| categoria     | VARCHAR(100)     | Categoría (boda, fiesta)  |
| marca         | VARCHAR(100)     | Marca del vestido         |
| imagen        | VARCHAR(255)     | URL de imagen             |
| descripcion   | TEXT             | Descripción del vestido   |

#### Tabla: `talla`
| Campo       | Tipo de dato     | Descripción               |
|-------------|------------------|---------------------------|
| id_talla    | SERIAL (PK)      | ID del talla del vestido  |
| talla       | 	VARCHAR(10)     | Nombre/número de la talla |

#### Tabla: `inventario_vestido`
| Campo          | Tipo de dato     | Descripción                   |
|----------------|------------------|-------------------------------|
| id_vestido     | SERIAL (PK)      | ID del vestido                |
| id_talla       | INTEGER (FK)     | ID de la talla                |
| disponibilidad | INTEGER          | cantidad disponible           |
| id_inventario  | INTEGER          | identificardor del inventario |


#### Tabla: `movimientos_inventario`
| Campo         | Tipo de dato   | Descripción                 |
|---------------|----------------|-----------------------------|
| id_movimiento | SERIAL (PK)    | Identificador del movimiento|
| id_vestido    | INTEGER (FK)   | ID del vestido              |
| id_talla      | INTEGER (FK)   | ID de la talla              |
| cantidad      | INTEGER        |	Cantidad agregada o retirada|
| fecha         | TIMESTAMP      | Fecha del movimiento        |


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


### Normalización y optimización

Para garantizar una estructura eficiente, escalable y alineada con las buenas prácticas del diseño relacional, se planteó implementar un modelo de base de datos siguiendo los principios de normalización, hasta la Tercera Forma Normal (3FN). Esto implica que cada tabla contiene datos atómicos (1FN), que todos los campos dependen completamente de su clave primaria (2FN) y que no existen dependencias transitivas entre atributos no clave (3FN). 
Por ejemplo, el campo de tallas, originalmente almacenado como texto en la tabla de vestidos, se separó en una tabla propia relacionada mediante una tabla intermedia, permitiendo representar relaciones muchos a muchos de forma adecuada. Además, se definieron claves primarias y foráneas para mantener la integridad referencial, y se consideró el uso de índices en campos clave para mejorar el rendimiento de las consultas.



## Tecnologías y Herramientas

### Sistema de Gestión de Bases de Datos
**PostgreSQL**  
PostgreSQL, es una base de datos de código abierto que tiene una sólida reputación por su fiabilidad, flexibilidad y soporte de estándares técnicos abiertos. A diferencia de otros RDMBS (sistemas de gestión de bases de datos relacionales), PostgreSQL (enlace externo a ibm.com) soporta tipos de datos relacionales y no relacionales. Esto la convierte en una de las bases de datos relacionales más compatibles, estables y maduras disponibles actualmente.

Desarrollada originalmente en 1986 como continuación de INGRES POSTGRES, ahora conocida como PostgreSQL, fue una creación de Michael Stonebraker, profesor de informática en Berkeley. En 1994, el proyecto agregó soporte para SQL y, poco después, surgió PostgreSQL.

Hoy, PostgreSQL continúa evolucionando, mantenido por un equipo internacional apasionado por mejorar con regularidad este proyecto de base de datos de código abierto y gratuito. 
Mantener sistemas de bases de datos dinámicos es fundamental en el panorama digital actual, especialmente considerando la velocidad a la que surgen nuevas tecnologías. PostgreSQL es expandible y versátil, por lo que puede soportar rápidamente una variedad de casos de uso especializados con un poderoso ecosistema de extensión, que abarca desde tipos de datos de series de tiempo hasta análisis geoespaciales.
Su diseño versátil y accesible convierte a PostgreSQL en una solución de "talla única" para muchas empresas que buscan formas rentables y eficientes de mejorar sus sistemas de gestión de bases de datos. Creada como una solución de base de datos de código abierto (enlace externo a ibm.com), PostgreSQL está completamente libre de restricciones de licencia, potencial de bloqueo de proveedores o riesgo de implementación excesiva. Los desarrolladores expertos y las empresas comerciales que son conscientes de las limitaciones de los sistemas de bases de datos tradicionales apoyan firmemente PostgreSQL. Trabajan diligentemente para proporcionar el mejor sistema en su clase de gestión de bases de datos relacionales probado sobre el terreno.

Se eligió PostgreSQL por ser un sistema de base de datos robusto, de código abierto y altamente compatible con los estándares SQL. Su capacidad para manejar relaciones complejas, como la normalización entre vestidos y tallas, lo hace ideal para estructuras de datos bien definidas. Además, se integra fácilmente con tecnologías modernas como Node.js y Sequelize, lo que facilita su uso en aplicaciones web escalables y mantenibles.


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

