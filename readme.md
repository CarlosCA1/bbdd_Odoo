# Operaciones sobre base de datos de una instalación de Odoo

1. Crear tabla EmpresasFCT.

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


2. Insertar registros.

Sentencia:

````
INSERT INTO EmpresasFCT (nombre, quiereAlumnos, numAlumnos, fechaContacto) VALUES
('Soluciones Tech', TRUE, 10, '2025-11-01'),
('Innova Group', FALSE, 0, '2025-10-15'),
('FutureLabs', TRUE, 5, '2025-11-20'),
('SmartTech', TRUE, 8, '2025-09-30'),
('Sistemas Alpha', FALSE, 2, '2025-11-10');
````

Comprobación:

![Imagen](images/a9.png)



