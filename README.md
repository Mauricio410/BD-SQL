# Comandos SQL para definir datos

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
