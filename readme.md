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


3. Apartado 3:

Sentencia: 

````
SELECT * 
FROM EmpresasFCT
ORDER BY fechaContacto DESC;
````

Comprobación:

![Imagen](images/a9.png)

4. Apartado 4:

Sentencia:

````
SELECT 
    rp.name AS nombre_contacto,
    rp.city AS ciudad,
    rc.name AS nombre_comercial_empresa
FROM res_partner rp
INNER JOIN res_partner rc ON rp.parent_id = rc.id
WHERE 
    rp.is_company = FALSE
    AND rp.city <> 'Tracy'
ORDER BY 
    rc.name ASC;
````

Esta consulta selecciona tres columnas: rp.name que es el nombre del contacto, rp.city que es la ciudad del contacto, y rc.name que es el nombre de la empresa asociada, renombrada como nombre_comercial_empresa. La tabla base es res_partner, a la que se le asigna el alias rp para referirse a los contactos de manera más corta; se hace un INNER JOIN con la misma tabla usando el alias rc para obtener la empresa asociada mediante rp.parent_id = rc.id, asegurando que solo se incluyan contactos que tengan empresa. La condición rp.is_company = FALSE filtra los registros para que sean personas y no empresas, mientras que rp.city <> 'Tracy' excluye los contactos cuya ciudad sea Tracy. Por último, ORDER BY rc.name ASC ordena los resultados alfabéticamente según el nombre de la empresa.

Comprobación:

![Imagen](images/a9.png)

5. Apartado 5:

````
SELECT
rp.name AS nombre_empresa,
am.name AS numero_factura,
am.invoice_date AS fecha_factura,
am.amount_untaxed AS total_sin_impuestos
FROM account_move am
JOIN res_partner rp ON am.partner_id = rp.id
WHERE am.move_type = 'in_refund'
ORDER BY am.invoice_date DESC;
````

Esta consulta obtiene un listado de empresas proveedoras que han emitido facturas rectificativas o reembolsos en Odoo, mostrando el nombre de la empresa (rp.name), el número de la factura (am.name), la fecha de la factura (am.invoice_date) y el total de la factura sin impuestos (am.amount_untaxed). La información se toma de la tabla account_move con alias am para las facturas y se une (JOIN) con res_partner con alias rp para obtener los datos de la empresa a través de am.partner_id = rp.id. La condición am.move_type = 'in_refund' filtra solo las facturas de proveedor que son reembolsos, y ORDER BY am.invoice_date DESC ordena los resultados de manera que las facturas más recientes aparezcan primero.

Comprobación:

![Imagen](images/a9.png)








