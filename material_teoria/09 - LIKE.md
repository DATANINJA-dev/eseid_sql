
# Sentencia LIKE en SQL

En esta sección, exploramos el uso de la condición `LIKE` en el contexto de **eseidGambling**, mostrando cómo realizar búsquedas basadas en patrones en las tablas `sessions`, `cost` y `purchase`. Además, veremos ejemplos prácticos en **Databricks** y cómo **ChatGPT** puede ayudarte a optimizar tus consultas.

---

## **¿Qué es la Condición LIKE?**

La condición `LIKE` en SQL se utiliza para buscar valores que coincidan con un patrón específico en una columna. Es ideal para encontrar datos basados en coincidencias parciales o patrones específicos.

---

## **Sintaxis Básica**

```sql
SELECT column_name 
FROM table_name 
WHERE column_name LIKE pattern;
```

---

## **Comodines en LIKE**

### **1. Comodín `%`**
- Representa cualquier secuencia de caracteres, incluyendo cero caracteres.
  - `A%`: Cadenas que comienzan con 'A'.
  - `%A`: Cadenas que terminan con 'A'.
  - `A%B`: Cadenas que comienzan con 'A' y terminan con 'B'.

### **2. Comodín `_`**
- Representa un único carácter.
  - `AB_C`: Cadenas que comienzan con 'AB', tienen cualquier carácter en la posición siguiente y terminan con 'C'.

---

## **Ejemplos en eseidGambling**

### **1. Buscar Fuentes que Comiencen con 'google'**
Obtenemos todas las filas de la tabla `sessions` donde la columna `utm_source_medium` comienza con "google":

```sql
SELECT * 
FROM sessions 
WHERE utm_source_medium LIKE 'google%';
```

### **2. Buscar Fuentes que Contengan 'organic'**
Seleccionamos registros de la tabla `sessions` donde la columna `utm_source_medium` contiene "organic":

```sql
SELECT * 
FROM sessions 
WHERE utm_source_medium LIKE '%organic%';
```

### **3. Buscar Transacciones con IDs de Cliente que Terminen en '5'**
Filtramos las transacciones en la tabla `purchase` donde el `customer_id` termina en "5":

```sql
SELECT * 
FROM purchase 
WHERE customer_id LIKE '%5';
```

### **4. Excluir Patrones Específicos**
Excluimos campañas de la tabla `cost` donde la fuente comienza con "bing":

```sql
SELECT * 
FROM cost 
WHERE utm_source NOT LIKE 'bing%';
```

---

## **Uso en Databricks**

En **Databricks**, la condición `LIKE` puede ser utilizada para realizar búsquedas basadas en patrones. Por ejemplo:

```sql
SELECT * 
FROM sessions 
WHERE utm_source_medium LIKE '%organic%';
```

Esto devuelve todas las sesiones donde la fuente contiene la palabra "organic".

---

## **Cómo Usar ChatGPT para Ayuda con LIKE**

### **1. Generación de Consultas**
**Prompt:**  
*"¿Cómo puedo usar LIKE para buscar registros en la tabla `sessions` donde la columna `utm_source_medium` contiene 'organic'?"*

**Respuesta de ChatGPT:**  
```sql
SELECT * 
FROM sessions 
WHERE utm_source_medium LIKE '%organic%';
```

### **2. Explicación de Consultas**
**Prompt:**  
*"¿Qué hace esta consulta?*  
```sql
SELECT * 
FROM cost 
WHERE utm_source NOT LIKE 'bing%';
```*

**Respuesta de ChatGPT:**  
*"Esta consulta selecciona todas las filas de la tabla `cost` donde la columna `utm_source` no comienza con 'bing'."*

---

## **Conclusión**

La condición `LIKE` es una herramienta poderosa para realizar búsquedas basadas en patrones en SQL. En el caso de **eseidGambling**, es especialmente útil para analizar patrones en fuentes, medios y datos de clientes. Herramientas como **Databricks** y **ChatGPT** hacen que trabajar con esta sentencia sea más sencillo y eficiente.
