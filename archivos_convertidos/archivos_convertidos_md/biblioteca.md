```sql
-- Diagrama relacional a SQL de biblioteca

-- Crear base de datos de una Biblioteca
CREATE DATABASE Biblioteca;


-- Utilizar base de datos de la biblioteca
USE Biblioteca;

-- Crear tabla de Lectores
CREATE TABLE Lectores
(
idLector int primary key,
nom varchar(30) not null,
ape1 varchar(30) not null,
ape2 varchar(30) not null,
idMembresia varchar(30) not null
);


-- Crear tabla de Libro
CREATE TABLE Libro
(
idlibro int primary key,
idISBN int not null,
tit varchar(30) not null,
autor varchar(30) not null,
idLector int not null,
FOREIGN KEY (idLector)
REFERENCES Lectores(idLector)
);


```