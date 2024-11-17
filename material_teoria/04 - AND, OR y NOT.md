
# Operadores AND, OR y NOT en SQL

En esta sección, exploramos el uso de los operadores lógicos `AND`, `OR` y `NOT` en el contexto de **eseidGambling**. Estos operadores permiten crear condiciones más complejas en las consultas SQL, filtrando los datos de las tablas `sessions`, `cost` y `purchase` de manera más precisa.

---

## **¿Qué Son AND, OR y NOT?**

### **AND**
Se utiliza para combinar múltiples condiciones. Todas las condiciones deben ser verdaderas para que una fila sea incluida en el conjunto de resultados.

### **OR**
Se utiliza para combinar múltiples condiciones. Solo se requiere que una de las condiciones sea verdadera para incluir una fila en los resultados.

### **NOT**
Se utiliza para negar una condición, seleccionando los datos que no cumplen con la condición especificada.

---

## **Sintaxis Básica**

### Uso de AND:
```sql
SELECT column_name 
FROM table_name 
WHERE condition1 AND condition2;
```

### Uso de OR:
```sql
SELECT column_name 
FROM table_name 
WHERE condition1 OR condition2;
```

### Uso de NOT:
```sql
SELECT column_name 
FROM table_name 
WHERE NOT condition;
```

---

## **Ejemplos en eseidGambling**

### **1. AND: Filtrar Sesiones por Mercado y Fuente**
Queremos obtener sesiones del mercado "ES" que provienen de "google/organic":

```sql
SELECT * 
FROM sessions 
WHERE market_id = 'ES' AND utm_source_medium = 'google/organic';
```

### **2. OR: Expandir Condiciones de Filtrado**
Para ver sesiones del mercado "ES" o "IT":

```sql
SELECT * 
FROM sessions 
WHERE market_id = 'ES' OR market_id = 'IT';
```

### **3. NOT: Excluir Condiciones Específicas**
Si queremos excluir sesiones de "bing/organic":

```sql
SELECT * 
FROM sessions 
WHERE NOT utm_source_medium = 'bing/organic';
```

---

## **Uso en Databricks**

En **Databricks**, estas consultas pueden ejecutarse directamente una vez cargadas las tablas. Por ejemplo:

```sql
SELECT * 
FROM sessions 
WHERE market_id = 'ES' AND utm_source_medium = 'google/organic';
```

Este ejemplo filtra únicamente las sesiones del mercado "ES" que provienen de "google/organic".

---

## **Cómo Usar ChatGPT para Ayuda con AND, OR y NOT**

### **1. Crear Consultas**
**Prompt:**  
*"¿Cómo puedo usar AND para filtrar sesiones del mercado 'ES' que provienen de 'google/organic'?"*

**Respuesta de ChatGPT:**  
```sql
SELECT * 
FROM sessions 
WHERE market_id = 'ES' AND utm_source_medium = 'google/organic';
```

### **2. Explicación de Consultas**
**Prompt:**  
*"¿Qué hace esta consulta?*  
```sql
SELECT * 
FROM sessions 
WHERE market_id = 'ES' OR market_id = 'IT';
```*

**Respuesta de ChatGPT:**  
*"Esta consulta selecciona todas las filas de la tabla `sessions` donde el `market_id` es 'ES' o 'IT'."*

---

## **Conclusión**

Los operadores `AND`, `OR` y `NOT` son esenciales para realizar filtrados avanzados en SQL. En el caso de **eseidGambling**, permiten analizar datos más específicos, como sesiones por mercados o fuentes. Herramientas como **Databricks** y **ChatGPT** son útiles para aplicar y comprender estas consultas.
