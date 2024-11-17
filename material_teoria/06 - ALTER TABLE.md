
# Sentencia ALTER TABLE en SQL

En esta sección, exploramos el uso de la sentencia `ALTER TABLE` en el contexto de **eseidGambling**, mostrando cómo modificar la estructura de las tablas `sessions`, `cost` y `purchase`. Además, veremos ejemplos prácticos en **Databricks** y cómo **ChatGPT** puede ser una herramienta útil para comprender y optimizar estas consultas.

---

## **¿Qué es la Sentencia ALTER TABLE?**

La sentencia `ALTER TABLE` permite modificar la estructura de una tabla existente en SQL. Esto incluye añadir, eliminar o modificar columnas, así como añadir o eliminar restricciones.

### **Acciones Comunes**
- **Columnas**: Añadir, eliminar, modificar o renombrar columnas.
- **Restricciones**: Añadir o eliminar restricciones como NOT NULL, CHECK o FOREIGN KEY.

---

## **Sintaxis Básica**

```sql
ALTER TABLE table_name
[Specify Actions];
```

---

## **Ejemplos en eseidGambling**

### **1. Añadir una Nueva Columna**
Queremos añadir una columna `campaign_name` a la tabla `cost`:

```sql
ALTER TABLE cost 
ADD campaign_name VARCHAR(255);
```

### **2. Eliminar una Columna**
Si ya no necesitamos la columna `utm_source` en la tabla `sessions`:

```sql
ALTER TABLE sessions 
DROP COLUMN utm_source;
```

### **3. Modificar el Tipo de Datos de una Columna**
Cambiamos el tipo de datos de `gross_revenue` en la tabla `purchase` a `FLOAT`:

```sql
ALTER TABLE purchase 
ALTER COLUMN gross_revenue TYPE FLOAT;
```

### **4. Renombrar una Columna**
Renombramos la columna `market_id` en la tabla `sessions` a `region_id`:

```sql
ALTER TABLE sessions 
RENAME COLUMN market_id TO region_id;
```

### **5. Añadir una Restricción NOT NULL**
Establecemos que la columna `date` en la tabla `sessions` no puede ser NULL:

```sql
ALTER TABLE sessions 
ALTER COLUMN date SET NOT NULL;
```

### **6. Añadir una Clave Primaria**
Designamos la columna `booking_id` como clave primaria en la tabla `purchase`:

```sql
ALTER TABLE purchase 
ADD PRIMARY KEY (booking_id);
```

---

## **Uso en Databricks**

En **Databricks**, puedes utilizar la sentencia `ALTER TABLE` para modificar estructuras de tablas existentes. Por ejemplo:

```sql
ALTER TABLE cost 
ADD campaign_name VARCHAR(255);
```

Este comando añade una nueva columna `campaign_name` a la tabla `cost`.

---

## **Cómo Usar ChatGPT para Ayuda con ALTER TABLE**

### **1. Generación de Consultas**
**Prompt:**  
*"¿Cómo puedo añadir una columna llamada `campaign_name` de tipo VARCHAR a la tabla `cost`?"*

**Respuesta de ChatGPT:**  
```sql
ALTER TABLE cost 
ADD campaign_name VARCHAR(255);
```

### **2. Explicación de Consultas**
**Prompt:**  
*"¿Qué hace esta consulta?*  
```sql
ALTER TABLE sessions 
DROP COLUMN utm_source;
```*

**Respuesta de ChatGPT:**  
*"Esta consulta elimina la columna `utm_source` de la tabla `sessions`."*

---

## **Conclusión**

La sentencia `ALTER TABLE` es fundamental para gestionar y actualizar la estructura de las tablas. En el caso de **eseidGambling**, permite realizar cambios dinámicos como añadir restricciones o modificar columnas para adaptarse a nuevas necesidades. Herramientas como **Databricks** y **ChatGPT** hacen que trabajar con esta sentencia sea más eficiente y comprensible.
