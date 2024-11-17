
# La Cláusula WHERE en SQL

En esta sección, exploramos el uso de la cláusula `WHERE` en el contexto de **eseidGambling**, mostrando cómo filtrar datos relevantes de las tablas `sessions`, `cost` y `purchase`. Además, veremos cómo utilizar **Databricks** para ejecutar consultas y **ChatGPT** para obtener soporte.

---

## **¿Qué es la Cláusula WHERE?**

La cláusula `WHERE` se utiliza para filtrar registros de una tabla, devolviendo solo aquellos que cumplen con las condiciones especificadas.

### **Funcionalidad Clave**
- **Filtrado Basado en Condiciones**: Selecciona solo las filas que cumplen con las condiciones.
- **Eficiencia y Relevancia**: Evita recuperar datos innecesarios, mejorando el rendimiento de las consultas y la relevancia de los resultados.

---

## **Sintaxis Básica**

```sql
SELECT column_name 
FROM table_name 
WHERE condition;
```

---

## **Ejemplo en eseidGambling**

### **1. Filtrar Sesiones por Fuente**
Si deseas ver todas las sesiones provenientes de "google/organic", la consulta sería:

```sql
SELECT * 
FROM sessions 
WHERE utm_source_medium = 'google/organic';
```

### **2. Filtrar por Mercado Específico**
Para obtener los datos de sesiones solo del mercado "ES":

```sql
SELECT * 
FROM sessions 
WHERE market_id = 'ES';
```

### **3. Filtrar Transacciones con Ingresos Altos**
Si queremos transacciones de la tabla `purchase` con ingresos (`gross_revenue`) mayores a 5000:

```sql
SELECT * 
FROM purchase 
WHERE gross_revenue > 5000;
```

---

## **Uso en Databricks**

En **Databricks**, puedes ejecutar estas consultas directamente sobre las tablas cargadas. Por ejemplo:

```sql
SELECT * 
FROM sessions 
WHERE market_id = 'IT';
```

Asegúrate de cargar las tablas correctamente antes de ejecutar las consultas.

---

## **Cómo Usar ChatGPT para Ayuda con WHERE**

### **1. Crear Consultas**
**Prompt:**  
*"¿Cómo puedo usar la cláusula WHERE para filtrar las sesiones del mercado 'IT' en la tabla `sessions`?"*

**Respuesta de ChatGPT:**  
```sql
SELECT * 
FROM sessions 
WHERE market_id = 'IT';
```

### **2. Explicación de Consultas**
**Prompt:**  
*"¿Qué hace esta consulta?*  
```sql
SELECT * 
FROM purchase 
WHERE gross_revenue > 5000;
```*

**Respuesta de ChatGPT:**  
*"Esta consulta selecciona todas las filas de la tabla `purchase` donde el valor de `gross_revenue` es mayor a 5000."*

---

## **Conclusión**

La cláusula `WHERE` es esencial para refinar tus consultas y filtrar datos en función de condiciones específicas. En el caso de **eseidGambling**, puedes usarla para analizar sesiones, transacciones o costos específicos. Herramientas como **Databricks** y **ChatGPT** te ayudan a aplicar y entender estas consultas con facilidad.
