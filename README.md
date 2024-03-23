# Comandos SQL para definir datos

## Comandos SQL para definir las bases de datos

### Crear Base de Datos
Crea una nueva base de datos.
```
CREATE DATABASE **Store**;
```

### Usar Base de Datos
Selecciona la base de datos para el siguiente comando.
```
USE **Store**;
```

### Borrar una Base de Datos
Borra una base de datos al completo.
```
DROP DATABASE **Store**;
```

_______

## Comandos SQL para definir tablas

### Crear Tabla
Crea una nueva tabla en la base de datos; además del nombre de la tabla, se definen los nombres de las columnas junto con sus tipos
```
CREATE TABLE **Customers**(
    CustomerID INT UNSIGNED NOT NULL AUTO_INCREMENT, 
    CustomerName VARCHAR(255) NOT NULL, 
    Country VARCHAR(60) NOT NULL, 
    PRIMARY KEY (CustomerID) );
```

### Modifica una Tabla
Modifica una tabla existente: añade/elimina columnas; cambia el tipo o el nombre de una columna
```
ALTER TABLE **Customers** ADD Email VARCHAR(50);
```

### Elimina los Registros de una Tabla
Elimina todos los registros de una tabla; conserva la estructura de la tabla en el proceso
```
TRUNCATE TABLE **Customers** ;
```

### Elimina la Tabla
Elimina la tabla por completo; genera un error al ejecutarse si la tabla no existe
```
DROP TABLE **Customers**;
```

### Elimina la Tabla si Existe
Elimina la tabla si existe
```
DROP TABLE IF EXISTS **Customers**;
```

### Modifica el tipo de dato de una Columna
Cambia el tipo de dato de una columna existente
```
ALTER COLUMN **Customers** ALTER COLUMN Email VARCHAR(255);
```

### Borra una Columna
Borra la columna de una tabla al completo
```
DROP COLUMN **Customers** DROP COLUMN Email;
```

### Crea una Indice
Crea un índice para la(s) columna(s) de una tabla existente y le asigna un nombre
```
CREATE INDEX IdxEmail ON Customers (Email);
```

### Elimina un Indice Existente
Elimina un índice existente
```
ALTER TABLE **Customers** DROP INDEX **IdxEmail**;
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
INSERT INTO **Customers (CustomerName)** VALUES ('Tester');
```

### Modificar Registros
Modifica los campos de uno o varios registros
```
UPDATE **Customers** SET **Email = 'test@example.com'** WHERE **CustomerName = 'Tester'**;
```

### Eiminar Registros
Elimina registros de una tabla
```
DELETE FROM **Customers** WHERE **CustomerName = 'Tester'**;
```

_______

## Comandos SQL para consultar datos

### 
```

```

### 
```

```

### 
```

```

### 
```

```

### 
```

```

### 
```

```

### 
```

```