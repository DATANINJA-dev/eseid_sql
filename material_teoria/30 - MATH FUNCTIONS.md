# Funciones Matemáticas en SQL

## Introducción

Las funciones matemáticas en SQL son cruciales para realizar diversas operaciones matemáticas sobre los datos. En el contexto de **eseidGambling**, estas funciones permiten analizar métricas como ingresos, costos, descuentos, y generar datos aleatorios para simulaciones o pruebas.

---

## Explicación Conceptual

### Principales Funciones Matemáticas

1. **CEIL & FLOOR**:  
   - `CEIL`: Devuelve el menor entero mayor o igual a un número.
   - `FLOOR`: Devuelve el mayor entero menor o igual a un número.

2. **RANDOM**:  
   - Genera un número aleatorio entre 0 y 1.

3. **SETSEED**:  
   - Establece una semilla para generar secuencias repetibles de números aleatorios.

4. **ROUND**:  
   - Redondea un número a un número específico de decimales.

5. **POWER**:  
   - Calcula la potencia de un número elevado a un exponente.

---

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

---

## Ejemplos Prácticos en eseidGambling

### **1. Redondear Ingresos (CEIL & FLOOR)**

```sql
SELECT transaction_id, gross_revenue, CEIL(gross_revenue) AS rounded_up, FLOOR(gross_revenue) AS rounded_down
FROM transactions;
```

Este ejemplo redondea los ingresos brutos (`gross_revenue`) hacia arriba y hacia abajo, proporcionando estimaciones rápidas.

### **2. Generar Números Aleatorios para Pruebas (RANDOM)**

```sql
SELECT RANDOM() AS random_value
FROM generate_series(1, 10);
```

Genera 10 valores aleatorios para simular métricas de prueba.

### **3. Crear Secuencias Repetibles de Datos Aleatorios (SETSEED)**

```sql
SELECT SETSEED(0.5);
SELECT RANDOM() AS random_value_1, RANDOM() AS random_value_2;
```

Esto asegura que los números aleatorios generados sean consistentes en cada ejecución.

### **4. Redondear Descuentos (ROUND)**

```sql
SELECT campaign_id, discount_percentage, ROUND(discount_percentage, 2) AS rounded_discount
FROM campaigns;
```

Redondea los porcentajes de descuento de las campañas a dos decimales.

### **5. Calcular Potencias para Métricas Avanzadas (POWER)**

```sql
SELECT market_id, POWER(average_session_duration, 2) AS squared_duration
FROM markets;
```

Calcula el cuadrado de la duración promedio de sesiones por mercado para análisis avanzados.

---

## Uso de ChatGPT para Funciones Matemáticas

### **1. Generar Consultas Matemáticas**

**Prompt:**  
*"¿Cómo puedo redondear los ingresos brutos hacia arriba y hacia abajo en una tabla de transacciones?"*

**Respuesta de ChatGPT:**  
```sql
SELECT transaction_id, gross_revenue, CEIL(gross_revenue) AS rounded_up, FLOOR(gross_revenue) AS rounded_down
FROM transactions;
```

### **2. Explicación de Consultas Matemáticas**

**Prompt:**  
*"¿Qué hace esta consulta?*  
```sql
SELECT campaign_id, discount_percentage, ROUND(discount_percentage, 2) AS rounded_discount
FROM campaigns;
```*

**Respuesta de ChatGPT:**  
*"Esta consulta redondea los porcentajes de descuento (`discount_percentage`) en la tabla `campaigns` a dos decimales, proporcionando resultados más claros y consistentes."*

---

## Resumen

Las funciones matemáticas en SQL son herramientas poderosas para el análisis numérico y la manipulación de datos. En **eseidGambling**, estas funciones facilitan cálculos precisos y simulaciones relevantes para optimizar campañas, evaluar costos y realizar análisis detallados. Con **ChatGPT**, puedes construir y entender consultas matemáticas de manera más eficiente.
