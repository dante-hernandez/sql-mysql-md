```sql
-- Diagrama relacional de Empresa

-- Crear base de datos de Empresa

CREATE DATABASE Empresa1;


-- Utilizar base de datos

USE Empresa1;

-- Crear tabla Department
CREATE TABLE Department
(
idberDepta int primary key,
NameDepto varchar(20) UNIQUE NOT NULL,
idssn char(12),
stardate DATE,

);


-- Crear tabla de Employee
CREATE TABLE Employee
(
idssn CHAR(12) primary key,
FirstName varchar(20) not null,
LastName varchar(20) not null,
Address1 varchar(50) not null,
BirtDate date,
Salary money not null,
Sex char(1) not null,
NumDepto  int not null,
NameDepto varchar(20) not null,
supervisor CHAR(12),
CHECK (Sex in('M', 'F')),
FOREIGN KEY(NumDepto)
REFERENCES Department(idberDepta),
FOREIGN KEY(supervisor)
REFERENCES Employee(idssn)
);




-- CREAR tabla DeptLocation
CREATE TABLE DeptLocation
(
NumDepto int not null,
NameDepto varchar(20) not null,
DLocation nvarchar(20) not null,
FOREIGN KEY(idDepto)
REFERENCES Department(idberDepta),

);


-- Crear tabla Project
CREATE TABLE Project
(
idberProject int primary key,
nameProject nvarchar(40),
location1 nvarchar(40),
idDepto int,
nameNumber nvarchar(30),
FOREIGN KEY (idDepto)
REFERENCES Department(idberDepta)
);


-- Crear tabla Works_On
CREATE TABLE Works_On
(
idssn char(12),
idProject int,
nameProject nvarchar(20),
horas DECIMAL(5,2),
PRIMARY KEY (idssn, idProject),
FOREIGN KEY (idssn)
REFERENCES Employee(idssn),
FOREIGN KEY (idProject)
REFERENCES Project(idberProject)
);


-- Crear tabla Dependent
CREATE TABLE Dependent1
(
idssn char(12),
name1 varchar(20),
relationship char(1) not null,
sex char(1),
birthdate DATE,
CHECK (relationship in('C', 'D', 'S', 'V')),
CHECK (sex in('M', 'F')),
PRIMARY KEY (idssn, name1),
FOREIGN KEY (idssn)
REFERENCES Employee(idssn)
);

```