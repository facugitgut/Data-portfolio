La siguiente documentación registra la creación de una base de datos para una biblioteca, en donde se especifican las tablas a crear,
los registros de las mismas y el tipo de dato con el que se trabajarán. Para este proyecto personal se utilizó el motor SQL SERVER EXPRESS y 
el entorno SQL SERVER MANAGEMENT STUDIO (SSMS)

DIAGRAMA DE TABLAS

Para tener una visión de las tablas a crear y las relaciones que se utilizarán por medio de las claves foraneas, se realizó el siguiente esquema ilustrativo,
en donde se especifica en cada fila de cada tabla el nombre de la columna y el tipo de dato que almacenará

Libros
PK ID_libro INT IDENTITY (1,1) NOT NULL
Titulo VARCHAR (50) NOT NULL
FK ID_autor INT NOT NULL

Autores
PK ID_autor INT IDENTITY (1,1) NOT NULL
Nombre VARCHAR (50) NOT NULL
Apellido VARCHAR (50) NOT NULL

Préstamos
PK ID_prestamo INT IDENTITY (1,1) NOT NULL
FK ID_libro INT NOT NULL
Fecha_prestamo DATE NOT NULL
Fecha_devolucion DATE NOT NULL

Los enlaces presentes son:
ID_autor de la tabla Autores es clave primaria, y se vincula con ID_autor de la tabla Libros, que es clave foranea.
ID_libro de la tabla Libros es clave primaria, y se vincula con ID_libro de la tabla Préstamos, que es clave foranea.

CREACIÓN DE TABLAS

Se procede a crear las siguientes tablas a través de la sintaxis  de SQL Server, utilizando el entorno de SSMS.

Las siguientes líneas de código crean la tabla 'autores' con un campo ID_autor clave primaria auto incremental
con la restricción de no ser nulo, y el campo 'nombre_apellido' del tipo varchar con un máximo de 50 caracteres y
la restrición de no ser nulo.

CREATE TABLE autores(
	ID_autor INT PRIMARY KEY IDENTITY (1,1) NOT NULL,
	nombre_apellido VARCHAR(50) NOT NULL
);

Para la siguiente tabla se incluyó el campo ID_autor como clave foranea, especificando en la última línea que hace referencia
al campo ID_autor de la tabla 'autores'.

CREATE TABLE libros(
	ID_libro INT PRIMARY KEY IDENTITY (1,1) NOT NULL,
	titulo VARCHAR(50) NOT NULL,
	ID_autor INT NOT NULL,
	publicacion_year INT,
	FOREIGN KEY (ID_autor) REFERENCES autores(ID_autor)

CREACIÓN DE REGISTROS EN TABLAS

Una vez creadas las tablas 'libros' y 'autores', se prosigue con la creación de registros. 
Para la tabla 'libros' se insertan los siguientes registros. Notar que se obvia incluir en la sintaxis al campo 'ID_libros' 
por ser autoincremental, es decir, se crea automaticamente con cada nuevo registro y se incrementa en una unidad.


INSERT INTO libros(titulo, ID_autor)
VALUES ('El nombre del mundo es bosque',1),
('La rueda celeste',1),
('El mundo de Rocannon',1),
('Los desposeidos',1),
('La mano izquierda de la oscuridad',1),
('Un mago de terramar',1),
('Las tumbas de atuan',1),
('Aprendiz de asesino',2),
('Las naves de la magia',2),
('La mision del bufon',2),
('Guardianes de Dragones',2),
('El asesino del bufon',2),
('Piranesi',3),
('It',4),
('El resplandor',4),
('La torre oscura, el pistolero',4),
('La primera cronica',5),
('Sombras fluctuantes',5),
('La rosa blanca',5),
('El silmarillion',6),
('El hobbit',6),
('El señor de los anillos',6),
('Kalpa imperial',7),
('El imperio final',8),
('Elantris',8),
('Palabras radiantes',8);

La siguiente consulta es de prueba para ver que todo se registró correctamente.

SELECT ID_libro, titulo, ID_autor FROM libros

El resultado que devuelve es el siguiente: 

<img width="331" height="424" alt="consulta libros" src="https://github.com/user-attachments/assets/6484509c-3ba7-44d7-a08b-80c3114e9325" />

