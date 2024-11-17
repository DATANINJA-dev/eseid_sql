<!-- # SQL Window Functions -->

<!-- Window Funciones en SQL -->

## Introducción

![Funciones de ventana](https://cdn.sanity.io/images/oaglaatp/production/e0d2b575fa404eec7c9bedcae9c3818261ffe1ab-1200x800.png?w=1200&h=800&auto=format)

Las funciones de ventana en SQL se utilizan para realizar cálculos en un conjunto de filas que están relacionadas con la fila actual. A diferencia de las funciones agregadas regulares, las funciones de ventana no colapsan las filas en una sola fila de salida; preservan las filas individuales. Esto nos permite agregar datos agregados a las consultas sin usar `GROUP BY`. Las funciones de ventana son ideales para tareas como totales acumulados, medias móviles y estadísticas acumulativas.

## Tipos de funciones de ventana

Hay tres tipos principales de funciones de ventana:

### 1. Funciones de ventana agregadas

Estas son funciones agregadas regulares, pero cuando se usan con la cláusula over, actúan sobre un conjunto de filas relacionadas con la fila actual mientras mantienen filas separadas. Las funciones de ventana agregadas comunes incluyen:
- `AVG()`: Calcula el promedio de un conjunto de valores.
- `MAX()`: Obtiene el valor máximo de un conjunto de valores.
- `MIN()`: Obtiene el valor mínimo de un conjunto de valores.
- `SUM()`: Calcula la suma de un conjunto de valores.
- `COUNT()`: Cuenta el número de valores en un conjunto.

### 2. Funciones de ventana de clasificación

Las funciones de clasificación asignan un rango a cada fila dentro de una partición de un conjunto de resultados. Las funciones de clasificación más comunes son:
- `ROW_NUMBER()`: Asigna un entero secuencial único a las filas dentro de una partición de un conjunto de resultados, comenzando en 1 para la primera fila en cada partición.
- `RANK()`: Asigna un rango a cada fila dentro de una partición de un conjunto de resultados, con huecos en el ranking para valores empatados.
- `DENSE_RANK()`: Similar a `RANK()`, pero sin huecos en el ranking para valores empatados.
- `PERCENT_RANK()`: Calcula el rango relativo de una fila dentro de una partición de un conjunto de resultados.
- `NTILE()`: Distribuye las filas en una partición ordenada en un número especificado de grupos y asigna un número de grupo a cada fila.

### 3. Funciones de ventana de valor

Las funciones de valor realizan cálculos relacionados con los valores en un conjunto de datos, a menudo comparando filas con filas precedentes o siguientes. Estas incluyen:
- `LAG()`: Accede a datos de una fila anterior en el mismo conjunto de resultados sin el uso de una autoconexión.
- `LEAD()`: Accede a datos de una fila posterior en el mismo conjunto de resultados sin el uso de una autoconexión.
- `FIRST_VALUE()`: Obtiene el primer valor en un conjunto ordenado de valores.
- `LAST_VALUE()`: Obtiene el último valor en un conjunto ordenado de valores.
- `NTH_VALUE()`: Obtiene el enésimo valor en un conjunto ordenado de valores.

## Uso de funciones de ventana

Para usar funciones de ventana, generalmente se define la ventana usando la cláusula `OVER()` para especificar cómo se dividen las filas en particiones o ventanas y cómo se ordenan. Aquí está la sintaxis general:

```sql
WINDOW_FUNCTION_NAME() OVER ( [PARTITION BY partition_expression] [ORDER BY sort_expression [ASC|DESC]] )
```

Donde:
- `NOMBRE_FUNCION_VENTANA` es el nombre de la función de ventana.
- `PARTITION BY expresión_partición` divide el conjunto de resultados en particiones donde se aplica la función de ventana. Si no se especifica, todo el conjunto de resultados se trata como una sola partición.
- `ORDER BY expresión_ordenación` especifica el orden lógico dentro de cada partición.

## Ejemplo de Uso

```sql
-- Calculate running total sales for each product
SELECT 
  ProductID,
  OrderDate,
  SalesAmount,
  SUM(SalesAmount) OVER (PARTITION BY ProductID ORDER BY OrderDate) AS RunningTotal
FROM Sales;
```

En el ejemplo anterior, estamos usando `SUM()` como una función de ventana para calcular un total acumulado de `SalesAmount` para cada `ProductID` según el orden de `OrderDate`.

## Resumen

Las funciones de ventana son una característica potente en SQL que permite realizar cálculos y análisis sofisticados. Pueden simplificar consultas que de otro modo serían complejas y aumentar el rendimiento al reducir la necesidad de múltiples consultas o uniones complejas.
