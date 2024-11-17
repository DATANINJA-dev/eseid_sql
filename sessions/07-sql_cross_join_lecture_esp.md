<!-- # CROSS JOIN en SQL -->

## Introducción

CROSS JOIN en SQL, también conocido como CARTESIAN JOIN, se utiliza para combinar cada fila de una tabla con cada fila de otra tabla. Este tipo de unión es esencial en escenarios donde necesitas crear un producto cartesiano de dos conjuntos de datos.

## Explicación Conceptual

En SQL, un CROSS JOIN es único ya que no requiere una condición para unir dos tablas. En su lugar, combina cada fila de una tabla con cada fila de otra, resultando en un producto cartesiano. Esto es particularmente útil para escenarios donde necesitas emparejar cada elemento de un conjunto de datos con cada elemento de otro conjunto de datos.

### Tipos de Uniones

- **INNER JOIN**: Devuelve registros con valores coincidentes en ambas tablas.
- **LEFT OUTER JOIN (LEFT JOIN)**: Devuelve todos los registros de la tabla izquierda y los registros coincidentes de la tabla derecha.
- **RIGHT OUTER JOIN (RIGHT JOIN)**: Devuelve todos los registros de la tabla derecha y los registros coincidentes de la tabla izquierda.
- **FULL OUTER JOIN (FULL JOIN)**: Combina los resultados de los outer joins izquierdo y derecho.
- **CROSS JOIN (CARTESIAN JOIN)**: Crea un producto cartesiano de filas de dos tablas.

## Sintaxis y Uso

La sintaxis básica para un CROSS JOIN en SQL es:

```sql
SELECT table1.column1, table2.column2...
FROM table1, table2;
```

Esta sintaxis combinará cada fila de `table1` con cada fila de `table2`.

## Ejemplos Prácticos

Considera dos tablas: `year_values` y `month_values`. La siguiente consulta SQL demuestra cómo usar un CROSS JOIN:

```sql
SELECT a.YYYY, b.MM
FROM year_values AS a, month_values AS b
ORDER BY a.YYYY, b.MM;
```

En este ejemplo, el CROSS JOIN combinará cada valor de año de `year_values` con cada valor de mes de `month_values`, ordenados por año y mes.

## Resumen

El CROSS JOIN en SQL es una herramienta poderosa para generar combinaciones de datos de dos tablas diferentes. Es particularmente útil para escenarios que requieren el emparejamiento de cada elemento de un conjunto de datos con cada elemento de otro, como en ciertos tipos de análisis de datos o informes.

