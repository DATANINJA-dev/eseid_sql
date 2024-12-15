# Funciones de Ventana de Valor en SQL

## Introducción

Las funciones de ventana de valor en SQL operan sobre valores de filas en una ventana definida y permiten realizar comparaciones avanzadas sin alterar el número de filas. En el contexto de **eseidGambling**, estas funciones son esenciales para analizar cambios entre sesiones, transacciones y métricas de campañas.

---

## Funciones Principales de Ventana de Valor

### 1. LAG()

La función `LAG()` permite acceder al valor de una fila anterior dentro de la misma ventana.

**Ejemplo en eseidGambling:** Comparar el ingreso generado en una transacción con el de la transacción anterior:

```sql
SELECT 
  transaction_id, 
  user_id, 
  gross_revenue, 
  LAG(gross_revenue, 1) OVER (PARTITION BY user_id ORDER BY transaction_date) AS previous_revenue
FROM transactions;
```

### 2. LEAD()

La función `LEAD()` permite acceder al valor de una fila posterior dentro de la misma ventana.

**Ejemplo en eseidGambling:** Comparar el ingreso generado en una transacción con el de la transacción siguiente:

```sql
SELECT 
  transaction_id, 
  user_id, 
  gross_revenue, 
  LEAD(gross_revenue, 1) OVER (PARTITION BY user_id ORDER BY transaction_date) AS next_revenue
FROM transactions;
```

### 3. FIRST_VALUE()

La función `FIRST_VALUE()` recupera el primer valor dentro de una ventana ordenada.

**Ejemplo en eseidGambling:** Identificar el primer ingreso generado por un usuario:

```sql
SELECT 
  user_id, 
  transaction_date, 
  gross_revenue, 
  FIRST_VALUE(gross_revenue) OVER (PARTITION BY user_id ORDER BY transaction_date) AS first_revenue
FROM transactions;
```

### 4. LAST_VALUE()

La función `LAST_VALUE()` recupera el último valor dentro de una ventana ordenada. Requiere ajustar el marco de filas para obtener resultados precisos.

**Ejemplo en eseidGambling:** Identificar el ingreso más reciente de un usuario:

```sql
SELECT 
  user_id, 
  transaction_date, 
  gross_revenue, 
  LAST_VALUE(gross_revenue) OVER (PARTITION BY user_id ORDER BY transaction_date ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS last_revenue
FROM transactions;
```

### 5. NTH_VALUE()

La función `NTH_VALUE()` permite recuperar el enésimo valor dentro de una ventana ordenada.

**Ejemplo en eseidGambling:** Identificar la tercera transacción más alta de un usuario:

```sql
SELECT 
  user_id, 
  transaction_date, 
  gross_revenue, 
  NTH_VALUE(gross_revenue, 3) OVER (PARTITION BY user_id ORDER BY gross_revenue DESC) AS third_highest_revenue
FROM transactions;
```

---

## Casos de Uso en eseidGambling

1. **Análisis de Cambios de Ingresos:** Utiliza `LAG()` y `LEAD()` para evaluar variaciones entre transacciones consecutivas.
2. **Identificación de Patrones Iniciales y Finales:** Emplea `FIRST_VALUE()` y `LAST_VALUE()` para determinar métricas clave en los extremos de una secuencia.
3. **Evaluación de Métricas Personalizadas:** Usa `NTH_VALUE()` para analizar métricas específicas como las transacciones más altas.

---

## Uso de ChatGPT para Funciones de Ventana de Valor

### **1. Generar Consultas Avanzadas**

**Prompt:**  
*"¿Cómo puedo comparar los ingresos generados en una transacción con la transacción anterior?"*

**Respuesta de ChatGPT:**  
```sql
SELECT 
  transaction_id, 
  user_id, 
  gross_revenue, 
  LAG(gross_revenue, 1) OVER (PARTITION BY user_id ORDER BY transaction_date) AS previous_revenue
FROM transactions;
```

### **2. Explicación de Consultas**

**Prompt:**  
*"¿Qué hace esta consulta?*  
```sql
SELECT 
  user_id, 
  transaction_date, 
  gross_revenue, 
  FIRST_VALUE(gross_revenue) OVER (PARTITION BY user_id ORDER BY transaction_date) AS first_revenue
FROM transactions;
```*

**Respuesta de ChatGPT:**  
*"Esta consulta identifica el primer ingreso generado por cada usuario (`first_revenue`) al ordenar las transacciones por fecha (`transaction_date`)."*

---

## Resumen

Las funciones de ventana de valor en SQL son herramientas poderosas para realizar análisis comparativos y secuenciales en datos. En **eseidGambling**, estas funciones permiten estudiar cambios entre transacciones, identificar tendencias iniciales y finales, y analizar métricas específicas con facilidad. Con **ChatGPT**, puedes construir y entender consultas avanzadas de manera eficiente.
