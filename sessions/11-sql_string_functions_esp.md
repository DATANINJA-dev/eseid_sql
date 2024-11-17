<!-- # SQL String Functions -->

<!-- Funciones de Cadenas en SQL -->

## Introducción

Las funciones de cadena en SQL son herramientas esenciales para la manipulación y análisis de datos. Permiten realizar operaciones sobre datos de tipo cadena, como formatear, extraer y concatenar, haciendo que los datos sean más significativos y fáciles de entender.

## Explicación Conceptual

### 1. LENGTH

La función `LENGTH` devuelve el número de caracteres en una cadena especificada.

### 2. UPPER & LOWER

Las funciones `UPPER` y `LOWER` convierten todos los caracteres en una cadena a mayúsculas o minúsculas, respectivamente.

### 3. REPLACE

La función `REPLACE` reemplaza ocurrencias de una subcadena especificada dentro de una cadena por otra subcadena.

### 4. TRIM, LTRIM & RTRIM

- `TRIM` elimina caracteres especificados del principio o final de una cadena.
- `LTRIM` elimina caracteres especificados del lado izquierdo de una cadena.
- `RTRIM` elimina caracteres especificados del lado derecho de una cadena.

### 5. CONCAT

La función `CONCAT` (o el operador `||`) permite la concatenación de dos o más cadenas.

### 6. SUBSTRING

La función `SUBSTRING` extrae una subcadena de una cadena, comenzando en una posición especificada y por una longitud especificada.

### 7. STRING_AGG

La función `STRING_AGG` concatena valores de entrada en una única cadena separada por un delimitador especificado.

## Sintaxis y Uso

### LENGTH


```sql
SELECT LENGTH(string);
```

### UPPER & LOWER

```sql
SELECT UPPER(string);
SELECT LOWER(string);
```

### REPLACE

```sql
SELECT REPLACE(string, from_substring, to_substring);
```

### TRIM, LTRIM & RTRIM

```sql
SELECT TRIM([LEADING | TRAILING | BOTH] [trim_character] FROM string);
SELECT RTRIM(string, trim_character);
SELECT LTRIM(string, trim_character);
```

### CONCAT

```sql
SELECT string1 || string2 || ... || stringN;
```

### SUBSTRING

```sql
SELECT SUBSTRING(string FROM start_position [FOR length]);
```

### STRING_AGG

```sql
SELECT STRING_AGG(expression, delimiter);
```

## Practical Examples

### LENGTH

```sql
-- Example: Find the length of customer names
SELECT Customer_name, LENGTH(Customer_name) AS characters
FROM customer
WHERE age > 30;
```

### UPPER & LOWER

```sql
-- Example: Convert the name 'Start-Tech Academy' to uppercase and lowercase
SELECT UPPER('Start-Tech Academy');
SELECT LOWER('Start-Tech Academy');
```

### REPLACE

```sql
-- Example: Replace 'United States' with 'US' in country names
SELECT Customer_name, REPLACE(country, 'United States', 'US') AS country_new
FROM customer;
```

### TRIM, LTRIM & RTRIM

```sql
-- Example: Trim spaces from different parts of the string '  Start-Tech Academy  '
SELECT TRIM(LEADING ' ' FROM '  Start-Tech Academy ');
SELECT TRIM(TRAILING ' ' FROM '  Start-Tech Academy ');
SELECT TRIM(BOTH ' ' FROM '  Start-Tech Academy ');
SELECT RTRIM('  Start-Tech Academy ', ' ');
SELECT LTRIM('  Start-Tech Academy ', ' ');
```

### CONCAT

```sql
-- Example: Concatenate customer's city, state, and country as address
SELECT Customer_name, city || ' ' || state || ' ' || country AS address
FROM customer;
```

### SUBSTRING

```sql
-- Example: Extract parts of the customer ID
SELECT Customer_id, Customer_name, SUBSTRING(Customer_id FOR 2) AS cust_group
FROM customer
WHERE SUBSTRING(Customer_id FOR 2) = 'AB';
```

### STRING_AGG

```sql
-- Example: Concatenate product IDs for each order
SELECT order_id, STRING_AGG(product_id, ' ')
FROM sales
GROUP BY order_id;
```

## Resumen

Las funciones de cadena de SQL son vitales para manipular y analizar datos textuales en bases de datos. Comprender estas funciones mejora la capacidad de manejar diversas tareas de manipulación de datos de manera eficiente y efectiva.

