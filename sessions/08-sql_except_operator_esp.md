<!-- # Operador EXCEPT en SQL -->

## Introducción

El operador EXCEPT en SQL se utiliza para operaciones de conjuntos. Permite devolver todas las filas del primer comando SELECT que no están presentes en el conjunto de resultados del segundo comando SELECT. Este operador es particularmente útil para encontrar diferencias entre dos conjuntos de datos.

## Explicación Conceptual

EXCEPT realiza una operación de diferencia de conjuntos. Compara los conjuntos de resultados de dos declaraciones SELECT y devuelve las filas del primer conjunto que no aparecen en el segundo conjunto. Esta operación es útil en escenarios donde necesitas identificar registros únicos en un conjunto de datos que no se encuentran en otro.

## Sintaxis y Uso

La sintaxis básica para usar el operador EXCEPT en SQL es la siguiente:

```sql
SELECT expression1, expression2, ...
FROM tables
[WHERE conditions]
EXCEPT
SELECT expression1, expression2, ...
FROM tables
[WHERE conditions];
```

Esta sintaxis recupera datos basados en los criterios especificados en las declaraciones SELECT y luego excluye las filas de la segunda consulta del conjunto de resultados de la primera consulta.

## Ejemplos Prácticos

Considera dos tablas: `sales_2015` y `customer_20_60`. La siguiente consulta SQL demuestra el uso del operador EXCEPT:


```sql
SELECT customer_id
FROM sales_2015
EXCEPT
SELECT customer_id
FROM customer_20_60
ORDER BY customer_id;
```

En este ejemplo, la consulta recupera los ID de clientes de la tabla `sales_2015` que no se encuentran en la tabla `customer_20_60`, ordenando el resultado por ID de cliente.

## Resumen

El operador EXCEPT en SQL es una herramienta valiosa para comparar y contrastar conjuntos de datos. Ayuda a identificar registros únicos en un conjunto de datos que no existen en otro, facilitando el análisis de datos y la gestión de bases de datos.

