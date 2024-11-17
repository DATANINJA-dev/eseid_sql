<!-- # Guía detallada de funciones de ventana de valor en SQL -->

<!-- Window Funciones de Value en SQL -->

## Introducción

Las funciones de ventana de valor son un subconjunto de funciones de ventana en SQL que operan sobre los valores de las filas en una ventana. Estas funciones son particularmente útiles para comparar valores entre diferentes filas sin cambiar el orden o el número de las filas.

## LAG()

La función `LAG()` se utiliza para acceder a datos de una fila anterior en el conjunto de resultados sin utilizar una autoconexión. Es útil para comparar la fila actual con una fila que viene antes.

### Ejemplo teórico:

Para comparar el monto de ventas del mes actual con el del mes anterior para cada empleado:

```sql
SELECT 
  EmployeeID,
  SaleMonth,
  SalesAmount,
  LAG(SalesAmount, 1) OVER (PARTITION BY EmployeeID ORDER BY SaleMonth) AS PreviousMonthSales
FROM 
  MonthlySales;
```

## LEAD()

La función `LEAD()` se utiliza para acceder a datos de una fila posterior en el conjunto de resultados sin utilizar una autoconexión. Es útil para comparar la fila actual con una fila que la sigue.

### Ejemplo teórico:

Para comparar el monto de ventas del mes actual con el del próximo mes para cada empleado:

```sql
SELECT 
  EmployeeID,
  SaleMonth,
  SalesAmount,
  LEAD(SalesAmount, 1) OVER (PARTITION BY EmployeeID ORDER BY SaleMonth) AS NextMonthSales
FROM 
  MonthlySales;
```

## FIRST_VALUE()

La función `FIRST_VALUE()` se utiliza para acceder al primer valor en un conjunto ordenado de valores en cada partición.

### Ejemplo teórico:

Para identificar el primer monto de venta logrado por un empleado en un año fiscal:


```sql
SELECT 
  EmployeeID,
  SaleMonth,
  SalesAmount,
  FIRST_VALUE(SalesAmount) OVER (PARTITION BY EmployeeID ORDER BY SaleMonth) AS FirstSaleAmount
FROM 
  MonthlySales;
```

## LAST_VALUE()

La función `LAST_VALUE()` se utiliza para acceder al último valor en un conjunto ordenado de valores en cada partición. Para obtener el verdadero último valor, se debe usar la cláusula `ROWS BETWEEN` para observar todas las filas en la partición.

### Ejemplo teórico:

Para identificar el último monto de venta logrado por un empleado en un año fiscal:


```sql
SELECT 
  EmployeeID,
  SaleMonth,
  SalesAmount,
  LAST_VALUE(SalesAmount) OVER (PARTITION BY EmployeeID ORDER BY SaleMonth 
                                RANGE BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING) AS LastSaleAmount
FROM 
  MonthlySales;
```

## NTH_VALUE()

La función `NTH_VALUE()` se utiliza para acceder al enésimo valor en un conjunto ordenado de valores en cada partición.

### Ejemplo teórico:

Para encontrar el tercer monto de venta más alto de un empleado en un año fiscal:


```sql
SELECT 
  EmployeeID,
  SaleMonth,
  SalesAmount,
  NTH_VALUE(SalesAmount, 3) OVER (PARTITION BY EmployeeID ORDER BY SalesAmount DESC) AS ThirdHighestSale
FROM 
  MonthlySales;
```

## Resumen

Las funciones de ventana de valor proporcionan un medio para realizar cálculos a través de filas relacionadas en una tabla. Son esenciales para analizar secuencias, tendencias y realizar comparaciones de fila a fila en conjuntos de datos. Con el uso de estas funciones, tareas complejas como calcular diferencias entre filas consecutivas o acceder a datos más allá de la fila actual se vuelven sencillas.
