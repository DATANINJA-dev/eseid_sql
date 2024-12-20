# LEFT JOIN en SQL

## Introducción

LEFT JOIN, también conocido como LEFT OUTER JOIN, es una operación esencial en SQL utilizada para combinar filas de dos tablas. A diferencia del INNER JOIN, devuelve todas las filas de la tabla izquierda, incluso si no hay coincidencias en la tabla derecha. En **eseidGambling**, este tipo de unión es útil para analizar datos incompletos, como sesiones sin transacciones o campañas sin costos asociados.

---

## Explicación Conceptual

LEFT JOIN incluye todos los registros de la tabla izquierda y los registros coincidentes de la tabla derecha. Si no hay coincidencia, el resultado es NULL en el lado de la tabla derecha. Este tipo de unión es particularmente útil cuando necesitas mantener todos los registros en una tabla independientemente de si tienen entradas correspondientes en otra tabla.

### Aplicaciones en eseidGambling:
- Analizar sesiones que no generaron ingresos.
- Identificar campañas sin costos asociados.
- Crear informes completos, incluso cuando faltan datos en algunas tablas.

---

## Sintaxis y Uso

La sintaxis para un LEFT JOIN es:

```sql
SELECT table1.column1, table2.column2...
FROM table1
LEFT JOIN table2
ON table1.common_field = table2.common_field;
```

Aquí, `table1` es la tabla izquierda, y `table2` es la tabla derecha. La cláusula `ON` especifica la condición para la unión.

---

## Ejemplos Prácticos en eseidGambling

### **1. Identificar Sesiones Sin Transacciones**

```sql
SELECT 
  sessions.session_id, 
  sessions.utm_source_medium, 
  transactions.transaction_id
FROM sessions
LEFT JOIN transactions
ON sessions.session_id = transactions.session_id;
```

Esta consulta incluye todas las sesiones, marcando con `NULL` aquellas que no tienen transacciones asociadas.

### **2. Analizar Campañas Sin Costos**

```sql
SELECT 
  campaigns.campaign_name, 
  costs.total_cost
FROM campaigns
LEFT JOIN costs
ON campaigns.campaign_id = costs.campaign_id;
```

Aquí, se listan todas las campañas, incluso aquellas que no tienen un costo registrado.

### **3. Generar Informes Completos de Transacciones y Usuarios**

```sql
SELECT 
  users.user_id, 
  users.user_name, 
  transactions.gross_revenue
FROM users
LEFT JOIN transactions
ON users.user_id = transactions.user_id;
```

Este ejemplo incluye todos los usuarios y muestra los ingresos generados por cada uno. Para los usuarios sin transacciones, el valor de `gross_revenue` será `NULL`.

---

## Uso de ChatGPT para LEFT JOIN

### **1. Crear Consultas LEFT JOIN**

**Prompt:**  
*"¿Cómo puedo listar todas las sesiones y marcar cuáles no tienen transacciones asociadas?"*

**Respuesta de ChatGPT:**  
```sql
SELECT 
  sessions.session_id, 
  sessions.utm_source_medium, 
  transactions.transaction_id
FROM sessions
LEFT JOIN transactions
ON sessions.session_id = transactions.session_id;
```

### **2. Explicación de Consultas LEFT JOIN**

**Prompt:**  
*"¿Qué hace esta consulta?*  
```sql
SELECT campaigns.campaign_name, 
       costs.total_cost
FROM campaigns
LEFT JOIN costs
ON campaigns.campaign_id = costs.campaign_id;
```*

**Respuesta de ChatGPT:**  
*"Esta consulta lista todas las campañas, incluyendo el nombre de la campaña y el costo total asociado. Si una campaña no tiene un costo registrado, el campo `total_cost` será NULL."*

---

## Resumen

LEFT JOIN es vital para las consultas SQL donde es esencial incluir todas las filas de una tabla, independientemente de si coinciden con filas en otra tabla. En el caso de **eseidGambling**, este enfoque permite analizar datos incompletos y generar informes más detallados. Además, herramientas como **ChatGPT** pueden ayudarte a construir y comprender consultas LEFT JOIN para abordar escenarios específicos.
