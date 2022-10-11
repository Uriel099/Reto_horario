# Reto rest api alumnos

para este reto vamos a crear una api en la que unicamente registraremos una curricula escolar que esta conformada por cuatro tablas: 
 * carrera
 * materias
 * grupo
 * horario

El modelo de base de datos entidad relacional es el siguiente

<p style = 'text-align:center;'>
    <img src='BD_alumnos_er.jpg' style='text-align: center'>
</p>

El modelo relacional es el siguiente

<p style = 'text-align:center;'>
    <img src='BD_relacional.jpg' style='text-align: center'>
</p>

pueden obtener el código para generar la base de datos en el archivos bd.sql en este reporitorio o en el siguiente fragmento de código

~~~sql
CREATE DATABASE Reto;

USE Reto;

CREATE TABLE Carrera(
    ID_Carrera int NOT NULL AUTO_INCREMENT,
    Nombre varchar(200),
    Duracion int,
    PRIMARY KEY(ID_Carrera)
);

CREATE TABLE Materia(
    ID_Materia int NOT NULL AUTO_INCREMENT,
    Nombre varchar(200),
    Grado int,
    ID_Carrera int,
    PRIMARY KEY(ID_Materia),
    FOREIGN KEY(ID_Carrera) REFERENCES Carrera(ID_Carrera)
);

CREATE TABLE Grupo(
    ID_Grupo int,
    Nombre varchar(200),
    Grado int,
    PRIMARY KEY(ID_Grupo)
);

CREATE TABLE Horario(
    ID_Horario int NOT NULL AUTO_INCREMENT,
    Hora int,
    Dia int,
    ID_Grupo int,
    ID_Materia int,
    PRIMARY KEY(ID_Horario),
    FOREIGN KEY(ID_Grupo) REFERENCES Grupo(ID_Grupo),
    FOREIGN KEY(ID_Materia) REFERENCES Materia(ID_Materia)
);
~~~