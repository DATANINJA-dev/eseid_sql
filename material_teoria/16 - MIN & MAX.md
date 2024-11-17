
# Declaración `MIN` y `MAX` en SQL

En esta sección, exploramos el uso de las funciones `MIN()` y `MAX()` en el contexto de **eseidGambling**. Estas herramientas permiten identificar los valores extremos en columnas específicas, facilitando el análisis de datos.

## Introducción

- **`MIN()`**: Devuelve el valor más bajo o mínimo encontrado en una columna especificada. Útil para identificar precios más bajos, fechas más tempranas o valores mínimos en conjuntos de datos.
- **`MAX()`**: Devuelve el valor más alto o máximo de una columna especificada. Es útil para determinar salarios más altos, fechas más recientes o valores máximos.

En el caso de **eseidGambling**, estas funciones pueden emplearse para analizar la duración más corta o larga de sesiones, los costos mínimos o máximos de campañas publicitarias, o los ingresos extremos por transacción.

## Sintaxis Básica

```sql
-- Función MIN
SELECT MIN(column_name) FROM table_name;

-- Función MAX
SELECT MAX(column_name) FROM table_name;
```

## Ejemplos Adaptados

### Ejemplo 1: Encontrando el Mínimo y Máximo de Ingresos

```sql
SELECT MIN(revenue) AS min_revenue, MAX(revenue) AS max_revenue
FROM purchase;
```

Esta consulta devuelve el ingreso más bajo y más alto registrado en la tabla `purchase`.

### Ejemplo 2: Usando `MIN` y `MAX` con una Condición

```sql
SELECT MIN(session_duration) AS min_duration, MAX(session_duration) AS max_duration
FROM sessions
WHERE session_duration > 10;
```

Esta consulta devuelve la duración mínima y máxima de sesiones que superan los 10 minutos.

### Ejemplo 3: Identificando Valores Extremos por Campaña

```sql
SELECT campaign_id, MIN(campaign_cost) AS min_cost, MAX(campaign_cost) AS max_cost
FROM cost
GROUP BY campaign_id;
```

Esta consulta agrupa los costos por campaña y calcula el costo mínimo y máximo para cada una.

## Cuándo Usar `MIN` y `MAX`

- **Análisis de Extremos**: Para identificar los valores más pequeños y más grandes en columnas numéricas o de fecha.
- **Informes y Visualización**: Útil para destacar los límites en un conjunto de datos.
- **Comparaciones**: Facilita la comparación de valores extremos entre categorías o grupos.

## Consejos Prácticos

- **Combinar con `WHERE`**: Usa condiciones para filtrar resultados y encontrar valores extremos específicos.
- **Uso con `GROUP BY`**: Agrupa los datos para calcular valores mínimos y máximos por categoría.
- **Consideración de NULOS**: Ambas funciones ignoran automáticamente los valores `NULL` en los cálculos.

## Uso en Databricks

En Databricks, puedes ejecutar consultas con `MIN` y `MAX` directamente para identificar valores extremos en tablas cargadas. Por ejemplo:

```sql
SELECT MIN(revenue) AS min_revenue, MAX(revenue) AS max_revenue
FROM purchase;
```

Databricks presenta los resultados en un formato tabular, ideal para análisis rápido.

## ChatGPT

### ¿Cómo Puede Ayudar ChatGPT?

1. **Generar Consultas con `MIN` y `MAX`**: Solicita ejemplos específicos adaptados a tus necesidades.
   - *Ejemplo*: "Genera una consulta para encontrar los costos mínimos y máximos por campaña."

2. **Depurar Consultas**: Pega una consulta con `MIN` o `MAX` y pide ayuda para corregir errores o mejorar la lógica.

3. **Optimización**: Solicita mejoras para consultas complejas que usen estas funciones.

   *Ejemplo de Prompt*: 
   > "Optimiza esta consulta que identifica los valores más bajos y altos de ingresos."

## Conclusión

Las funciones `MIN()` y `MAX()` son esenciales para el análisis de datos en SQL. En el contexto de **eseidGambling**, permiten identificar valores extremos en sesiones, transacciones y campañas publicitarias. Su integración con condiciones y agrupaciones proporciona una poderosa herramienta para análisis detallado y efectivo.
