# 🚗 Concesionario de Vehículos – Java DAO & MySQL (JDBC)

<p align="center">
  <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white" alt="Java" />
  <img src="https://img.shields.io/badge/Database-MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL" />
  <img src="https://img.shields.io/badge/Pattern-DAO_Architecture-007396?style=for-the-badge" alt="DAO Pattern" />
  <img src="https://img.shields.io/badge/Academic-1º_DAW_STUCOM-10B981?style=for-the-badge" alt="STUCOM" />
</p>

> 🎓 **Proyecto Académico:** Desarrollado como práctica evaluativa para el **Resultado de Aprendizaje 9 (MP0485 RA9 - Persistencia en Bases de Datos Relacionales)** en **STUCOM Pelai** (Barcelona), 1º Grado Superior en Desarrollo de Aplicaciones Web (DAW).

---

## Descripción del Proyecto

Sistema integral de gestión de un concesionario de vehículos desarrollado en **Java**, implementando el patrón de diseño **DAO (Data Access Object)** para desacoplar completamente la capa de persistencia relacional en **MySQL** de la lógica de negocio y las vistas.

---

## Arquitectura del Proyecto

```
src/main/java/
├── controller/
│   └── Concesionario.java        # Controlador que orquesta las operaciones del sistema
├── dao/
│   ├── IDAO.java                 # Interfaz que define las operaciones CRUD del repositorio
│   └── DAOSQL.java               # Implementación JDBC con consultas SQL preparadas
├── model/
│   └── Vehiculo.java             # Entidad Vehículo con sus atributos y getters/setters
└── main/
    └── main.java                 # Punto de entrada de la aplicación
```

---

## Patrón DAO e Interfaz `IDAO`

El acceso a la base de datos se abstrae mediante la interfaz `IDAO`:
- `insertarVehiculo(Vehiculo v)`: Inserta un nuevo registro mediante `PreparedStatement` para prevenir inyecciones SQL.
- `obtenerVehiculos()`: Recupera la lista completa de vehículos mediante `ResultSet`.
- `buscarPorMatricula(String matricula)`: Consulta filtrada por clave única.
- `eliminarVehiculo(String matricula)`: Baja lógica o física del vehículo en la base de datos.

---

## Requisitos y Configuración de Base de Datos

1. Disponer de un servidor **MySQL** activo (puerto por defecto `3306`).
2. Crear la base de datos y la tabla de vehículos:

```sql
CREATE DATABASE IF NOT EXISTS concesionario;
USE concesionario;

CREATE TABLE IF NOT EXISTS vehiculos (
    matricula VARCHAR(10) PRIMARY KEY,
    marca VARCHAR(50) NOT NULL,
    modelo VARCHAR(50) NOT NULL,
    precio DOUBLE NOT NULL
);
```

3. Configurar credenciales de conexión en `DAOSQL.java`:
   - URL: `jdbc:mysql://localhost:3306/concesionario`
   - Usuario: `root`
   - Contraseña: *(la configurada en tu entorno local)*

---

## Compilación y Ejecución

```bash
# Compilar con Maven
mvn clean compile

# Ejecutar
mvn exec:java -Dexec.mainClass="main.main"
```

---

## Licencia

Distribuido bajo la **Licencia MIT**.
