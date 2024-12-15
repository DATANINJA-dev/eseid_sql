# Fundamentos de Bases de Datos - Primera Parte (Adaptado a eseidGambling)

## Duración Total

### Objetivos de Aprendizaje
Al final de esta sesión, los estudiantes podrán:
- Comprender el propósito de las bases de datos en un entorno empresarial como eseidGambling.
- Identificar los diferentes tipos de modelos de bases de datos y sus casos de uso.
- Diferenciar entre bases de datos SQL y NoSQL.
- Aplicar principios básicos de diseño de bases de datos y normalización.

---

## Contenido

### Introducción a Bases de Datos (30 minutos)
- **Definición y Propósito:** Explicar qué es una base de datos y su rol en la gestión de datos en empresas como eseidGambling.
- **Tipos de Usuarios:** Identificar roles clave como analistas de datos, administradores de bases de datos y desarrolladores.

### Modelos de Datos (30 minutos)
- **Modelo Relacional:** Características clave y su uso para almacenar transacciones y sesiones en eseidGambling.
- **Modelo de Documentos:** Uso para almacenar configuraciones dinámicas o datos de usuarios no estructurados.
- **Modelo Clave-Valor:** Ideal para almacenamiento rápido de información de sesiones.
- **Modelo de Grafos:** Representación de relaciones entre jugadores y campañas.

### SQL vs NoSQL (30 minutos)
- Comparar bases de datos SQL (ideal para transacciones) y NoSQL (útil para manejar datos de usuarios y patrones de comportamiento).

### Diseño de Bases de Datos y Normalización (30 minutos)
- Diseñar tablas optimizadas para almacenar campañas, sesiones y transacciones en eseidGambling.
- Aplicar normalización para prevenir redundancias y asegurar integridad de datos.

---

## Introducción a Bases de Datos

### ¿Qué es una Base de Datos?

Una base de datos es una colección estructurada de datos organizados para facilitar su acceso y gestión. En **eseidGambling**, las bases de datos se utilizan para almacenar:
- Información de usuarios.
- Detalles de campañas publicitarias.
- Transacciones realizadas por los jugadores.

**Prompt de ChatGPT:**  
*"¿Cómo puedo definir de manera sencilla qué es una base de datos y cuál es su propósito en una empresa como eseidGambling?"*  

**Respuesta de ChatGPT:**  
*"Una base de datos es un sistema estructurado que almacena información para facilitar su acceso y análisis. En eseidGambling, se utiliza para gestionar datos de usuarios, transacciones y campañas publicitarias, asegurando eficiencia y precisión."*

---

## Modelos de Datos

### Modelo Relacional
Se basa en tablas relacionadas que permiten almacenar y consultar datos con SQL. En eseidGambling, este modelo es ideal para manejar transacciones y sesiones.

**Ejemplo:** Tabla de Transacciones  
| transaction_id | user_id | gross_revenue | campaign_id |
|----------------|---------|---------------|-------------|

### Modelo Clave-Valor
Perfecto para almacenar datos simples como configuraciones de usuario o detalles de sesiones.

**Ejemplo:**  
```key-value
session_id: "abc123"
duration: "25 minutos"
```

**Prompt de ChatGPT:**  
*"¿Qué modelo de datos es más adecuado para almacenar configuraciones rápidas en eseidGambling?"*  

**Respuesta de ChatGPT:**  
*"El modelo clave-valor es ideal para almacenar configuraciones rápidas y ligeras, ya que permite accesos eficientes con un esquema flexible."*

---

## SQL vs NoSQL

### SQL en eseidGambling
Adecuado para transacciones que requieren alta consistencia y relaciones complejas entre tablas.

**Ejemplo:** Consultar ingresos totales por campaña.  
```sql
SELECT campaign_id, SUM(gross_revenue) AS total_revenue
FROM transactions
GROUP BY campaign_id;
```

### NoSQL en eseidGambling
Ideal para manejar grandes volúmenes de datos no estructurados, como datos de sesiones o preferencias de usuario.

**Prompt de ChatGPT:**  
*"¿Qué ventajas tiene NoSQL para almacenar datos de sesiones de jugadores en eseidGambling?"*  

**Respuesta de ChatGPT:**  
*"NoSQL es ideal porque permite escalabilidad horizontal, lo que facilita manejar grandes volúmenes de datos dinámicos como las sesiones de jugadores."*

---

## Diseño de Bases de Datos y Normalización

### Principios de Diseño
Al diseñar bases de datos para eseidGambling:
- Cada tabla debe representar una entidad específica (usuarios, transacciones, campañas).
- Las claves primarias y foráneas aseguran relaciones consistentes entre tablas.

**Ejemplo:** Relación entre Usuarios y Transacciones  
| user_id | nombre   | edad |
|---------|----------|------|  
| 1       | Alice    | 30   |  

| transaction_id | user_id | gross_revenue |
|----------------|---------|---------------|  
| 101            | 1       | 150.00        |  

### Normalización en eseidGambling
La normalización reduce redundancias y asegura integridad. Por ejemplo, separar datos de campañas en tablas relacionadas.

**Prompt de ChatGPT:**  
*"¿Cómo puedo diseñar una base de datos normalizada para campañas publicitarias?"*  

**Respuesta de ChatGPT:**  
*"Crea una tabla para las campañas con detalles básicos (ID, nombre, presupuesto) y otra para métricas (clics, conversiones), relacionándolas con claves foráneas."*

---

## Resumen

Este módulo cubre los fundamentos de las bases de datos en el contexto de eseidGambling, destacando cómo aprovechar modelos de datos, SQL, NoSQL y técnicas de normalización para gestionar datos de manera eficiente. Con **ChatGPT**, los estudiantes pueden aprender a formular consultas y diseñar bases de datos adaptadas a casos reales.
