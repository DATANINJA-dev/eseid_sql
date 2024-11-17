<!-- # Subconsultas en SQL -->

## Introducción

Una subconsulta en SQL es una consulta anidada dentro de otra consulta. Las subconsultas pueden usarse en varias partes de una consulta, incluidas las cláusulas WHERE, FROM y SELECT. Son herramientas poderosas para realizar tareas complejas de recuperación de datos.

## Explicación Conceptual

Las subconsultas permiten consultas SQL más dinámicas y flexibles. Permiten que una consulta se construya basada en los resultados de otra consulta, lo que a menudo permite un análisis y recuperación de datos más sofisticados.

### Subconsulta en WHERE

Una subconsulta dentro de la cláusula WHERE puede filtrar datos basados en el resultado de otra consulta.

### Subconsulta en FROM

Una subconsulta dentro de la cláusula FROM puede usarse para crear una tabla temporal de la cual la consulta principal puede recuperar datos.

### Subconsulta en SELECT

Una subconsulta dentro de la cláusula SELECT puede devolver un valor único utilizado en una columna de la consulta principal.

## Sintaxis y Uso

La sintaxis general para una subconsulta es:

```sql
SELECT column_name1
FROM table_name1
WHERE column_name2 [Comparison Operator]
(SELECT column_name3
 FROM table_name2
 WHERE condition);
```

## Ejemplos Prácticos

1. **Subconsulta en WHERE**:

   ```sql
   SELECT * FROM sales
   WHERE customer_ID IN
   (SELECT DISTINCT customer_id
    FROM customer WHERE age > 60);
   ```

2. **Subconsulta con FROM**:
   ```sql
   SELECT a.product_id, a.product_name, a.category, b.quantity
   FROM product AS a
   LEFT JOIN (SELECT product_id, SUM(quantity) AS quantity
              FROM sales GROUP BY product_id) AS b
   ON a.product_id = b.product_id
   ORDER BY b.quantity DESC;
   ```

3. **Subconsulta con SELECT**:
   ```sql
   SELECT customer_id, order_line,
          (SELECT customer_name
           FROM customer
           WHERE sales.customer_id = customer.customer_id)
   FROM sales
   ORDER BY customer_id;
   ```

## Reglas para Subconsultas

- Las subconsultas deben estar encerradas entre paréntesis.
- Una subconsulta solo puede tener una columna en la cláusula SELECT, a menos que en la consulta principal se utilicen múltiples columnas.
- No se puede usar el comando ORDER BY en una subconsulta.
- Las subconsultas que devuelven más de una fila solo pueden usarse con operadores de valores múltiples como IN.
- La lista SELECT no puede incluir referencias a BLOB, ARRAY, CLOB o NCLOB.
- Una subconsulta no puede estar inmediatamente encerrada en una función de conjunto.
- El operador BETWEEN no puede usarse con una subconsulta, pero puede usarse dentro de la subconsulta.

## Resumen

Las subconsultas en SQL proporcionan una forma flexible y poderosa de realizar consultas anidadas, lo que permite una recuperación de datos compleja. Comprender su sintaxis y aplicaciones es crucial para consultas y análisis de bases de datos avanzados.
