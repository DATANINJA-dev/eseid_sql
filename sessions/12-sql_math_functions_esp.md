<!-- # SQL Math Functions -->

<!-- # Funciones Matemáticas en SQL -->

## Introducción

Las funciones matemáticas en SQL son cruciales para realizar diversas operaciones matemáticas sobre los datos. Estas funciones permiten a los analistas de datos y administradores de bases de datos ejecutar cálculos complejos directamente dentro de las consultas SQL.

## Explicación Conceptual

### 1. CEIL & FLOOR

- La función `CEIL` devuelve el menor entero mayor o igual a un número.
- La función `FLOOR` devuelve el mayor entero menor o igual a un número.

### 2. RANDOM

La función `RANDOM` devuelve un número aleatorio entre 0 y 1.

### 3. SETSEED

La función `SETSEED` establece la semilla para la función `RANDOM` para generar una secuencia repetible de números.

### 4. ROUND

La función `ROUND` redondea un número a un número especificado de decimales.

### 5. POWER

La función `POWER` devuelve un número elevado a la potencia de otro número.

## Sintaxis y Uso

### CEIL & FLOOR

```sql
SELECT CEIL(number);
SELECT FLOOR(number);
```
### RANDOM

```sql
SELECT RANDOM();
```

### SETSEED

```sql
SELECT SETSEED(seed);
```

### ROUND

```sql
SELECT ROUND(number, decimal_places);
```

### POWER

```sql
SELECT POWER(base, exponent);
```

## Practical Examples

### CEIL & FLOOR

```sql
-- Example: Round sales figures to the nearest integer
SELECT order_line, sales, CEIL(sales), FLOOR(sales)
FROM sales
WHERE discount > 0;
```

### RANDOM

```sql
-- Example: Generate a random number between 0 and 1
SELECT RANDOM();
```

### SETSEED

```sql
-- Example: Generate a repeatable sequence of random numbers
SELECT SETSEED(0.5);
SELECT RANDOM();
SELECT RANDOM();
```

### ROUND

```sql
-- Example: Round sales figures to 2 decimal places
SELECT order_line, sales, ROUND(sales, 2)
FROM sales;
```

### POWER

```sql
-- Example: Calculate the square of each customer's age
SELECT age, POWER(age, 2)
FROM customer
ORDER BY age;
```

## Resumen

Las funciones matemáticas de SQL desempeñan un papel significativo en el análisis y manipulación de datos. Comprender y utilizar eficazmente estas funciones puede mejorar enormemente la capacidad de realizar cálculos complejos dentro de las consultas SQL.
