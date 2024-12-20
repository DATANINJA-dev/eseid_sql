
# Soluciones y Conclusiones del Business Case: esidGambling

## Introducción

Este documento contiene las soluciones al Business Case planteado para **esidGambling**. Incluye consultas SQL prácticas que los estudiantes pueden ejecutar para resolver problemas clave, así como conclusiones que reflejan insights obtenidos a partir de los datos.

---

## Soluciones

### **1. Análisis de Eficiencia de Campañas (CPS)**

**Consulta SQL:**
```sql
SELECT 
  s.market_id, 
  c.utm_source, 
  SUM(c.cost_campaign) / SUM(s.sessions) AS cps
FROM sessions s
JOIN costs c 
  ON s.market_id = c.market_id AND s.date_ = c.date_
GROUP BY s.market_id, c.utm_source;
```

**Explicación:**  
- Esta consulta calcula el **Costo por Sesión (CPS)** al dividir los costos de campaña entre las sesiones generadas.
- Las campañas con **CPS altos** son menos eficientes y necesitan optimización.

---

### **2. Análisis del ROAS (Retorno de la Inversión Publicitaria)**

**Consulta SQL:**
```sql
SELECT 
  p.market_id, 
  p.utm_source, 
  SUM(p.gross_revenue) / SUM(c.cost_campaign) AS roas
FROM purchase p
JOIN costs c 
  ON p.market_id = c.market_id AND p.date_ = c.date_ AND p.utm_source = c.utm_source
GROUP BY p.market_id, p.utm_source;
```

**Explicación:**  
- Este cálculo del **ROAS** divide los ingresos totales por los costos de campaña.
- Fuentes con un **ROAS bajo** no están justificando su inversión.

---

### **3. Identificación de Patrones Estacionales**

**Consulta SQL:**
```sql
SELECT 
  market_id, 
  DATE_TRUNC('month', date_) AS month, 
  SUM(gross_revenue) AS total_revenue
FROM purchase
GROUP BY market_id, DATE_TRUNC('month', date_);
```

**Explicación:**  
- Se agrupan los ingresos por **mes** y **mercado**.
- Esta consulta detecta patrones estacionales para identificar meses con mayor actividad.

---

### **4. Sesiones y Conversión**

**Consulta SQL:**
```sql
SELECT 
  s.market_id, 
  s.utm_source_medium, 
  SUM(s.sessions) AS total_sessions, 
  SUM(p.gross_revenue) AS total_revenue,
  SUM(p.gross_revenue) / SUM(s.sessions) AS conversion_rate
FROM sessions s
JOIN purchase p 
  ON s.market_id = p.market_id AND s.date_ = p.date_
GROUP BY s.market_id, s.utm_source_medium;
```

**Explicación:**  
- La consulta examina la relación entre sesiones y conversiones (ingresos) por fuente.
- Proporciona la **tasa de conversión**, útil para priorizar las fuentes más efectivas.

---

### **5. Ranking de Fuentes por Ingresos**

**Consulta SQL:**
```sql
SELECT 
  market_id, 
  utm_source, 
  SUM(gross_revenue) AS total_revenue,
  RANK() OVER (PARTITION BY market_id ORDER BY SUM(gross_revenue) DESC) AS revenue_rank
FROM purchase
GROUP BY market_id, utm_source;
```

**Explicación:**  
- Clasifica las **fuentes** en cada mercado por ingresos generados.
- Ayuda a priorizar fuentes que contribuyen más al éxito financiero.

---

## Conclusiones

1. **Eficiencia de Campañas (CPS):**  
   - Campañas con un CPS alto deben ser optimizadas o eliminadas.
   - Las fuentes con bajo CPS son prioritarias para inversión.

2. **ROAS:**  
   - Las campañas con un ROAS superior a 1 son rentables.  
   - Fuentes con ROAS bajo necesitan análisis para ajustar su enfoque.

3. **Patrones Estacionales:**  
   - Se identifican meses de alta actividad que justifican incrementos en presupuesto.  
   - Meses de baja actividad requieren campañas específicas para atraer tráfico.

4. **Tasa de Conversión:**  
   - Fuentes con altas tasas de conversión deben recibir mayor atención.  
   - Las fuentes con baja conversión necesitan análisis para mejorar.

5. **Ranking de Fuentes:**  
   - El ranking de ingresos ayuda a priorizar fuentes y mercados clave.  
   - Proporciona una guía clara para asignación de recursos.

---

## Próximos Pasos

- **Ejecuta las consultas SQL:** Usa los datos de las tablas para comprobar los resultados.  
- **Analiza tus hallazgos:** Identifica patrones e insights adicionales.  
- **Propón mejoras:** Usa tus conclusiones para plantear estrategias que maximicen el impacto de las campañas.

---

## Recursos

- [Documentación SQL](https://www.w3schools.com/sql/)
- [Guía de Data Analytics](https://towardsdatascience.com/)

¡Ahora es tu turno de analizar y optimizar las estrategias de marketing en esidGambling!
