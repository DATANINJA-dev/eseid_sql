# Funciones de Ventana en SQL

## Introducción

Las funciones de ventana en SQL permiten realizar cálculos avanzados sobre un conjunto de filas relacionadas con la fila actual, sin colapsar los resultados en una sola fila. En el contexto de **eseidGambling**, estas funciones son útiles para calcular métricas como totales acumulados, rankings de campañas, o comparar datos entre filas consecutivas para identificar tendencias y patrones.

---

## Tipos de Funciones de Ventana

### 1. Funciones Agregadas de Ventana

Calculan métricas agregadas sobre un conjunto de filas, preservando las filas individuales. Ejemplos comunes incluyen:
- `AVG()`: Calcula el promedio de un conjunto de valores.
- `SUM()`: Calcula la suma acumulativa.
- `COUNT()`: Cuenta el número de filas.
- `MAX()` / `MIN()`: Obtiene el valor máximo o mínimo.

### 2. Funciones de Clasificación

Ordenan y asignan un rango a las filas dentro de una partición de un conjunto de resultados.
- `ROW_NUMBER()`: Asigna un número único a cada fila dentro de una partición.
- `RANK()`: Asigna rangos con huecos para valores empatados.
- `DENSE_RANK()`: Similar a `RANK()`, pero sin huecos.
- `NTILE()`: Divide las filas en un número específico de grupos.

### 3. Funciones de Valor

Permiten acceder a valores de filas precedentes, siguientes, o específicos dentro de un conjunto de datos.
- `LAG()`: Recupera el valor de la fila anterior.
- `LEAD()`: Recupera el valor de la fila siguiente.
- `FIRST_VALUE()`: Obtiene el primer valor de una partición ordenada.
- `LAST_VALUE()`: Obtiene el último valor de una partición ordenada.

---

## Sintaxis General

```sql
FUNCTION_NAME() OVER (
  [PARTITION BY column_name]
  [ORDER BY column_name ASC|DESC]
)
```

### Notas:
- `PARTITION BY` divide el conjunto de resultados en particiones.
- `ORDER BY` especifica el orden de las filas dentro de una partición.

---

## Ejemplos Prácticos en eseidGambling

### **1. Ranking de Campañas por Ingresos Totales**

```sql
SELECT campaign_id, 
       SUM(gross_revenue) AS total_revenue,
       RANK() OVER (ORDER BY SUM(gross_revenue) DESC) AS campaign_rank
FROM transactions
GROUP BY campaign_id;
```

Este ejemplo clasifica las campañas según sus ingresos totales.

### **2. Totales Acumulados de Sesiones por País**

```sql
SELECT country, 
       session_id, 
       COUNT(session_id) OVER (PARTITION BY country ORDER BY session_id) AS running_total_sessions
FROM sessions;
```

Calcula un total acumulado de sesiones por país.

### **3. Comparar Ingresos Entre Transacciones Consecutivas**

```sql
SELECT transaction_id, 
       gross_revenue, 
       LAG(gross_revenue) OVER (PARTITION BY user_id ORDER BY transaction_date) AS previous_revenue,
       LEAD(gross_revenue) OVER (PARTITION BY user_id ORDER BY transaction_date) AS next_revenue
FROM transactions;
```

Permite analizar cómo varían los ingresos entre transacciones consecutivas de cada usuario.

### **4. Identificar Campañas con Mayor ROI**

```sql
SELECT campaign_id, 
       SUM(gross_revenue) AS total_revenue,
       SUM(cost) AS total_cost,
       (SUM(gross_revenue) - SUM(cost)) AS net_revenue,
       NTILE(4) OVER (ORDER BY (SUM(gross_revenue) - SUM(cost)) DESC) AS roi_quartile
FROM campaigns
GROUP BY campaign_id;
```

Divide las campañas en cuartiles según su ROI neto.

### **5. Determinar Primera y Última Transacción de Usuarios**

```sql
SELECT user_id, 
       FIRST_VALUE(transaction_date) OVER (PARTITION BY user_id ORDER BY transaction_date) AS first_transaction,
       LAST_VALUE(transaction_date) OVER (PARTITION BY user_id ORDER BY transaction_date ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS last_transaction
FROM transactions;
```

Identifica las fechas de la primera y última transacción de cada usuario.

---

## Uso de ChatGPT para Funciones de Ventana

### **1. Generar Consultas con Funciones de Ventana**

**Prompt:**  
*"¿Cómo puedo calcular un total acumulado de sesiones por país en mi base de datos?"*

**Respuesta de ChatGPT:**  
```sql
SELECT country, 
       session_id, 
       COUNT(session_id) OVER (PARTITION BY country ORDER BY session_id) AS running_total_sessions
FROM sessions;
```

### **2. Explicación de Consultas de Ventana**

**Prompt:**  
*"¿Qué hace esta consulta?*  
```sql
SELECT transaction_id, 
       gross_revenue, 
       LAG(gross_revenue) OVER (PARTITION BY user_id ORDER BY transaction_date) AS previous_revenue
FROM transactions;
```*

**Respuesta de ChatGPT:**  
*"Esta consulta calcula el ingreso de la transacción anterior para cada usuario, lo que permite analizar cambios en los ingresos a lo largo del tiempo."*

---

## Resumen

Las funciones de ventana son herramientas poderosas para realizar cálculos avanzados y análisis sofisticados en SQL. En **eseidGambling**, estas funciones permiten clasificar campañas, calcular totales acumulados y analizar tendencias. Con **ChatGPT**, puedes diseñar consultas complejas que aprovechen todo el potencial de las funciones de ventana.
