
# Sentencia INSERT INTO en SQL

En esta sección, exploramos el uso de la sentencia `INSERT INTO` en el contexto de **eseidGambling**, mostrando cómo agregar nuevos registros a las tablas `sessions`, `cost` y `purchase`. Además, veremos ejemplos prácticos en **Databricks** y cómo **ChatGPT** puede ser una herramienta útil para comprender y optimizar estas consultas.

---

## **¿Qué es la Sentencia INSERT INTO?**

La sentencia `INSERT INTO` permite agregar nuevos registros a una tabla en SQL. Esto es esencial para gestionar y actualizar los datos en las bases de datos.

### **Características Clave**
- **Flexibilidad**: Puedes insertar valores en todas las columnas o en columnas específicas.
- **Integridad de los Datos**: Asegúrate de cumplir con las restricciones del esquema de la tabla, como tipos de datos y restricciones NOT NULL.

---

## **Sintaxis Básica**

### Insertar valores en columnas específicas:
```sql
INSERT INTO table_name (column1, column2) 
VALUES (value1, value2);
```

### Insertar valores en todas las columnas:
```sql
INSERT INTO table_name 
VALUES (value1, value2, value3);
```

---

## **Ejemplos en eseidGambling**

### **1. Insertar un Registro en la Tabla sessions**
Agregamos un nuevo registro para una sesión:

```sql
INSERT INTO sessions (date, market_id, utm_source_medium, sessions) 
VALUES ('2023-11-15', 'ES', 'google/organic', 500);
```

### **2. Insertar un Registro en la Tabla cost**
Añadimos un costo de campaña:

```sql
INSERT INTO cost (market_id, date, utm_source, utm_medium, cost_campaign) 
VALUES ('IT', '2023-11-15', 'bing', 'cpc', 300);
```

### **3. Insertar Varias Transacciones en purchase**
Incluimos múltiples registros de transacciones:

```sql
INSERT INTO purchase (market_id, date, utm_source, utm_medium, booking_id, customer_id, gross_revenue) 
VALUES 
    ('AU', '2023-11-15', 'travelzoo', 'email', 123456, 78910, 1500),
    ('ES', '2023-11-16', 'google', 'organic', 123457, 78911, 2000);
```

---

## **Uso en Databricks**

En **Databricks**, puedes usar la sentencia `INSERT INTO` para agregar datos a las tablas previamente creadas o vistas. Por ejemplo:

```sql
INSERT INTO sessions (date, market_id, utm_source_medium, sessions) 
VALUES ('2023-11-15', 'ES', 'google/organic', 500);
```

Esto actualiza automáticamente la tabla `sessions` con un nuevo registro.

---

## **Cómo Usar ChatGPT para Ayuda con INSERT INTO**

### **1. Generación de Consultas**
**Prompt:**  
*"¿Cómo puedo usar INSERT INTO para agregar un nuevo registro en la tabla `sessions` con las columnas `date`, `market_id`, `utm_source_medium`, y `sessions`?"*

**Respuesta de ChatGPT:**  
```sql
INSERT INTO sessions (date, market_id, utm_source_medium, sessions) 
VALUES ('2023-11-15', 'ES', 'google/organic', 500);
```

### **2. Explicación de Consultas**
**Prompt:**  
*"¿Qué hace esta consulta?*  
```sql
INSERT INTO cost (market_id, date, utm_source, utm_medium, cost_campaign) 
VALUES ('IT', '2023-11-15', 'bing', 'cpc', 300);
```*

**Respuesta de ChatGPT:**  
*"Esta consulta agrega un nuevo registro a la tabla `cost`, indicando un costo de campaña de 300 en el mercado 'IT'."*

---

## **Conclusión**

La sentencia `INSERT INTO` es esencial para agregar nuevos datos a las tablas. En el caso de **eseidGambling**, permite registrar sesiones, costos y transacciones fácilmente. Herramientas como **Databricks** y **ChatGPT** hacen que trabajar con esta sentencia sea más eficiente y comprensible.
