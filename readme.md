# Operaciones sobre base de datos de una instalación de Odoo

1. Crear tabla EmpresasFCT

Sentencia:

````
CREATE TABLE EmpresasFCT (
    idEmpresa SERIAL PRIMARY KEY,
    nombre VARCHAR(40) NOT NULL,
    quiereAlumnos BOOLEAN,
    numAlumnos INTEGER,
    fechaContacto DATE
);
````

Comprobación:

![Imagen](images/a9.png)


