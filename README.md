# Comandos SQL

## ¿Qué son los comandos SQL?

Los comandos SQL ordenan a un sistema de gestión de bases de datos (DBMS por sus siglas en inglés: Database Management Systems) que realice determinadas acciones. Esto incluye definir tablas y sus estructuras, así como introducir, modificar y eliminar datos y ejecutar consultas.

El alcance que tienen los comandos SQL viene definido en varias normas ISO o ANSI. Además, hay una serie de dialectos de implementación específicos. Por ejemplo, las implementaciones de los principales fabricantes como PostgreSQL, MySQL, Oracle DBMS y Microsoft SQL Server traen cada uno sus propias variantes del lenguaje. Algunos tienen sus propios comandos; la mayoría, difieren al menos respecto a las funciones para procesar strings y otros datos.

De hecho, SQL consta de varios sublenguajes; cada uno de ellos cubre diferentes áreas y cuenta con sus propios comandos. Veamos los tipos de comandos SQL más importantes.

## ¿Qué tipos de comandos SQL existen?

Los comandos SQL más importantes pueden dividirse, a grandes rasgos, en cinco sublenguajes. Veamos los ámbitos de aplicación de cada uno de los sublenguajes y sus comandos respectivos:

### Data Definition Language (DDL)
* Comandos para definir el esquema de la base de datos: crear, modificar y eliminar tablas de la base de datos; definir claves primarias, claves externas y limitaciones (constraints).
* Ejemplo => CREATE TABLE, DROP TABLE


### Data Manipulation Language (DML)
* Comandos de manipulación de datos: modificar, insertar y eliminar registros.
* Ejemplo => INSERT, UPDATE

### Data Query Language (DQL)
* Comandos para consultar y acondicionar los datos.
* Ejemplo => SELECT

### Data Control Language (DCL)
* Comandos para la gestión de derechos.
* Ejemplo => GRANT, REVOKE

### Transaction Control Language (TCL)
* Comandos para el control de las transacciones.
* Ejemplo => COMMIT, ROLLBACK

## ¿Cuál es la sintaxis básica de los comandos SQL?

A diferencia de los lenguajes de programación más comunes, SQL es un lenguaje declarativo. Esto significa que describe el resultado que debe alcanzarse sin especificar exactamente qué pasos deben llevarse a cabo para lograrlo. Esta característica especial del lenguaje se refleja en su tendencia a que los comandos sean más largos; a cambio, a menudo se requieren menos líneas de código que con los lenguajes imperativos convencionales.

Como ejemplo ilustrativo, nos remitimos al siguiente comando SQL: DROP TABLE IF EXISTS. Has leído bien, es un comando que se utiliza únicamente para eliminar una tabla si ya existe:

```
DROP TABLE IF EXISTS SomeTable;
```

Un código de ejemplo en Python con una funcionalidad similar incluye varias solicitudes a funciones y consta de una extensión mayor a dos líneas:

```
if db.has_table(some_table):
    db.drop_table(some_table)
```

Como se ha visto, un solo comando SQL puede estar compuesto por varias palabras clave. Esto lleva a una apariencia similar entre dichos comandos. He aquí un ejemplo: Los comandos SQL CREATE TABLE y CREATE OR REPLACE VIEW parecen a primera vista expresiones derivadas y subordinadas de un comando hipotético CREATE. Sin embargo, este no es el caso. A pesar de su similitud, se trata de comandos independientes.

Al igual que en otros lenguajes, algunos comandos SQL admiten parámetros adicionales. Suelen ser nombres de bases de datos, tablas o columnas. Por ejemplo, solicitamos las columnas “Name” y “Age” de la tabla “People”:

```
SELECT Name, Age FROM People;
```

En el sentido estricto de la palabra, los comandos SQL son sentencias. A mayores, hay otras construcciones sintácticas, algunas de las cuales actúan como comandos. Te mostramos una visión general de los elementos más importantes que conforman la sintaxis SQL:

### Sentencia o Statement
* Ordena al DBMS que realice una acción; termina con un punto y coma.
* Ejemplo => CREATE TABLE People;

### Cláusula o Clause
* Modifica una instrucción; solo puede aparecer dentro de una instrucción.
* Ejemplo => WHERE, HAVING

### Expresión o Expression
* Retorna un valor al ser evaluada.
* Ejemplo => 6 * 7

### Identificador o Identifier
* Nombre de un objeto, variable o procedimiento de la base de datos; puede ser cualificado o no cualificado.
* Ejemplo => dbname.tablename / tablename

### Predicado o Predicate
* Expresión que se evalúa como TRUE, FALSE o UNKNOWN.
* Ejemplo => Age < 42

### Consulta o Query
* Instrucción especial; retorna un conjunto de registros como resultado.
* Ejemplo => SELECT Name FROM People WHERE Age < 42;

### Función o Function
* Procesa uno o más valores; normalmente crea un nuevo valor.
* Ejemplo => UPPER('text') -- Devuelve 'TEXT'

### Comentario o Comment
* Se utiliza para hacer comentarios en el código SQL; el RDBMS lo ignora.
* Ejemplo => -- Comentario al final de la línea / /* Si es necesario, comentario de varias líneas */

_______

# Comandos SQL para definir datos

Las bases de datos estructuran los datos dentro de una jerarquía de capas de almacenamiento, desde el servidor de la base de datos hasta el valor almacenado en un campo. Dado que todos los aspectos de un sistema de gestión de bases de datos relacionales (RDBMS) pueden controlarse mediante SQL, existen comandos SQL para cada una de las capas. Te mostramos una visión general de la jerarquía de los objetos RDBMS:

### Servidor
* Bases de datos

### Base de datos
* Tablas
 
### Tabla
* Registros

### Registro
* Campos

### Campo
* Valores tipificados

Además de los objetos RDBMS principales mencionados anteriormente, también se utilizan otros objetos como las vistas (“Views”) y los procedimientos almacenados (“Stored Procedures”). Estos también tienen sus propios comandos SQL. A continuación, nos adentraremos en los comandos de los cinco sublenguajes principales de SQL:

1. Data Definition Language (DDL) – Lenguaje de definición de datos
2. Data Manipulation Language (DML) – Lenguaje de manipulación de datos
3. Data Query Language (DQL) – Lenguaje de solicitud de datos
4. Data Control Language (DCL) – Lenguaje de control de datos
5. Transaction Control Language (TCL) – Lenguaje de control de transacciones

## Comandos SQL para definir las bases de datos

### Crear Base de Datos
Crea una nueva base de datos.
```
CREATE DATABASE Store;
```

### Usar Base de Datos
Selecciona la base de datos para el siguiente comando.
```
USE Store;
```

### Borrar una Base de Datos
Borra una base de datos al completo.
```
DROP DATABASE Store;
```

_______

## Comandos SQL para definir tablas

### Crear Tabla
Crea una nueva tabla en la base de datos; además del nombre de la tabla, se definen los nombres de las columnas junto con sus tipos
```
CREATE TABLE Customers(
    CustomerID INT UNSIGNED NOT NULL AUTO_INCREMENT, 
    CustomerName VARCHAR(255) NOT NULL, 
    Country VARCHAR(60) NOT NULL, 
    PRIMARY KEY (CustomerID) );
```

### Modifica una Tabla
Modifica una tabla existente: añade/elimina columnas; cambia el tipo o el nombre de una columna
```
ALTER TABLE Customers ADD Email VARCHAR(50);
```

### Elimina los Registros de una Tabla
Elimina todos los registros de una tabla; conserva la estructura de la tabla en el proceso
```
TRUNCATE TABLE Customers ;
```

### Elimina la Tabla
Elimina la tabla por completo; genera un error al ejecutarse si la tabla no existe
```
DROP TABLE Customers;
```

### Elimina la Tabla si Existe
Elimina la tabla si existe
```
DROP TABLE IF EXISTS Customers;
```

### Modifica el tipo de dato de una Columna
Cambia el tipo de dato de una columna existente
```
ALTER COLUMN Customers ALTER COLUMN Email VARCHAR(255);
```

### Borra una Columna
Borra la columna de una tabla al completo
```
DROP COLUMN Customers DROP COLUMN Email;
```

### Crea una Indice
Crea un índice para la(s) columna(s) de una tabla existente y le asigna un nombre
```
CREATE INDEX IdxEmail ON Customers (Email);
```

### Elimina un Indice Existente
Elimina un índice existente
```
ALTER TABLE Customers DROP INDEX IdxEmail;
```

### Clausulas para establecer limitaciones en cada columna

### NOT NULL
* Establece que el valor del campo no pueda ser NULL.

### UNIQUE
* Establece que el valor del campo dentro de la columna no puede aparecer dos veces.

### DEFAULT
* Establece un valor por defecto para el campo; de esta forma, si no se especifica ningún valor para el campo se utilizará el valor por defecto al crear el registro.

### CHECK
* Establece una condición que el valor del campo debe cumplir.

### PRIMARY KEY
* Especifica que el campo contiene la clave primaria; esto implica UNIQUE y NOT NULL.

### FOREIGN KEY
* Establece que el valor del campo debe ser una clave primaria de otra tabla.

_______

## Comandos SQL para la manipulación de datos

### Insertar Registros
Inserta un registro en la tabla
```
INSERT INTO Customers (CustomerName) VALUES ('Tester');
```

### Modificar Registros
Modifica los campos de uno o varios registros
```
UPDATE Customers SET Email = 'test@example.com' WHERE CustomerName = 'Tester';
```

### Eiminar Registros
Elimina registros de una tabla
```
DELETE FROM Customers WHERE CustomerName = 'Tester';
```

_______

## Comandos SQL para consultar datos

### Consultar en la Base de Datos
Consulta datos de la base de datos
```
SELECT CustomerName FROM Customers;
```

### Consultar en la Base de Datos especificas
Limita la consulta a los registros que cumplen un determinado criterio
```
SELECT Email FROM Customers WHERE CustomerName = 'Tester';
```

### Definir alias en una consulta
Define un alias para una tabla o fila durante una consulta
```
SELECT CustomerID AS ID, CustomerName AS Customer FROM Customers;
```

### Consultar con datos conjuntos
Limita la consulta a los conjuntos de datos pertinentes con la función de agregación
```
SELECT COUNT(CustomerID), Country FROM Customers HAVING COUNT(CustomerID) >= 1;
```

_______

## Comandos SQL para refinar las consultas

### Elimina los resultados duplicados
Elimina los duplicados del conjunto de resultados
```
SELECT DISTINCT Country FROM Customers;
```

### Limita la cantidad de resultados
Restringe el conjunto de resultados a los primeros resultados
```
SELECT * FROM Customers LIMIT 5;
```

### Agrupa resultados con caracteristicas comunes
Agrupa el conjunto de resultados según una característica común
```
SELECT CustomerName, Country FROM Customers GROUP BY Country;
```

### Ordena resultados con caracteristicas comunes
Ordena el conjunto de resultados según una característica
```
SELECT CustomerName, Email FROM Customers SORT BY CustomerName;
```

### Organiza los resultados en orden ascendente
Utiliza el orden ascendente (“ascending”)
```
SELECT DISTINCT Country FROM Customers SORT BY Country ASC;
```

### Organiza los resultados en orden descendente
Utilizar el orden descendente (“descending”)
```
SELECT DISTINCT Country FROM Customers SORT BY Country DESC;
```

_______

## Comandos SQL para unir consultas

### UNION
* Combina dos conjuntos de resultados; los conjuntos de resultados deben tener columnas del mismo tipo en el mismo orden. Sus filas están unidas.

### INNER JOIN
* Filtra dos conjuntos de resultados según un criterio común.

### LEFT JOIN
* Vincula el conjunto de resultados de la consulta de la izquierda con los resultados coincidentes de la consulta de la derecha; los campos no coincidentes se fijan como NULL.

### RIGHT JOIN
* Vincula el conjunto de resultados de la consulta de la derecha con los resultados que coinciden de la consulta de la izquierda; los campos que no coinciden se fijan como NULL.

### FULL OUTER JOIN
* Combina el LEFT JOIN y el RIGHT JOIN.

_______

## Comandos SQL para guardar y repetir consultas

### Crear una nueva Vista
Crea una nueva vista
```
CREATE VIEW SpanishCustomers AS SELECT CustomerName, Email FROM Customers WHERE Country = "ES";
```

### Modificar una Vista
Modifica una vista existente
```
ALTER VIEW SpanishCustomers AS SELECT * FROM Customers WHERE Country = "ES";
```

### Crea o remplaza una Vista
Crea una nueva vista o sustituye una vista existente, si procede.
```
CREATE OR REPLACE VIEW SpanishCustomers AS SELECT * FROM Customers WHERE Country = "ES";
```

### Muestra el Comando que creo una Vista
Muestra el comando SQL utilizado para crear una vista
```
SHOW CREATE VIEW SpanishCustomers;
```

### Elimina una Vista
Elimina una vista existente
```
DROP VIEW SpanishCustomers;
```

## Procedimientos Almacenados

### CREATE PROCEDURE
* Crea un nuevo procedimiento.

### ALTER PROCEDURE
* Modifica un procedimiento existente.

### CREATE OR REPLACE PROCEDURE
* Crea un nuevo procedimiento o sustituye un procedimiento existente, si procede.

### DROP PROCEDURE
* Elimina un procedimiento existente.

### CALL
* Ejecuta un procedimiento almacenado.

_______

## Comandos SQL para el control de acceso

### Asigna los derechos (permisos) para los usuarios
Asignar derechos 
```
GRANT ALL ON SomeDB.* TO 'john'@'localhost';
```

### Quita los derechos (permisos) para los usuarios
Quitar derechos
```
REVOKE INSERT ON *.* FROM 'john'@'localhost';
```

_______

## Comandos SQL para controlar transacciones

### Inicia una Transaccion
Marca el inicio de una transacción
```
START TRANSACTION;
```

### Completar una Transaccion Iniciada
Completa con éxito una transacción ya iniciada
```
START TRANSACTION; TRUNCATE TABLE Customers; COMMIT;
```

### Cancela una Transaccion Iniciada
Cancela una transacción previamente iniciada y devuelve el conjunto de datos a su estado inicial
```
START TRANSACTION; TRUNCATE TABLE Customers; ROLLBACK;
```

### Guarda un punto durante la Transaccion
Crea un punto de guardado durante una transacción y le asigna un nombre
```
START TRANSACTION; SAVEPOINT BeforeAddData;
```

### Guarda un punto indicando su nombre
Volver a un punto de guardado indicando su nombre
```
ROLLBACK TO BeforeAddData;
```

## Propiedades ACID

### ATOMICITY
* Las transacciones son “indivisibles”. Se ejecutan de forma completa o no se ejecutan en absoluto. Si se cancela una transacción atómica, el sistema se encuentra en el estado anterior al inicio de la transacción.

### CONSISTENCY
* Tras ejecutar una transacción, el stock de datos vuelve a estar disponible de forma consistente.

### ISOLATION
* Las operaciones realizadas al mismo tiempo no deben influirse mutuamente.

### DURABILITY
* Los efectos de una transacción deben quedar de forma permanente en el stock de datos. Los efectos de una transacción exitosa no deben perderse si, por ejemplo, el RDBMS se bloquea.

_______

Para mas informacion consultar https://www.ionos.es/digitalguide/servidores/configuracion/comandos-sql/