# Tipos de Datos SQL

## Introducción

Los tipos de datos en SQL son atributos que especifican el tipo de datos que se pueden almacenar en una columna de la tabla. Son esenciales para garantizar la integridad de los datos y el procesamiento eficiente. En el contexto de **eseidGambling**, comprender los tipos de datos nos permite estructurar las tablas de manera que reflejen la información clave de sesiones, costos y transacciones de la plataforma.

---

## Tipos de Datos

### Tipos de Datos Numéricos

- **Tipos de Entero**:
  - `smallint`: Almacena números enteros, rango pequeño (2 bytes, -32,768 a +32,767).
  - `integer`: Enteros típicos (4 bytes, -2,147,483,648 a +2,147,483,647).
  - `bigint`: Enteros de gran rango (8 bytes, -9,223,372,036,854,775,808 a +9,223,372,036,854,775,807).
  - `decimal`: Precisión especificada por el usuario, exacta variable (hasta 131,072 dígitos antes y 16,383 después del punto decimal).

**Ejemplo en eseidGambling**:  
La columna `gross_revenue` en la tabla `purchase` puede utilizar el tipo `decimal(10,2)` para almacenar valores precisos de ingresos.

```sql
CREATE TABLE purchase (
    purchase_id SERIAL PRIMARY KEY,
    gross_revenue DECIMAL(10,2)
);
```

### Tipos de Cadenas de Caracteres

- `CHAR(n)`: Cadena de longitud fija, rellena de espacios en blanco.
- `VARCHAR(n)`: Cadena de longitud variable con un límite.
- `text`: Longitud variable ilimitada.

**Ejemplo en eseidGambling**:  
La columna `utm_source_medium` en la tabla `sessions` puede utilizar `VARCHAR(50)` para almacenar descripciones como "google/organic".

```sql
CREATE TABLE sessions (
    session_id SERIAL PRIMARY KEY,
    utm_source_medium VARCHAR(50)
);
```

### Tipos de Fecha/Hora

- `timestamp`: Fecha y hora (sin zona horaria), 8 bytes.
- `date`: Fecha (sin hora del día), 4 bytes.
- `time`: Hora del día (sin fecha), 8 bytes.
- `interval`: Intervalo de tiempo, 12 bytes (rango: -178,000,000 años a +178,000,000 años).

**Ejemplo en eseidGambling**:  
La columna `session_start` en la tabla `sessions` puede utilizar el tipo `timestamp` para registrar el inicio de cada sesión.

```sql
CREATE TABLE sessions (
    session_id SERIAL PRIMARY KEY,
    session_start TIMESTAMP
);
```

### Tipos de Datos Personalizados

- Los usuarios pueden definir tipos de datos personalizados según los requisitos.
- Ejemplos:
  - `CREATE TYPE Dollar AS DECIMAL(9,2);`
  - `CREATE TYPE days AS ENUM ('Lunes', 'Martes', 'Miércoles', 'Jueves', 'Viernes', 'Sábado', 'Domingo');`

**Ejemplo en eseidGambling**:  
Definir un tipo personalizado para los días de la semana puede ayudar a registrar patrones estacionales.

```sql
CREATE TYPE days AS ENUM ('Lunes', 'Martes', 'Miércoles', 'Jueves', 'Viernes', 'Sábado', 'Domingo');
```

---

## Uso de ChatGPT para Comprender Tipos de Datos

### **1. Selección de Tipos de Datos**
**Prompt:**  
*"¿Qué tipo de dato debo usar para almacenar el ingreso bruto en la tabla `purchase`?"*

**Respuesta de ChatGPT:**  
*"Para almacenar el ingreso bruto, utiliza el tipo `DECIMAL(10,2)` si necesitas precisión en valores monetarios."*

### **2. Explicación de Tipos de Datos**
**Prompt:**  
*"¿Cuál es la diferencia entre `CHAR(50)` y `VARCHAR(50)`?"*

**Respuesta de ChatGPT:**  
*"`CHAR(50)` siempre almacena una cadena de longitud fija de 50 caracteres, rellenando con espacios si es necesario. `VARCHAR(50)` solo utiliza el espacio necesario hasta 50 caracteres."*

---

## Resumen

Entender los tipos de datos en SQL es fundamental para el diseño de bases de datos y la integridad de los datos. En el caso de **eseidGambling**, elegir los tipos de datos adecuados asegura que la información de sesiones, costos y transacciones se maneje eficientemente. Además, el uso de herramientas como **ChatGPT** puede guiarte en la selección de los tipos correctos y en la optimización de tus consultas SQL.
