<!-- # Funciones DATETIME en SQL -->

## Introducción

Las funciones DATETIME en SQL son esenciales para manejar valores de fecha y hora dentro de las bases de datos. Proporcionan la capacidad de manipular, formatear y calcular fechas y horas, lo cual es crucial para muchas tareas de análisis de datos.

## Explicación Conceptual

### 1. CURRENT_DATE, CURRENT_TIME, CURRENT_TIMESTAMP

- `CURRENT_DATE` devuelve la fecha actual.
- `CURRENT_TIME` devuelve la hora actual con la zona horaria.
- `CURRENT_TIMESTAMP` devuelve la fecha y hora actuales con la zona horaria.

### 2. AGE

La función `AGE` calcula la edad (diferencia) entre dos fechas.

### 3. EXTRACT

La función `EXTRACT` recupera partes específicas de un valor de fecha o hora (como día, mes, año, etc.).

## Sintaxis y Uso

### CURRENT_DATE, CURRENT_TIME, CURRENT_TIMESTAMP

```sql
SELECT CURRENT_DATE;
SELECT CURRENT_TIME;
SELECT CURRENT_TIMESTAMP;
```

### AGE

```sql
SELECT AGE(timestamp1, timestamp2);
```

### EXTRACT

```sql
SELECT EXTRACT(unit FROM date);
```

## Practical Examples

### CURRENT_DATE, CURRENT_TIME, CURRENT_TIMESTAMP

```sql
-- Example: Retrieve the current date, time, and timestamp
SELECT CURRENT_DATE;
SELECT CURRENT_TIME;
SELECT CURRENT_TIMESTAMP;
```

### AGE

```sql
-- Example: Calculate the age between two dates
SELECT age('2014-04-25', '2014-01-01');
-- Example: Calculate the time taken for an order to ship
SELECT order_line, order_date, ship_date, 
       AGE(ship_date, order_date) AS time_taken
FROM sales
ORDER BY time_taken DESC;
```

### EXTRACT

```sql
-- Example: Extract day from a date
SELECT EXTRACT(day FROM '2014-04-25');
-- Example: Extract minute from time
SELECT EXTRACT(minute FROM '08:44:21');
-- Example: Calculate the epoch time difference between shipping and order dates
SELECT order_line, EXTRACT(EPOCH FROM (ship_date - order_date))
FROM sales;
```

## Resumen

Comprender las funciones DATETIME en SQL es crucial para la manipulación y análisis efectivos de datos, especialmente cuando se trata de datos sensibles al tiempo. Estas funciones permiten cálculos precisos de fecha y hora, formateo y extracción, mejorando las capacidades de las consultas SQL.

