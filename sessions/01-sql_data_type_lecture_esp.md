<!-- # Tipos de Datos SQL -->

## Introducción

Los tipos de datos en SQL son atributos que especifican el tipo de datos que se pueden almacenar en una columna de la tabla. Son esenciales para garantizar la integridad de los datos y el procesamiento eficiente.

## Tipos de Datos

### Tipos de Datos Numéricos

- **Tipos de Entero**:
  - `smallint`: Almacena números enteros, rango pequeño (2 bytes, -32,768 a +32,767).
  - `integer`: Enteros típicos (4 bytes, -2,147,483,648 a +2,147,483,647).
  - `bigint`: Enteros de gran rango (8 bytes, -9,223,372,036,854,775,808 a +9,223,372,036,854,775,807).
  - `decimal`: Precisión especificada por el usuario, exacta variable (hasta 131,072 dígitos antes y 16,383 después del punto decimal).

### Tipos de Cadenas de Caracteres

- `CHAR(n)`: Cadena de longitud fija, rellena de espacios en blanco.
- `VARCHAR(n)`: Cadena de longitud variable con un límite.
- `text`: Longitud variable ilimitada.

### Tipos de Fecha/Hora

- `timestamp`: Fecha y hora (sin zona horaria), 8 bytes.
- `date`: Fecha (sin hora del día), 4 bytes.
- `time`: Hora del día (sin fecha), 8 bytes.
- `interval`: Intervalo de tiempo, 12 bytes (rango: -178,000,000 años a +178,000,000 años).

### Tipos de Datos Personalizados

- Los usuarios pueden definir tipos de datos personalizados según los requisitos.
- Ejemplos:
  - `CREATE TYPE Dollar AS DECIMAL(9,2);`
  - `CREATE TYPE days AS ENUM ('Lunes', 'Martes', 'Miércoles', 'Jueves', 'Viernes', 'Sábado', 'Domingo');`

## Resumen

Entender los tipos de datos en SQL es fundamental para el diseño de bases de datos y la integridad de los datos. Cada tipo de dato sirve a un propósito específico, desde almacenar datos numéricos y de cadena hasta manejar fechas y horas. Los tipos de datos personalizados mejoran aún más la flexibilidad y especificidad del manejo de datos en SQL.