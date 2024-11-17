<!-- # Operador UNION en SQL -->

## Introducción

El operador UNION en SQL se utiliza para combinar los conjuntos de resultados de dos o más declaraciones SELECT. Es particularmente útil para consolidar resultados de múltiples consultas en un solo conjunto de resultados. Una característica clave de UNION es que automáticamente elimina filas duplicadas entre los conjuntos de resultados.

## Explicación Conceptual

UNION se utiliza para ejecutar dos o más declaraciones SELECT y combinar sus resultados en un solo conjunto de resultados. Solo incluye valores distintos, eliminando efectivamente los duplicados. Esta operación es útil cuando necesitas agregar datos de diferentes fuentes o tablas pero solo quieres incluir registros únicos.

## Sintaxis y Uso

La sintaxis básica para usar el operador UNION en SQL es:

```sql
SELECT expression1, expression2, ... expression_n
FROM tables
[WHERE conditions]
UNION
SELECT expression1, expression2, ... expression_n
FROM tables
[WHERE conditions];
```
Cada declaración SELECT dentro del UNION debe tener el mismo número de campos con tipos de datos similares.

## Ejemplos Prácticos

Considera dos tablas: `sales_2015` y `customer_20_60`. La siguiente consulta SQL demuestra el uso del operador UNION:


```sql
SELECT customer_id
FROM sales_2015
UNION
SELECT customer_id
FROM customer_20_60
ORDER BY customer_id;
```

En este ejemplo, la consulta recupera ID de clientes únicos de ambas tablas `sales_2015` y `customer_20_60`, ordenándolos por ID de cliente.

## Resumen

El operador UNION en SQL es una herramienta poderosa para combinar datos de múltiples declaraciones SELECT asegurando que solo se incluyan registros únicos en el resultado final. Comprender su sintaxis y aplicación es esencial para una consolidación y análisis de datos efectivos.
