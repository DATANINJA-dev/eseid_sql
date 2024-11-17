<!-- # RIGHT JOIN en SQL -->

## Introducción

RIGHT JOIN, también conocido como RIGHT OUTER JOIN, es una operación de SQL que combina filas de dos tablas. Se utiliza particularmente para devolver todas las filas de la tabla derecha, incluso si no hay entradas coincidentes en la tabla izquierda, lo cual es crucial en ciertos escenarios de consulta de bases de datos.

## Explicación Conceptual

RIGHT JOIN es similar a LEFT JOIN, pero se centra en la tabla derecha. Recupera todos los registros de la tabla derecha, emparejados con los registros coincidentes de la tabla izquierda. Si no hay coincidencia, la tabla izquierda tendrá valores NULL. Este tipo de unión es beneficioso cuando necesitas preservar todos los registros de la tabla derecha en tu conjunto de resultados.

## Sintaxis y Uso

La sintaxis para RIGHT JOIN es:
```sql
SELECT table1.column1, table2.column2...
FROM table1
RIGHT JOIN table2
ON table1.common_field = table2.common_field;
```

En esta estructura, `table1` es la tabla izquierda y `table2` es la tabla derecha. La cláusula `ON` define la condición para la unión.

## Ejemplos Prácticos

Por ejemplo, si tenemos dos tablas: `sales_2015` y `customer_20_60`, y queremos incluir todos los clientes junto con cualquier registro de ventas, la consulta sería:

```sql
SELECT 
  a.order_line, 
  a.product_id, 
  a.customer_id, 
  a.sales, 
  b.customer_name, 
  b.age
FROM sales_2015 AS a
RIGHT JOIN customer_20_60 AS b
ON a.customer_id = b.customer_id
ORDER BY customer_id;
```

Esto asegura que cada cliente esté incluido en el resultado, incluso si no tienen registros de ventas correspondientes.

## Resumen

RIGHT JOIN en SQL es esencial cuando el objetivo es incluir cada fila de la tabla derecha en una consulta, independientemente de las filas coincidentes en la tabla izquierda. Es una herramienta poderosa para necesidades específicas de recuperación de datos en la gestión de bases de datos.

