<!-- # Declaración CASE en SQL -->

## Introducción

La declaración CASE en SQL es una expresión condicional, similar a las declaraciones if/else en los lenguajes de programación. Permite realizar consultas basadas en condiciones, haciendo que las consultas SQL sean más dinámicas y versátiles.

## Explicación Conceptual

La declaración CASE proporciona una forma de realizar lógica condicional directamente dentro de una consulta SQL. Evalúa condiciones y devuelve un valor cuando se cumple la primera condición. Si no se cumplen condiciones, puede devolver un valor predeterminado (especificado en la cláusula ELSE).

## Sintaxis y Uso

Hay dos formas de la expresión CASE en SQL:

1. **Expresión CASE simple**:
   ```sql
   CASE expression
   WHEN value THEN result
   [WHEN ...]
   [ELSE result]
   END

   ```

2. **Expression CASE**:
   ```sql
   CASE WHEN condition THEN result
   [WHEN ...]
   [ELSE result]
   END
   ```

## Ejemplo Práctico

Considera la siguiente consulta SQL utilizando una declaración CASE:

```sql
SELECT *,
CASE WHEN age < 30 THEN 'Young'
     WHEN age > 60 THEN 'Senior Citizen'
     ELSE 'Middle aged'
END AS Age_category
FROM customer;
```

En este ejemplo, la consulta clasifica a los clientes en categorías según su edad. La declaración CASE asigna una etiqueta a cada grupo de edad.

## Resumen

La declaración CASE en SQL es una herramienta poderosa para introducir lógica condicional en las consultas SQL. Mejora la flexibilidad de la recuperación de datos al permitir diferentes salidas basadas en condiciones específicas.
