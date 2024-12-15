# Funciones de Cadenas en SQL

## Introducción

Las funciones de cadenas en SQL son herramientas esenciales para la manipulación y análisis de datos textuales. En el contexto de **eseidGambling**, estas funciones permiten realizar operaciones útiles como formatear etiquetas de campañas, extraer información de datos de sesiones y transacciones, y crear reportes personalizados para marketing.

---

## Explicación Conceptual

### Principales Funciones de Cadenas

1. **LENGTH**: Devuelve el número de caracteres en una cadena especificada.
2. **UPPER & LOWER**: Convierten todos los caracteres en una cadena a mayúsculas o minúsculas.
3. **REPLACE**: Reemplaza subcadenas específicas dentro de una cadena.
4. **TRIM, LTRIM & RTRIM**: Elimina caracteres innecesarios desde el inicio, final o ambos lados de una cadena.
5. **CONCAT**: Combina dos o más cadenas en una.
6. **SUBSTRING**: Extrae una parte de una cadena según una posición y longitud especificadas.
7. **STRING_AGG**: Concatena valores de entrada en una única cadena separada por un delimitador.

---

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

---

## Ejemplos Prácticos en eseidGambling

### **1. Analizar Longitud de Etiquetas de Campañas (LENGTH)**

```sql
SELECT campaign_id, LENGTH(campaign_name) AS campaign_length
FROM campaigns;
```

Esto mide la longitud de los nombres de campañas para verificar su consistencia y usabilidad en reportes.

### **2. Normalizar Nombres de Mercados (UPPER & LOWER)**

```sql
SELECT market_id, UPPER(market_name) AS market_uppercase, LOWER(market_name) AS market_lowercase
FROM markets;
```

Convierte los nombres de mercados a mayúsculas y minúsculas para análisis consistente.

### **3. Reemplazar Fuentes de Tráfico (REPLACE)**

```sql
SELECT session_id, REPLACE(utm_source_medium, 'google/organic', 'SEO') AS source_normalized
FROM sessions;
```

Reemplaza etiquetas como 'google/organic' por 'SEO' para mejorar la claridad en los reportes.

### **4. Eliminar Espacios en Etiquetas de Fuentes (TRIM, LTRIM & RTRIM)**

```sql
SELECT session_id, TRIM(BOTH ' ' FROM utm_source_medium) AS cleaned_source
FROM sessions;
```

Elimina espacios no deseados de etiquetas en `utm_source_medium`.

### **5. Crear Direcciones Personalizadas (CONCAT)**

```sql
SELECT user_id, city || ', ' || country AS full_address
FROM users;
```

Combina ciudad y país para crear direcciones personalizadas en los reportes.

### **6. Extraer Categorías de Campañas (SUBSTRING)**

```sql
SELECT campaign_id, SUBSTRING(campaign_name FROM 1 FOR 5) AS campaign_category
FROM campaigns;
```

Extrae las primeras cinco letras de los nombres de las campañas para categorización.

### **7. Consolidar Productos por Pedido (STRING_AGG)**

```sql
SELECT order_id, STRING_AGG(product_id, ', ') AS product_list
FROM orders
GROUP BY order_id;
```

Agrupa productos en una sola columna por cada pedido, separándolos por comas.

---

## Uso de ChatGPT para Funciones de Cadenas

### **1. Generar Consultas para Normalización de Datos**

**Prompt:**  
*"¿Cómo puedo convertir todos los nombres de mercados a mayúsculas en mi tabla de mercados?"*

**Respuesta de ChatGPT:**  
```sql
SELECT market_id, UPPER(market_name) AS market_uppercase
FROM markets;
```

### **2. Explicación de Consultas de Manipulación de Cadenas**

**Prompt:**  
*"¿Qué hace esta consulta?*  
```sql
SELECT campaign_id, SUBSTRING(campaign_name FROM 1 FOR 5) AS campaign_category
FROM campaigns;
```*

**Respuesta de ChatGPT:**  
*"Esta consulta extrae los primeros cinco caracteres de los nombres de las campañas (`campaign_name`) y los presenta como una nueva columna llamada `campaign_category`."*

---

## Resumen

Las funciones de cadenas en SQL son herramientas fundamentales para manipular y analizar datos textuales. En **eseidGambling**, estas funciones son esenciales para normalizar etiquetas, extraer datos relevantes y crear reportes personalizados. Con **ChatGPT**, puedes generar y entender consultas más avanzadas para manipulación de cadenas.
