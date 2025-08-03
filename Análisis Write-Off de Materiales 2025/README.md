# 📊 Dashboard de Riesgo de Vencimiento y Write-Off de Materiales 2025

**Autor**: Alessandro Cruzado Gutiérrez  
**Rol en el proyecto**: Desarrollador de Power BI y Analista de Supply Planning  
**Empresa**: Nestlé Perú  
**Duración**: 2025-Q3  
**Herramientas**: Power BI, DAX, Excel, SAP

---

## 🧠 Contexto del Problema

En operaciones industriales, los materiales críticos como insumos (ROH), semielaborados (HALB) y empaques (ZPCK) tienen una vida útil limitada. Si no se gestionan a tiempo, corren riesgo de vencimiento y se generan pérdidas financieras (Write-Offs).

Este dashboard responde a una necesidad urgente: **identificar, cuantificar y mitigar en tiempo real** el riesgo de vencimiento de materiales en el corto plazo, integrando múltiples fuentes de datos SAP y criterios de negocio.

---

## 🎯 Objetivo del Proyecto

> Diseñar e implementar un tablero de control que:
- Identifique materiales con vencimiento cercano (próximas 5 semanas).
- Calcule el monto total valorizado en riesgo de Write-Off.
- Detecte duplicidad de lotes para consolidación.
- Clasifique estatus de mitigación: `OK`, `Riesgo de WO`, etc.
- Visualice planes de acción aplicados por negocio y material.

---
<img width="1417" height="790" alt="Dashboard WO Corto Plazo" src="https://github.com/user-attachments/assets/eaefa39e-ef89-417d-9ddc-bcfd9b247e0d" />

## 🧩 Dataset y Modelo de Datos

| Campo                   | Descripción                                          |
|------------------------|------------------------------------------------------|
| `CP-Mat-Lot`           | Código único por combinación de corto plazo, material y lote |
| `Semana Vencimiento`   | Semana epidemiológica de expiración del material     |
| `Sem Actual`           | Semana actual del calendario                         |
| `Corto Plazo`          | Categoría (`Corto Plazo` u `Otro`) según vencimiento |
| `EstadoWO`             | Estado actual del lote (`OK`, `Riesgo de WO`, etc.)  |
| `Tipo Material`        | ROH / HALB / ZPCK                                    |
| `Valor Stock Lote`     | Monto en soles valorizado por cada lote              |

---

## 📈 Visualizaciones Clave

- **Tarjetas de KPIs**: 
  - Monto total a vencer en corto plazo
  - Cantidad de lotes únicos consolidados
  - Monto mitigado (`EstadoWO = OK`)

- **Segmentadores Dinámicos**:
  - Semana de vencimiento
  - EstadoWO
  - Tipo de material
  - Planta / Negocio

- **Tabla con Plan de Acción**: 
  - Visualiza cada lote, monto valorizado, estado, acción asignada y comentarios técnicos.

- **Gráficos de columnas**: 
  - Evolución semanal de montos valorizados en riesgo.

---

## 🔧 Lógica DAX Destacada

```DAX
Lotes_Únicos_Corto_Plazo = 
CALCULATE(
    DISTINCTCOUNT(BD_Vencimiento[CP-Mat-Lot]),
    BD_Vencimiento[Corto Plazo] = "Corto Plazo"
)

