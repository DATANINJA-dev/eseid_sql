<!-- # OUTER JOIN en SQL -->

## Introducción

OUTER JOIN en SQL es un tipo de unión que se utiliza para recuperar datos de múltiples tablas en una base de datos. Es un aspecto crucial de SQL, ya que permite la combinación de datos de diferentes tablas basadas en una columna relacionada entre ellas. Esta lección se centra en el concepto de OUTER JOIN, específicamente el FULL OUTER JOIN, y su aplicación en consultas SQL.

## Explicación Conceptual

Las uniones son fundamentales en SQL para combinar filas de dos o más tablas. El OUTER JOIN es único porque puede devolver todas las filas de ambas tablas, incluso si la condición de unión no se cumple. Este tipo de unión es particularmente útil en escenarios donde quieres encontrar registros que no tienen coincidencia en otra tabla.

### Tipos de Uniones

- **INNER JOIN**: Devuelve registros que tienen valores coincidentes en ambas tablas.
- **LEFT OUTER JOIN (LEFT JOIN)**: Devuelve todos los registros de la tabla izquierda y los registros coincidentes de la tabla derecha.
- **RIGHT OUTER JOIN (RIGHT JOIN)**: Devuelve todos los registros de la tabla derecha y los registros coincidentes de la tabla izquierda.
- **FULL OUTER JOIN (FULL JOIN)**: Combina los resultados de los outer joins izquierdo y derecho.
- **CROSS JOIN (CARTESIAN JOIN)**: Devuelve el producto cartesiano de ambas tablas.

## Sintaxis y Uso

La sintaxis básica para un FULL OUTER JOIN en SQL es la siguiente:

```sql
SELECT table1.column1, table2.column2...
FROM table1
FULL JOIN table2
ON table1.common_field = table2.common_field;
```

Esta sintaxis combina los datos de dos tablas basadas en un campo común, incluyendo registros que no tienen valores coincidentes en ninguna de las tablas.

## Ejemplos Prácticos

Considera dos tablas: `sales_2015` y `customer_20_60`. La siguiente consulta SQL demuestra cómo usar un FULL OUTER JOIN para combinar datos de estas tablas:


```sql
SELECT 
    a.order_line, 
    a.product_id,
    a.customer_id,
    a.sales,
    b.customer_name,
    b.age,
    b.customer_id
FROM sales_2015 AS a
FULL JOIN customer_20_60 AS b
ON a.customer_id = b.customer_id
ORDER BY a.customer_id, b.customer_id;
```

En este ejemplo, la consulta recupera líneas de pedido, IDs de productos, IDs de clientes, cifras de ventas, nombres de clientes y edades de ambas tablas, ordenándolos por ID de cliente.

## Resumen

El FULL OUTER JOIN en SQL es una herramienta poderosa para combinar datos de dos tablas, especialmente cuando necesitas incluir filas que no tienen coincidencias correspondientes en la otra tabla. Comprender su sintaxis y aplicación es esencial para una gestión efectiva de la base de datos y análisis de datos.

