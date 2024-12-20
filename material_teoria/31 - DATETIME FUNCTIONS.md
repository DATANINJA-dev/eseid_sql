# Funciones de Fecha y Hora en SQL

## Introducción

Las funciones de fecha y hora en SQL son esenciales para manejar y analizar valores temporales dentro de las bases de datos. En el contexto de **eseidGambling**, estas funciones permiten calcular métricas como duración de sesiones, tiempos entre transacciones y análisis de patrones estacionales.

---

## Explicación Conceptual

### Principales Funciones de Fecha y Hora

1. **CURRENT_DATE, CURRENT_TIME, CURRENT_TIMESTAMP**:  
   - `CURRENT_DATE`: Devuelve la fecha actual.
   - `CURRENT_TIME`: Devuelve la hora actual con la zona horaria.
   - `CURRENT_TIMESTAMP`: Devuelve la fecha y hora actuales con la zona horaria.

2. **AGE**:  
   - Calcula la diferencia entre dos fechas.

3. **EXTRACT**:  
   - Recupera partes específicas de un valor de fecha o hora, como día, mes, año, etc.

---

## Sintaxis y Uso

### CURRENT_DATE, CURRENT_TIME, CURRENT_TIMESTAMP
```sql
SELECT CURRENT_DATE;
SELECT CURRENT_TIME;
SELECT CURRENT_TIMESTAMP;
```

### AGE
```sql
SELECT AGE(timestamp1, timestamp2);
```

### EXTRACT
```sql
SELECT EXTRACT(unit FROM date);
```

---

## Ejemplos Prácticos en eseidGambling

### **1. Recuperar la Fecha y Hora Actuales**

```sql
SELECT CURRENT_DATE AS today, CURRENT_TIME AS now, CURRENT_TIMESTAMP AS current_timestamp;
```

Este ejemplo recupera la fecha y hora actuales para análisis en tiempo real.

### **2. Calcular la Duración de Sesiones (AGE)**

```sql
SELECT session_id, AGE(session_end, session_start) AS session_duration
FROM sessions;
```

Aquí se calcula la duración de cada sesión, lo que permite identificar patrones de comportamiento de los usuarios.

### **3. Extraer Partes de Fechas para Análisis (EXTRACT)**

```sql
SELECT session_id, EXTRACT(year FROM session_start) AS year, EXTRACT(month FROM session_start) AS month
FROM sessions;
```

Este ejemplo extrae el año y el mes de inicio de cada sesión para análisis estacional.

### **4. Calcular el Tiempo entre Transacciones**

```sql
SELECT transaction_id, user_id, AGE(lead(transaction_date) OVER (PARTITION BY user_id ORDER BY transaction_date), transaction_date) AS time_between_transactions
FROM transactions;
```

Este ejemplo calcula el tiempo transcurrido entre transacciones consecutivas de un usuario.

### **5. Convertir Fechas a Epoch para Comparaciones**

```sql
SELECT transaction_id, EXTRACT(EPOCH FROM transaction_date) AS transaction_epoch
FROM transactions;
```

Convierte las fechas de transacciones en formato epoch para análisis o cálculos avanzados.

---

## Uso de ChatGPT para Funciones de Fecha y Hora

### **1. Generar Consultas Temporales**

**Prompt:**  
*"¿Cómo puedo calcular la duración de cada sesión en mi tabla de sesiones?"*

**Respuesta de ChatGPT:**  
```sql
SELECT session_id, AGE(session_end, session_start) AS session_duration
FROM sessions;
```

### **2. Explicación de Consultas Temporales**

**Prompt:**  
*"¿Qué hace esta consulta?*  
```sql
SELECT transaction_id, user_id, AGE(lead(transaction_date) OVER (PARTITION BY user_id ORDER BY transaction_date), transaction_date) AS time_between_transactions
FROM transactions;
```*

**Respuesta de ChatGPT:**  
*"Esta consulta calcula el tiempo transcurrido entre transacciones consecutivas de cada usuario, utilizando la función `AGE` combinada con la función de ventana `LEAD`."*

---

## Resumen

Las funciones de fecha y hora en SQL son fundamentales para analizar y manipular datos sensibles al tiempo. En **eseidGambling**, estas funciones permiten calcular métricas clave como duración de sesiones, tiempos entre transacciones y patrones estacionales. Con **ChatGPT**, puedes crear y entender consultas más avanzadas para análisis temporales.
