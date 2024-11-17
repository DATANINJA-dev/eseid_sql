<!-- # SQL Conversion Functions -->

<!-- Funciones de Conversión en SQL -->

## Introducción

Las funciones de conversión en SQL son cruciales para la manipulación de tipos de datos, permitiendo la conversión de datos de un tipo a otro. Esta capacidad es esencial para un procesamiento y análisis de datos efectivos.

## Explicación Conceptual

### 1. TO_CHAR

La función `TO_CHAR` convierte un número o fecha en una cadena. A menudo se utiliza para formatear la salida.

### 2. TO_DATE

La función `TO_DATE` convierte una cadena en un formato de fecha, lo que permite cálculos y formateos de fecha.

### 3. TO_NUMBER

La función `TO_NUMBER` convierte una cadena en un número, permitiendo operaciones numéricas en datos inicialmente almacenados como texto.

## Sintaxis y Uso

### TO_CHAR

```sql
SELECT TO_CHAR(value, format_mask);
```

### TO_DATE

```sql
SELECT TO_DATE(string, format_mask);
```

### TO_NUMBER

```sql
SELECT TO_NUMBER(string, format_mask);
```

## Practical Examples

### TO_CHAR

```sql
-- Example: Convert sales figures to string with two decimal places
SELECT TO_CHAR(sales, '9999.99') FROM sales;
-- Example: Convert order date to a formatted string
SELECT TO_CHAR(order_date, 'Month DD YYYY') FROM sales;
```

### TO_DATE

```sql
-- Example: Convert a string to date format
SELECT TO_DATE('2014/04/25', 'YYYY/MM/DD');
-- Example: Convert a string with day and month to date
SELECT TO_DATE('033114', 'MMDDYY');
```

### TO_NUMBER

```sql
-- Example: Convert a formatted string to a number
SELECT TO_NUMBER('1210.73', '9999.99');
-- Example: Convert a currency string to a number
SELECT TO_NUMBER('$1210.73', 'L9999.99');
```

## Resumen

Las funciones de conversión de SQL son fundamentales para manipular y convertir tipos de datos, lo cual es un requisito común en el análisis y procesamiento de datos. El dominio de estas funciones permite capacidades de manipulación de datos más flexibles y potentes.

