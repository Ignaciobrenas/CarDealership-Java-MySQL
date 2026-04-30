# ðŸš— Car Dealership Management System (Java DAO & MySQL via JDBC)

<p align="center">
  <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white" alt="Java" />
  <img src="https://img.shields.io/badge/Database-MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL" />
  <img src="https://img.shields.io/badge/Pattern-DAO_(Data_Access_Object)-047857?style=for-the-badge" alt="DAO" />
  <img src="https://img.shields.io/badge/Academic-1Âº_DAW_STUCOM-10B981?style=for-the-badge" alt="STUCOM" />
</p>

> ðŸŽ“ **Academic Project Notice:** Evaluative project for the **1st year of Web Application Development (DAW)** at **STUCOM Pelai** (Barcelona) within the Data Access module (MP0485 RA9: Relational Database Persistence).

---

## ðŸ“Œ Overview / DescripciÃ³n General

### ðŸ‡¬ðŸ‡§ English
An enterprise-style vehicle dealership persistence application in **Java**. It adopts the **DAO (Data Access Object)** design pattern to cleanly decouple business logic from the **MySQL** relational database layer accessed through **JDBC**.

### ðŸ‡ªðŸ‡¸ EspaÃ±ol
AplicaciÃ³n de gestiÃ³n de concesionario de vehÃ­culos en **Java** con persistencia relacional. Aplica el patrÃ³n de diseÃ±o **DAO (Data Access Object)** e interfaces para desacoplar completamente la lÃ³gica de negocio del acceso a la base de datos **MySQL** mediante **JDBC**.

---

## ðŸ›ï¸ Architectural Highlights

- **IDAO.java (Interface):** Defines the strict CRUD contract for persistence operations.
- **DAOSQL.java:** JDBC implementation managing prepared statements, connection lifecycles, transactions, and SQL error mapping.
- **Custom Exceptions:** Domain-specific exceptions (DAO_Excep, Read_SQL_DAO_Excep, Vehicle_Excep) preventing data corruption.
- **Concesionario.java & Vehiculo.java:** Core business entities with full validation.

---

## ðŸ—„ï¸ Database Setup

`sql
CREATE DATABASE IF NOT EXISTS concesionario;
USE concesionario;

CREATE TABLE IF NOT EXISTS vehiculos (
    matricula VARCHAR(10) PRIMARY KEY,
    marca VARCHAR(50) NOT NULL,
    modelo VARCHAR(50) NOT NULL,
    precio DECIMAL(10,2) NOT NULL,
    fecha_ingreso DATE
);
`

---

## ðŸš€ How to Run

1. Configure your MySQL credentials in DAOSQL.java (or connection config).
2. Run via Maven:
   `ash
   mvn clean compile
   mvn exec:java -Dexec.mainClass="com.mycompany.concesionario.Concesionario"
   `

---

## ðŸ“„ License

Distributed under the **MIT License**.
