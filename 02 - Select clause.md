## Sentencias SELECT: La Puerta de Entrada a la Recuperación de Datos

La sentencia SELECT es un componente fundamental de SQL, utilizado principalmente para la recuperación de datos de una base de datos. Es la herramienta más básica pero poderosa en SQL para consultar y extraer datos.

### Comprensión de las Sentencias SELECT

- **Propósito**: La sentencia SELECT se utiliza para seleccionar datos específicos de una o más tablas en una base de datos.
- **Flexibilidad**: Puedes optar por extraer todas las columnas de una tabla o especificar columnas particulares.
- **Combinación con Otras Cláusulas**: Las sentencias SELECT pueden combinarse con varias cláusulas (como WHERE, JOIN, ORDER BY) para refinar y personalizar la recuperación de datos.

### Sintaxis Básica

```sql
SELECT column_name1, column_name2 FROM table_name;
```

### Ejemplos
Seleccion un sola columna:
```sql
SELECT first_name FROM customer_table;
```
Selecciona multiples columnas:
```sql
SELECT first_name, last_name FROM customer_table;
```
Seleccion todas las columnas:
```sql
SELECT * FROM customer_table;
```