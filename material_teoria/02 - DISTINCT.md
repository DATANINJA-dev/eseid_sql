
# Uso de DISTINCT en SQL

En esta sección, adaptamos el concepto de `DISTINCT` al caso de **eseidGambling**, explorando cómo eliminar valores duplicados en las consultas y aplicando estos conceptos a las tablas `sessions`, `cost` y `purchase`. Además, incluimos ejemplos en **Databricks** y el uso de **ChatGPT** para mejorar tu aprendizaje.

---

## **¿Qué es DISTINCT?**

La palabra clave `DISTINCT` en SQL se utiliza para eliminar registros duplicados en el conjunto de resultados, devolviendo solo valores únicos.

### **Características Clave**
- **Eliminación de Duplicados**: Asegura que cada fila sea única en el resultado.
- **Claridad en los Datos**: Proporciona una vista limpia y precisa, ideal para reportes.
- **Aplicación Flexible**: Puede aplicarse a una o más columnas.

---

## **Sintaxis Básica**

```sql
SELECT DISTINCT column_name 
FROM table_name;
```

Si deseas aplicar `DISTINCT` a múltiples columnas:

```sql
SELECT DISTINCT column1, column2 
FROM table_name;
```

---

## **Ejemplo en eseidGambling**

### **1. Obtener Mercados Únicos**
Para ver los mercados (`market_id`) en los que opera **eseidGambling**, puedes ejecutar:

```sql
SELECT DISTINCT market_id 
FROM sessions;
```

Esto devuelve una lista de todos los mercados únicos en la tabla `sessions`.

### **2. Combinar Múltiples Columnas**
Si quieres obtener combinaciones únicas de `market_id` y `utm_source_medium`:

```sql
SELECT DISTINCT market_id, utm_source_medium 
FROM sessions;
```

Este ejemplo es útil para entender qué fuentes y medios son más comunes en cada mercado.

---

## **Uso en Databricks**

En **Databricks**, estas consultas se pueden ejecutar directamente una vez que hayas cargado las tablas. Por ejemplo:

```sql
SELECT DISTINCT market_id 
FROM sessions;
```

Asegúrate de haber creado las vistas o cargado las tablas correctamente antes de ejecutar estas consultas.

---

## **Cómo Usar ChatGPT para Ayuda con DISTINCT**

### **1. Generación de Consultas**
**Prompt:**  
*"¿Cómo puedo usar DISTINCT para obtener combinaciones únicas de `market_id` y `utm_source_medium` en la tabla `sessions`?"*

**Respuesta de ChatGPT:**  
```sql
SELECT DISTINCT market_id, utm_source_medium 
FROM sessions;
```

### **2. Explicación de Consultas**
**Prompt:**  
*"¿Qué hace esta consulta?*  
```sql
SELECT DISTINCT market_id 
FROM sessions;
```*

**Respuesta de ChatGPT:**  
*"Esta consulta selecciona todos los valores únicos de la columna `market_id` en la tabla `sessions`."*

---

## **Conclusión**

El uso de `DISTINCT` es fundamental para eliminar duplicados y trabajar con datos limpios. En el contexto de **eseidGambling**, esto te permite identificar mercados únicos, combinaciones de fuentes y medios, y mucho más. Herramientas como **Databricks** y **ChatGPT** facilitan la ejecución y comprensión de estas consultas.
