# 📦 MPA | Apego al Planeamiento de Materiales

**Repositorio oficial del proyecto MPA (Apego al Planeamiento de Materiales)**, una solución desarrollada en **Power BI** para evaluar, monitorear y mejorar el cumplimiento semanal del abastecimiento de materiales frente al planeamiento logístico.

> Proyecto originalmente conocido como **MRA (Asertividad al Requerimiento de Materiales)**.

---

## 📊 Objetivo del Proyecto

El tablero de MPA tiene como finalidad cuantificar de forma visual, dinámica y accionable el grado de **apego entre lo planificado y lo realmente recibido** en planta por cada negocio, proveedor y código de material. 

Se busca con esto facilitar la toma de decisiones, identificar materiales críticos, evaluar la confiabilidad de los proveedores y prevenir paradas de producción por quiebre de stock.

<img width="1411" height="787" alt="Dashboard MPR " src="https://github.com/user-attachments/assets/4fbd0a3a-b22b-492c-ac9e-09401b5fad73" />


---

## 🧠 Contexto Operacional

- 🎯 **Área:** Demand & Supply Planning - Nestlé Perú  
- 🏭 **Negocios incluidos:** Helados, Cafés, Bebidas, Culinarios  
- 📆 **Frecuencia de actualización:** Semanal  
- 📍 **Fuente de datos:** SAP (ME2M, MB51), Excel externo (DPS)  
- ⚙️ **Tecnologías utilizadas:**  
  - Power BI Desktop  
  - Power Query (ETL)  
  - DAX (KPIs y lógica de cálculo)  
  - SAP GUI + VBA (extracción automatizada de datos)

---

## 🚀 KPIs Principales

| KPI | Descripción |
|-----|-------------|
| **MPA (%)** | % de monto recibido vs planificado, por semana |
| **Materiales con MPA < 90%** | Alerta de materiales con alto desvío |
| **Ranking de proveedores incumplidos** | Proveedores con menor apego al plan |
| **Monto en riesgo** | Valor monetario de materiales no entregados |
| **Cantidad de RC únicas** | Total de Recepciones Contables (RC) distintas por semana-negocio-proveedor-material |

---

## 🧩 Estructura del Tablero

1. **Selector de Semana / Mes (parámetro dinámico)**  
2. **Resumen ejecutivo (tarjetas con indicadores clave)**  
3. **Gráfico de tendencia del MPA**  
4. **Detalle de materiales críticos con bajo cumplimiento**  
5. **Vista de proveedor vs material**  
6. **Mapa de calor por día planificado**

---

## 📂 Estructura de Datos y Modelado

- **ME2M (Orden de Compra):** contiene las cantidades planificadas y precios unitarios.
- **MB51 (Movimientos de material):** contiene las cantidades recepcionadas en planta.
- **Cálculo de Monto Planificado y Recibido:**  
  `Monto = Cantidad * Precio unitario`
- **Ordenamiento de Meses personalizado:**  
  Para asegurar que enero vaya antes que diciembre, se creó una tabla auxiliar de ordenamiento.
- **Cálculo del estatus recibido:**  
  Se definió una lógica DAX:  
  - *Completo:* Recibido ≥ 90% del planificado  
  - *Faltante:* Recibido < 90% del planificado
- **RC únicas por semana-material:**  
  Se evitó la sobrecontabilización de RC por día usando combinaciones únicas `Sem-Neg-Prov-Mat`.

---

## 🤖 Automatizaciones

- 🔄 **Macro VBA** para extracción automática de reportes SAP `ME2M` y `MB51`.
- 📁 Archivos exportados directamente a carpeta local con estructura fija.
- 📈 **Actualización semiautomática** del Power BI al abrirlo, gracias a Power Query.

---

## 💡 Impacto del Proyecto

- ⏱️ Reducción de +70% del tiempo invertido en generación de reportes semanales.
- 📉 Detección temprana de materiales con riesgo de quiebre.
- 📢 Mejor comunicación entre compras, logística y producción.
- 🔍 Auditoría del comportamiento histórico de proveedores frente al cumplimiento del MPS/MRP.

---

## 🧠 Lecciones aprendidas

- Cómo manejar múltiples fuentes de datos SAP y armonizarlas.
- Buenas prácticas en modelado dimensional y relaciones en Power BI.
- Manejo de parámetros dinámicos para cambio de vista (Semana/Mes).
- Aplicación de reglas de negocio a nivel DAX para obtener métricas de valor.

---

## 🛠️ Requisitos Técnicos

- Power BI Desktop (versión 2023 en adelante)
- Acceso a SAP GUI y reportes ME2M / MB51
- Excel habilitado para macros (VBA)
- Carpeta local `C:\SAP_EXPORTS` para recibir archivos

---

## ✍️ Autor

📌 **Alessandro Cruzado Gutierrez**  
Supply Planning Trainee | Nestlé Perú  
Especialista en Power BI, Automatización de reportes SAP y Planeamiento de materiales.  
[LinkedIn](https://www.linkedin.com/in/alessandro-cruzado/)  

---

## ⭐ Créditos

Proyecto desarrollado en colaboración con múltiples áreas de Supply Chain:  
Planeamiento, Compras, Producción, MRP y Gestión de Proveedores.

---

## 📌 Nota final

Este dashboard ha sido una herramienta transformadora dentro del equipo de Supply Planning, marcando un antes y un después en cómo se analizan las desviaciones entre lo planificado y lo realmente abastecido en planta. Su uso continúa expandiéndose a nuevos negocios y operaciones.

---

