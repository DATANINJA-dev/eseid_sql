
# Comprensión de las Primary y Foreign Keys en SQL

---

En esta sección, adaptamos los conceptos de Claves Primarias y Claves Foráneas al caso real de **eseidGambling**, utilizando las tablas proporcionadas para demostrar cómo estas claves ayudan a mantener la integridad de los datos y permiten relaciones efectivas entre tablas en una base de datos relacional. Este enfoque práctico se complementa con su implementación en **Databricks** y el uso de **ChatGPT** para optimizar el aprendizaje.

---

## **Claves Primarias**

Una clave primaria identifica de manera única cada fila en una tabla. En el caso de **eseidGambling**, estas claves son fundamentales para distinguir registros únicos, como usuarios o campañas publicitarias, y para garantizar la integridad de los datos en todas las tablas.

### **Características de las Claves Primarias**
- **Unicidad**: Cada fila en una tabla debe tener un valor único de clave primaria.
- **No Nulidad**: Las claves primarias no pueden contener valores nulos.

### **Ejemplo en eseidGambling**
En la tabla `purchase_business_case`, la columna `booking_id` actúa como la clave primaria, asegurando que cada transacción registrada sea única.

```plaintext
| booking_id | customer_id | market_id | date_       | gross_revenue |
|------------|-------------|-----------|-------------|---------------|
| 166011     | 142286      | AU        | 2023-02-13  | 3413          |
| 169015     | 106993      | AU        | 2023-02-27  | 5449          |
```

---

## **Claves Foráneas**

Las claves foráneas son esenciales para establecer relaciones entre tablas. En el caso de **eseidGambling**, vinculan datos entre sesiones, costos de campañas y transacciones.

### **Ejemplo en eseidGambling**
En la tabla `sessions_business_case`, la columna `market_id` se relaciona con la misma columna en la tabla `costs_business_case`, permitiendo analizar las sesiones por mercado y vincularlas con los costos de las campañas en ese mercado.

```plaintext
Tabla: sessions_business_case
| date_       | market_id | utm_source_medium   | sessions |
|-------------|-----------|---------------------|----------|
| 2023-01-01  | ES        | google/organic      | 863      |
| 2023-01-01  | IT        | bing/organic        | 3        |

Tabla: costs_business_case
| market_id | date_       | utm_source | utm_medium | cost_campaign |
|-----------|-------------|------------|------------|---------------|
| ES        | 2023-01-05  | google     | cpc        | 215           |
| IT        | 2023-01-10  | bing       | cpc        | 0             |
```

Estas relaciones permiten unir información de sesiones con los costos asociados a las campañas, obteniendo insights clave sobre el rendimiento de las estrategias de marketing.

---

