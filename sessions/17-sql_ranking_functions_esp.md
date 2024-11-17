<!-- # Guía detallada de funciones de ventana de clasificación en SQL -->

<!-- Window Funciones de Clasificación en SQL -->


## Introducción

En SQL, las funciones de ventana de clasificación son esenciales para el análisis y la generación de informes donde hay una necesidad de asignar rangos a las filas basándose en sus valores. Son particularmente poderosas cuando se usan en conjunto con la cláusula `OVER()`, que define la partición y el orden de las filas para la operación de clasificación.

## ROW_NUMBER()

La función `ROW_NUMBER()` asigna un número único a cada fila comenzando desde 1 para la primera fila en cada partición. Este ranking se reinicia para cada partición.

### Ejemplo teórico:

Imagina que tenemos una tabla de ventas y queremos clasificar a los empleados de ventas basándonos en su rendimiento individual de ventas en cada región.

```sql
SELECT 
  EmployeeID,
  Region,
  SalesAmount,
  ROW_NUMBER() OVER (PARTITION BY Region ORDER BY SalesAmount DESC) AS Rank
FROM 
  SalesRecords;
```

Esto asignará un rango único a cada empleado de ventas dentro de cada región basado en el monto total de ventas, siendo el número 1 para las ventas más altas.

## RANK()

La función `RANK()` asigna un rango a cada fila dentro de una partición con el mismo rango para valores empatados. El rango subsiguiente después de un empate se incrementará basado en el número total de rangos empatados.

### Ejemplo teórico:

Usando la misma tabla de ventas, si queremos clasificar a los empleados de ventas pero dar el mismo rango a los empleados con la misma cantidad de ventas, usaríamos `RANK()`.

```sql
SELECT 
  EmployeeID,
  Region,
  SalesAmount,
  RANK() OVER (PARTITION BY Region ORDER BY SalesAmount DESC) AS Rank
FROM 
  SalesRecords;
```

## DENSE_RANK()

La función `DENSE_RANK()` es similar a `RANK()`, pero no omite rangos después de empates. Después de un empate, el siguiente rango será el siguiente entero consecutivo.

### Ejemplo teórico:

En la tabla de ventas, si dos empleados en la misma región tienen la misma cantidad de ventas y queremos asegurar que no se omitan rangos después de un empate:

```sql
SELECT 
  EmployeeID,
  Region,
  SalesAmount,
  DENSE_RANK() OVER (PARTITION BY Region ORDER BY SalesAmount DESC) AS DenseRank
FROM 
  SalesRecords;
```

## PERCENT_RANK()

La función `PERCENT_RANK()` calcula el rango de una fila como un porcentaje del número de filas en la partición.

### Ejemplo teórico:

Para entender la posición relativa de cada empleado dentro de su región:

```sql
SELECT 
  EmployeeID,
  Region,
  SalesAmount,
  PERCENT_RANK() OVER (PARTITION BY Region ORDER BY SalesAmount DESC) AS PercentRank
FROM 
  SalesRecords;
```

## NTILE()

La función `NTILE()` divide el conjunto de resultados ordenado en un número especificado de partes aproximadamente iguales.

### Ejemplo teórico:

Si queremos dividir a los empleados en cuartiles basados en sus ventas dentro de cada región:

```sql
SELECT 
  EmployeeID,
  Region,
  SalesAmount,
  NTILE(4) OVER (PARTITION BY Region ORDER BY SalesAmount DESC) AS Quartile
FROM 
  SalesRecords;
```

## Resumen

Las funciones de clasificación son altamente beneficiosas para identificar y categorizar datos basados en su rango ordinal dentro de una partición. Son indispensables para el análisis comparativo y la generación de informes en SQL. Estas funciones son compatibles con diversas bases de datos SQL, haciéndolas universalmente útiles para analistas de datos y desarrolladores.

Al comprender estas funciones y practicar con datos reales o teóricos, los estudiantes podrán aplicar estas funciones para abordar requisitos complejos de recuperación de datos.
