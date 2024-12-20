# Operador UNION en SQL

## Introducción

El operador UNION en SQL se utiliza para combinar los conjuntos de resultados de dos o más declaraciones SELECT. En el contexto de **eseidGambling**, UNION es útil para consolidar datos de sesiones, transacciones o campañas provenientes de diferentes tablas o periodos, asegurando que solo se incluyan valores únicos.

---

## Explicación Conceptual

UNION ejecuta dos o más declaraciones SELECT y combina sus resultados en un solo conjunto de resultados, eliminando automáticamente los duplicados. Es una herramienta ideal para consolidar datos dispersos en diferentes tablas o fuentes.

### Características clave:
- Combina resultados de múltiples consultas en un solo conjunto.
- Elimina duplicados por defecto.
- Cada consulta debe tener el mismo número de columnas y tipos de datos similares.

---

## Sintaxis y Uso

La sintaxis básica para usar el operador UNION en SQL es:

```sql
SELECT expression1, expression2, ... expression_n
FROM tables
[WHERE conditions]
UNION
SELECT expression1, expression2, ... expression_n
FROM tables
[WHERE conditions];
```

Para incluir valores duplicados en el resultado final, puedes usar el operador `UNION ALL` en lugar de `UNION`.

---

## Ejemplos Prácticos en eseidGambling

### **1. Consolidar Datos de Sesiones de Dos Fuentes**

```sql
SELECT session_id, utm_source_medium
FROM sessions_2023
UNION
SELECT session_id, utm_source_medium
FROM sessions_2024;
```

Este ejemplo combina sesiones de los años 2023 y 2024, asegurando que cada sesión única se incluya una sola vez.

### **2. Unificar Datos de Transacciones y Registros de Ventas**

```sql
SELECT transaction_id, gross_revenue
FROM transactions
UNION
SELECT sales_id, total_revenue
FROM sales;
```

Aquí se unifican transacciones y ventas, consolidando registros únicos de ambas tablas.

### **3. Agregar Campañas Activas y Completadas**

```sql
SELECT campaign_id, campaign_name, status
FROM active_campaigns
UNION
SELECT campaign_id, campaign_name, status
FROM completed_campaigns;
```

Este ejemplo combina campañas activas y completadas en un solo conjunto de resultados.

---

## Uso de ChatGPT para el Operador UNION

### **1. Generar Consultas UNION**

**Prompt:**  
*"¿Cómo puedo combinar sesiones de dos tablas diferentes en un solo conjunto de resultados únicos?"*

**Respuesta de ChatGPT:**  
```sql
SELECT session_id, utm_source_medium
FROM sessions_2023
UNION
SELECT session_id, utm_source_medium
FROM sessions_2024;
```

### **2. Explicación de Consultas UNION**

**Prompt:**  
*"¿Qué hace esta consulta?*  
```sql
SELECT transaction_id, gross_revenue
FROM transactions
UNION
SELECT sales_id, total_revenue
FROM sales;
```*

**Respuesta de ChatGPT:**  
*"Esta consulta combina las columnas `transaction_id` y `gross_revenue` de la tabla `transactions` con las columnas `sales_id` y `total_revenue` de la tabla `sales`, eliminando registros duplicados."*

---

## Resumen

El operador UNION en SQL es una herramienta poderosa para consolidar datos de múltiples fuentes en un solo conjunto de resultados, asegurando que solo se incluyan registros únicos. En **eseidGambling**, UNION es útil para analizar datos combinados de sesiones, campañas y transacciones. Con **ChatGPT**, puedes construir y comprender consultas UNION de manera más efectiva.
