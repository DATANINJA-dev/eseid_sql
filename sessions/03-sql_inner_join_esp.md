<!-- # INNER JOIN en SQL -->

## Introducción

INNER JOIN es un concepto fundamental en SQL utilizado para combinar filas de dos o más tablas basado en una columna relacionada entre ellas. Esta operación es crítica en la gestión de bases de datos para consultar conjuntos de datos complejos de manera eficiente.

## Explicación Conceptual

INNER JOIN funciona comparando cada fila en una tabla con cada fila en otra tabla para encontrar pares de filas que satisfacen una condición especificada. Cuando se encuentra una coincidencia basada en el predicado de unión, los valores de las columnas de cada par de filas coincidentes se combinan en una fila de resultado. Este proceso permite una recuperación de datos efectiva de múltiples tablas en una base de datos relacional.

## Sintaxis y Uso

La sintaxis básica para un INNER JOIN es la siguiente:

```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

Aquí, `table1` y `table2` son las tablas que se unirán. La cláusula `ON` especifica la columna en base a la cual se realiza la unión.

## Ejemplos Prácticos

Considera dos tablas: `sales_2015` y `customer_20_60`. Para unir estas tablas basado en un `customer_id` común y recuperar datos relevantes, la consulta sería:


```sql
SELECT 
  a.order_line, 
  a.product_id, 
  a.customer_id, 
  a.sales, 
  b.customer_name, 
  b.age
FROM sales_2015 AS a
INNER JOIN customer_20_60 AS b
ON a.customer_id = b.customer_id
ORDER BY a.customer_id;
```

Esta consulta recupera detalles de pedidos junto con información del cliente donde los ID de cliente en ambas tablas coinciden.

## Resumen

INNER JOIN en SQL es esencial para combinar datos de múltiples tablas basado en una columna relacionada. Comprender y utilizar eficazmente INNER JOIN es crucial para la consulta y gestión de bases de datos, particularmente en entornos de datos complejos.

