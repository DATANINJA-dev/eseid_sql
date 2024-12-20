
# Funciones de Ventana en SQL

## Introducción

Las funciones de ventana en SQL permiten realizar cálculos avanzados sobre un conjunto de filas relacionadas con la fila actual, sin colapsar los resultados en una sola fila. En el contexto de este business case, estas funciones son útiles para calcular métricas como ingresos acumulados, rankings de campañas y comparación de datos entre filas consecutivas.

---

## Tipos de Funciones de Ventana

### 1. Funciones Agregadas de Ventana
- `SUM()`: Calcula la suma acumulativa.
- `COUNT()`: Cuenta el número de filas.
- `AVG()`: Calcula el promedio.

### 2. Funciones de Clasificación
- `ROW_NUMBER()`: Asigna un número único a cada fila dentro de una partición.
- `RANK()`: Asigna rangos con huecos para valores empatados.
- `DENSE_RANK()`: Similar a `RANK()`, pero sin huecos.

### 3. Funciones de Valor
- `LAG()`: Recupera el valor de la fila anterior.
- `LEAD()`: Recupera el valor de la fila siguiente.

---

## Ejemplos Prácticos

### **1. Ranking de Fuentes por Ingresos Totales**

Clasificar las fuentes (`utm_source`) en cada mercado (`market_id`) según los ingresos totales.

```sql
SELECT market_id, 
       utm_source, 
       SUM(gross_revenue) AS total_revenue,
       RANK() OVER (PARTITION BY market_id ORDER BY SUM(gross_revenue) DESC) AS source_rank
FROM purchase
GROUP BY market_id, utm_source;
```

### **2. Total Acumulado de Costos por Mercado**

Calcular el costo acumulado de campañas en cada mercado.

```sql
SELECT market_id, 
       date_, 
       SUM(cost_campaign) OVER (PARTITION BY market_id ORDER BY date_) AS cumulative_cost
FROM costs;
```

### **3. Comparar Sesiones Entre Fechas Consecutivas**

Comparar el número de sesiones entre fechas consecutivas en cada mercado.

```sql
SELECT market_id, 
       date_, 
       sessions, 
       LAG(sessions) OVER (PARTITION BY market_id ORDER BY date_) AS previous_sessions,
       LEAD(sessions) OVER (PARTITION BY market_id ORDER BY date_) AS next_sessions
FROM sessions;
```

### **4. Identificar la Primera y Última Fuente por Mercado**

Determinar la primera y última fuente (`utm_source`) de ingresos por mercado ordenada por fecha.

```sql
SELECT market_id, 
       utm_source, 
       FIRST_VALUE(utm_source) OVER (PARTITION BY market_id ORDER BY date_) AS first_source,
       LAST_VALUE(utm_source) OVER (PARTITION BY market_id ORDER BY date_ ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS last_source
FROM purchase;
```

---

## Resumen

Las funciones de ventana son herramientas poderosas para realizar cálculos avanzados y análisis sofisticados en SQL. Estas consultas permiten obtener insights clave sobre ingresos, costos y sesiones utilizando las tablas proporcionadas.
