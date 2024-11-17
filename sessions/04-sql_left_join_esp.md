<!-- # LEFT JOIN en SQL -->

## Introducción

LEFT JOIN, también conocido como LEFT OUTER JOIN, es una operación esencial en SQL utilizada para combinar filas de dos tablas. A diferencia del INNER JOIN, devuelve todas las filas de la tabla izquierda, incluso si no hay coincidencias en la tabla derecha, lo que lo hace crucial para ciertos tipos de consultas de bases de datos.

## Explicación Conceptual

LEFT JOIN incluye todos los registros de la tabla izquierda y los registros coincidentes de la tabla derecha. Si no hay coincidencia, el resultado es NULL en el lado de la tabla derecha. Este tipo de unión es particularmente útil cuando necesitas mantener todos los registros en una tabla independientemente de si tienen entradas correspondientes en otra tabla.

## Sintaxis y Uso

La sintaxis para un LEFT JOIN es:

```sql
SELECT table1.column1, table2.column2...
FROM table1
LEFT JOIN table2
ON table1.common_field = table2.common_field;
```

Aquí, `table1` es la tabla izquierda, y `table2` es la tabla derecha. La cláusula `ON` especifica la condición para la unión.

## Ejemplos Prácticos

Supongamos que tenemos dos tablas: `sales_2015` y `customer_20_60`. Para recuperar todos los registros de `sales_2015` junto con cualquier registro coincidente en `customer_20_60` basado en `customer_id`, utilizamos:

```sql
SELECT 
  a.order_line, 
  a.product_id, 
  a.customer_id, 
  a.sales, 
  b.customer_name, 
  b.age
FROM sales_2015 AS a
LEFT JOIN customer_20_60 AS b
ON a.customer_id = b.customer_id
ORDER BY a.customer_id;
```

Esta consulta asegura que todas las entradas en `sales_2015` se incluyan, incluso si no hay un cliente coincidente en `customer_20_60`.

## Resumen

LEFT JOIN es vital para las consultas SQL donde es esencial incluir todas las filas de una tabla independientemente de si coinciden con filas en otra tabla. Ofrece flexibilidad en el manejo de varios escenarios de recuperación de datos en la gestión de bases de datos.