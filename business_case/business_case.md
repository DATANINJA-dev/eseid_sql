
# Business Case: Redefiniendo Estrategias de Marketing en esidGambling

## Introducción

Imagina que eres parte del equipo de análisis de datos en **esidGambling**, una plataforma global que conecta a jugadores con experiencias de juego únicas. En los últimos meses, el equipo directivo ha identificado una caída en el retorno de las campañas publicitarias en ciertos mercados clave. Además, se ha notado que los costos de las campañas han aumentado, mientras que el volumen de sesiones y las conversiones no están creciendo al mismo ritmo.

Tu misión es clara: analizar los datos disponibles, identificar áreas de mejora y proponer acciones basadas en los resultados.

---

## Escenario

### Contexto del Negocio

La empresa ha lanzado una serie de campañas en mercados clave para aumentar las sesiones en la plataforma. Estas campañas utilizan múltiples fuentes y medios publicitarios, con presupuestos significativos asignados. Sin embargo, los resultados no están cumpliendo las expectativas:

1. **Crecen los costos:** Los costos de campañas han aumentado significativamente.
2. **Estancamiento en sesiones:** El volumen de sesiones no se correlaciona con el aumento en los costos.
3. **Bajo ROI:** Algunas campañas no están generando ingresos suficientes para justificar su costo.

Los datos disponibles están organizados en las siguientes tablas:

### Tablas

1. **`purchase`:** Registra todas las transacciones realizadas en la plataforma.
   - `market_id`: Identificador del mercado.
   - `date_`: Fecha de la transacción.
   - `utm_source`: Fuente de la campaña.
   - `utm_medium`: Medio de la campaña.
   - `gross_revenue`: Ingreso bruto generado.

2. **`costs`:** Detalla los costos asociados a cada campaña publicitaria.
   - `market_id`: Identificador del mercado.
   - `date_`: Fecha del costo.
   - `utm_source`: Fuente de la campaña.
   - `utm_medium`: Medio de la campaña.
   - `cost_campaign`: Costo asociado.

3. **`sessions`:** Registra las sesiones generadas en la plataforma.
   - `market_id`: Identificador del mercado.
   - `date_`: Fecha de la sesión.
   - `utm_source_medium`: Fuente y medio combinados.
   - `sessions`: Número de sesiones generadas.

---

## Tu Reto

Usando las tablas disponibles, responde las siguientes preguntas clave:

### **1. Análisis de Eficiencia de Campañas**
- **Pregunta:** ¿Cuáles son las campañas con mayor costo por sesión (CPS) en cada mercado? ¿Qué campañas muestran la mejor eficiencia?
- **Pista:** Utiliza las tablas `sessions` y `costs` para calcular el CPS.

### **2. Análisis de Retorno de la Inversión Publicitaria (ROAS)**
- **Pregunta:** ¿Qué mercados y fuentes están generando el mejor y peor ROAS?
- **Pista:** Combina las tablas `purchase` y `costs` para calcular el ROAS (ingresos generados dividido por costos).

### **3. Identificación de Patrones Estacionales**
- **Pregunta:** ¿Qué meses muestran los mayores ingresos en cada mercado? ¿Hay patrones de estacionalidad que puedas identificar?
- **Pista:** Agrupa los datos de la tabla `purchase` por mes y mercado.

### **4. Sesiones y Conversión**
- **Pregunta:** ¿Qué relación existe entre las sesiones generadas y los ingresos obtenidos por mercado y fuente?
- **Pista:** Combina las tablas `sessions` y `purchase` para analizar esta relación.

### **5. Ranking de Fuentes por Ingresos**
- **Pregunta:** ¿Qué fuentes están generando los mayores ingresos en cada mercado?
- **Pista:** Usa funciones de clasificación como `RANK()` o `DENSE_RANK()` para crear un ranking por mercado.

---

## Entregables

Como analista, debes preparar los siguientes entregables:

1. **Reporte de Análisis:** Un informe que resuma tus hallazgos, incluidas las campañas menos eficientes, las fuentes más rentables y los patrones estacionales.
2. **Acciones Propuestas:** Propuestas basadas en los resultados del análisis. Ejemplo: ¿Deberían ajustarse los presupuestos para las fuentes más eficientes?
3. **Consultas SQL:** Asegúrate de incluir todas las consultas SQL utilizadas para responder las preguntas clave.

---

## Conclusión

Este Business Case te permite aplicar los conceptos aprendidos en clase en un escenario realista. A través del análisis de datos, no solo mejorarás tu habilidad técnica con SQL, sino que también desarrollarás una perspectiva estratégica para resolver problemas empresariales complejos.
