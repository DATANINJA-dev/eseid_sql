# Subconsultas en SQL

## Introducción

Una subconsulta en SQL es una consulta anidada dentro de otra consulta. En el contexto de **eseidGambling**, las subconsultas son herramientas poderosas para realizar análisis complejos, como filtrar datos de sesiones, calcular ingresos o identificar usuarios según criterios específicos.

---

## Explicación Conceptual

Las subconsultas permiten consultas SQL más dinámicas y flexibles. Se pueden usar en varias partes de una consulta SQL, incluidas las cláusulas WHERE, FROM y SELECT, y permiten que la consulta principal dependa de los resultados de otra consulta.

### Tipos de Subconsultas

1. **Subconsulta en WHERE**: Filtra datos basados en el resultado de otra consulta.
2. **Subconsulta en FROM**: Crea una tabla temporal a partir de otra consulta.
3. **Subconsulta en SELECT**: Calcula valores individuales o agrega datos para usarlos como columnas.

---

## Sintaxis y Uso

La sintaxis general para una subconsulta es:

```sql
SELECT column_name1
FROM table_name1
WHERE column_name2 [Comparison Operator]
(SELECT column_name3
 FROM table_name2
 WHERE condition);
```

---

## Ejemplos Prácticos en eseidGambling

### **1. Subconsulta en WHERE: Filtrar Sesiones por Usuarios Activos**

```sql
SELECT *
FROM sessions
WHERE user_id IN
(SELECT DISTINCT user_id
 FROM transactions
 WHERE gross_revenue > 100);
```

Este ejemplo selecciona sesiones de usuarios que han generado ingresos mayores a 100 en la tabla `transactions`.

### **2. Subconsulta en FROM: Agregar Ingresos por Mercado**

```sql
SELECT m.market_id, m.market_name, t.total_revenue
FROM markets AS m
LEFT JOIN (SELECT market_id, SUM(gross_revenue) AS total_revenue
           FROM transactions
           GROUP BY market_id) AS t
ON m.market_id = t.market_id;
```

Esta consulta devuelve una lista de mercados con el total de ingresos generados, incluso para aquellos que no tienen transacciones.

### **3. Subconsulta en SELECT: Recuperar Nombre de Usuario**

```sql
SELECT session_id, 
       (SELECT user_name
        FROM users
        WHERE users.user_id = sessions.user_id) AS user_name
FROM sessions
ORDER BY session_id;
```

Aquí, se muestra el nombre del usuario asociado a cada sesión utilizando una subconsulta en la cláusula SELECT.

---

## Reglas para Subconsultas

1. Las subconsultas deben estar encerradas entre paréntesis.
2. Una subconsulta solo puede devolver una columna en la cláusula SELECT, a menos que sea parte de una tabla temporal.
3. No se puede usar el comando ORDER BY en una subconsulta.
4. Subconsultas que devuelven más de una fila solo pueden usarse con operadores como IN, EXISTS, ANY o ALL.

---

## Uso de ChatGPT para Subconsultas

### **1. Generar Subconsultas**

**Prompt:**  
*"¿Cómo puedo listar sesiones asociadas a usuarios que hayan generado más de 100 en ingresos?"*

**Respuesta de ChatGPT:**  
```sql
SELECT *
FROM sessions
WHERE user_id IN
(SELECT DISTINCT user_id
 FROM transactions
 WHERE gross_revenue > 100);
```

### **2. Explicación de Subconsultas**

**Prompt:**  
*"¿Qué hace esta consulta?*  
```sql
SELECT market_id, market_name, total_revenue
FROM markets AS m
LEFT JOIN (SELECT market_id, SUM(gross_revenue) AS total_revenue
           FROM transactions
           GROUP BY market_id) AS t
ON m.market_id = t.market_id;
```*

**Respuesta de ChatGPT:**  
*"Esta consulta combina la tabla `markets` con una subconsulta que calcula los ingresos totales (`total_revenue`) por mercado en la tabla `transactions`. Incluye todos los mercados, incluso aquellos sin transacciones."*

---

## Resumen

Las subconsultas en SQL proporcionan una forma flexible y poderosa de realizar consultas anidadas, permitiendo análisis complejos y dinámicos. En **eseidGambling**, las subconsultas son fundamentales para resolver problemas específicos, como filtrar datos o agregar información desde múltiples tablas. Con **ChatGPT**, puedes crear y comprender subconsultas más efectivas para abordar necesidades analíticas.
