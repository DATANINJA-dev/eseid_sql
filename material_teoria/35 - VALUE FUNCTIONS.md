
# Funciones de Ventana de Valor en SQL

## Introducción

Las funciones de ventana de valor en SQL operan sobre valores de filas en una ventana definida y permiten realizar comparaciones avanzadas sin alterar el número de filas. En este caso de uso, estas funciones son esenciales para analizar cambios entre sesiones, transacciones y costos de campañas.

---

## Funciones Principales de Ventana de Valor

### 1. LAG()

La función `LAG()` permite acceder al valor de una fila anterior dentro de la misma ventana.

**Ejemplo:** Comparar el ingreso generado en una transacción con el de la transacción anterior dentro del mismo mercado.

```sql
SELECT 
  market_id, 
  date_, 
  gross_revenue, 
  LAG(gross_revenue, 1) OVER (PARTITION BY market_id ORDER BY date_) AS previous_revenue
FROM purchase;
```

### 2. LEAD()

La función `LEAD()` permite acceder al valor de una fila posterior dentro de la misma ventana.

**Ejemplo:** Comparar el costo de una campaña con el costo de la campaña siguiente en el mismo mercado.

```sql
SELECT 
  market_id, 
  date_, 
  cost_campaign, 
  LEAD(cost_campaign, 1) OVER (PARTITION BY market_id ORDER BY date_) AS next_cost
FROM costs;
```

### 3. FIRST_VALUE()

La función `FIRST_VALUE()` recupera el primer valor dentro de una ventana ordenada.

**Ejemplo:** Identificar la primera fuente de tráfico utilizada en un mercado específico.

```sql
SELECT 
  market_id, 
  date_, 
  utm_source, 
  FIRST_VALUE(utm_source) OVER (PARTITION BY market_id ORDER BY date_) AS first_source
FROM purchase;
```

### 4. LAST_VALUE()

La función `LAST_VALUE()` recupera el último valor dentro de una ventana ordenada. Requiere ajustar el marco de filas para obtener resultados precisos.

**Ejemplo:** Determinar el ingreso más reciente de un mercado.

```sql
SELECT 
  market_id, 
  date_, 
  gross_revenue, 
  LAST_VALUE(gross_revenue) OVER (PARTITION BY market_id ORDER BY date_ ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS last_revenue
FROM purchase;
```

### 5. NTH_VALUE()

La función `NTH_VALUE()` permite recuperar el enésimo valor dentro de una ventana ordenada.

**Ejemplo:** Identificar la tercera mayor cantidad de sesiones en cada mercado.

```sql
SELECT 
  market_id, 
  date_, 
  sessions, 
  NTH_VALUE(sessions, 3) OVER (PARTITION BY market_id ORDER BY sessions DESC) AS third_highest_sessions
FROM sessions;
```

---

## Casos de Uso

1. **Análisis de Cambios de Ingresos:** Utiliza `LAG()` y `LEAD()` para evaluar variaciones entre transacciones consecutivas por mercado.
2. **Identificación de Patrones Iniciales y Finales:** Emplea `FIRST_VALUE()` y `LAST_VALUE()` para determinar las métricas clave al inicio y final de una secuencia.
3. **Evaluación de Métricas Personalizadas:** Usa `NTH_VALUE()` para analizar métricas específicas como las campañas más costosas.

---

## Uso de ChatGPT para Funciones de Ventana de Valor

### **1. Generar Consultas Avanzadas**

**Prompt:**  
*"¿Cómo puedo comparar los ingresos generados en una transacción con la transacción anterior dentro del mismo mercado?"*

**Respuesta de ChatGPT:**  
```sql
SELECT 
  market_id, 
  date_, 
  gross_revenue, 
  LAG(gross_revenue, 1) OVER (PARTITION BY market_id ORDER BY date_) AS previous_revenue
FROM purchase;
```

### **2. Explicación de Consultas**

**Prompt:**  
*"¿Qué hace esta consulta?*  
```sql
SELECT 
  market_id, 
  date_, 
  utm_source, 
  FIRST_VALUE(utm_source) OVER (PARTITION BY market_id ORDER BY date_) AS first_source
FROM purchase;
```*

**Respuesta de ChatGPT:**  
*"Esta consulta identifica la primera fuente de tráfico (`utm_source`) utilizada en cada mercado (`market_id`) al ordenar los datos por fecha (`date_`)."*

---

## Resumen

Las funciones de ventana de valor en SQL son herramientas poderosas para realizar análisis comparativos y secuenciales en datos. Estas funciones permiten estudiar cambios entre transacciones, identificar tendencias iniciales y finales, y analizar métricas específicas con facilidad.
