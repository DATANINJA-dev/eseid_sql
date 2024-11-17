# Sesiones y Desarrollo

---

## **Introducción al Caso Real y Uso de ChatGPT**

- **Contexto del Curso:**  
  El curso se basa en una entrevista técnica con una empresa de gambling, explicando cómo utiliza datos de sesiones de usuarios, costos de campañas publicitarias y transacciones para tomar decisiones estratégicas.

- **Entrevista Técnica:**  
  - ¿Cómo mide la empresa la efectividad de sus campañas?  
  - ¿Qué datos son más relevantes para las decisiones de negocio?

- **ChatGPT:**  
  Los estudiantes aprenderán a usar **prompting** para optimizar sus consultas SQL y resolver problemas comunes planteados en la entrevista.

---

## **Session I - Fundamentos de Bases de Datos**

- **Contexto del Caso:**  
  La empresa utiliza bases de datos relacionales para almacenar datos de marketing y transacciones.

- **Entrevista Técnica:**  
  ¿Qué tecnologías de bases de datos están en uso y cómo estructuran sus datos de manera eficiente?

- **Aplicación:**  
  Explicación de cómo se organizan los datos en tablas que contienen información sobre sesiones, campañas y resultados de ventas.

---

## **Session II - SQL I: Consultas Básicas**

- **Consultas SELECT y WHERE:**  
  Introducción a consultas básicas para extraer datos relevantes del negocio.

  - **Entrevista Técnica:**  
    ¿Qué preguntas comerciales típicas responden con SQL? Ejemplo: extracción de datos de sesiones y costos de campañas.

  - **Aplicación:**  
    Recuperar datos de sesiones y filtrar campañas específicas utilizando `SELECT` y `WHERE`.

- **ORDER BY y LIMIT:**  
  Ordenar y limitar los resultados para identificar las campañas más efectivas.

  - **Aplicación:**  
    Filtrar y priorizar campañas con mejor retorno de inversión en reportes.

- **INSERT, UPDATE, DELETE:**  
  Manejo práctico de cómo actualizar o eliminar datos de campañas en la base de datos.

  - **Aplicación:**  
    Inserción de nuevas campañas, actualización de costos y eliminación de datos obsoletos.

---

## **Session III - SQL II: Consultas Intermedias**

- **JOIN:**  
  Combinar tablas que incluyen datos de sesiones, costos y transacciones.

  - **Entrevista Técnica:**  
    ¿Cómo combina la empresa datos de múltiples fuentes para obtener una visión completa del rendimiento de las campañas?

  - **Aplicación:**  
    Construir consultas que unan información de campañas publicitarias, costos y resultados de ventas.

- **KPIs del Business Case:**  
  - **Cost per Session (CPS):** Calcular el costo por sesión de usuario.  
  - **Revenue:** Relacionar costos de campañas con ingresos generados.  
  - **ROAS:** Medir el retorno de la inversión publicitaria.

- **GROUP BY y HAVING:**  
  Agrupar datos por país o campaña y filtrar resultados agregados.

  - **Aplicación:**  
    Calcular costos totales de campañas por país o por mes, aplicando filtros según criterios comerciales clave.

---

## **Session IV - Tipos de Schemas y Data Warehousing**

- **Diseño de Esquemas:**  
  Explicación sobre cómo estructurar un almacén de datos utilizando un **star schema**.

  - **Entrevista Técnica:**  
    ¿Cómo estructuran los datos para análisis de gran escala y qué tipo de reporting utilizan?

  - **Aplicación:**  
    Diseñar un esquema estrella que facilite el análisis de campañas y ventas.

---

## **Session V - SQL III: Técnicas Avanzadas**

- **Funciones Avanzadas:**  
  Uso de funciones como `ROW_NUMBER` o `RANK` para crear rankings de campañas más eficientes.

  - **Aplicación:**  
    Ranking de campañas basado en el retorno de inversión publicitaria o costos por sesión.

- **Window Functions:**  
  Cálculos avanzados para análisis temporales, como la evaluación de la efectividad de campañas a lo largo del tiempo.

  - **Entrevista Técnica:**  
    ¿Cómo analiza la empresa las tendencias temporales en el rendimiento de sus campañas?

  - **Aplicación:**  
    Crear consultas para evaluar las campañas más exitosas mes a mes.

- **Optimización de Consultas:**  
  Implementar mejores prácticas para optimizar el rendimiento de consultas SQL mediante índices y particionamiento de datos.

  - **Aplicación:**  
    Garantizar que las consultas sobre grandes volúmenes de datos sean eficientes.
