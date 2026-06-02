# HubSpot Deals Dashboard

Dashboard interactivo para analizar deals de HubSpot: ratios de conversión, salud del pipeline, cohortes, lead scoring e insights automáticos.

## 🚀 Cómo usarlo

### Opción 1 — Abrir directamente en el navegador
Descarga `index.html` y ábrelo en cualquier navegador moderno. No requiere servidor.

### Opción 2 — GitHub Pages (para compartir con el equipo)
1. Crea un repositorio público en GitHub (ej: `deals-dashboard`)
2. Sube `index.html` a la raíz del repo
3. Ve a **Settings → Pages → Source → main branch / root**
4. Tu dashboard estará en: `https://TU_USUARIO.github.io/deals-dashboard/`

## 📂 Cómo exportar el CSV desde HubSpot

1. Ve a **CRM → Deals**
2. Aplica los filtros que quieras (ej: año en curso)
3. Clic en **Export** (esquina superior derecha)
4. Selecciona **CSV** y descarga
5. Asegúrate de que el export incluye estas columnas:
   - `Deal Name`
   - `Deal Stage`
   - `New Platform`
   - `Close Date`
   - `Deal owner`
   - `Amount`
   - `Fuente`
   - `Lead Scoring (Sync)`
   - `SignUp Datetime`
   - `Create Date`

## 📸 Sistema de snapshots (comparación entre semanas)

1. Carga el CSV del lunes
2. Haz clic en **💾 Guardar snapshot**
3. La semana que viene, carga el nuevo CSV
4. La barra superior mostrará automáticamente la diferencia (▲▼ por ratio)

El snapshot se guarda en `localStorage` del navegador — persiste entre sesiones en el mismo navegador.

## 🔧 Actualizar el equipo (cuando hay cambios de personal)

Edita el objeto `TEAM_MAP` en `index.html` (línea ~350). El formato es:

```js
const TEAM_MAP = {
  "Nombre Apellido": { "team": "NombreEquipo", "leader": "Nombre del Leader" },
  // ...
};
```

## 📊 Páginas del dashboard

| Página | Contenido |
|--------|-----------|
| 📊 Resumen | KPIs globales, evolución semanal, foto fija |
| 👥 Equipos | Ratios por equipo + desglose por plataforma |
| 🛒 Plataformas | Comparativa de conversión por plataforma |
| 🙋 Owners | Tabla filtrable y ordenable por cualquier ratio |
| 🩺 Pipeline | Deals atascados, tiempo de cierre, salud por equipo |
| 📅 Cohortes | Análisis de madurez por mes de creación |
| 🎯 Scoring | Lead score vs ratios de conversión |
| 💡 Insights | Alertas y recomendaciones generadas automáticamente |

## ⚙️ Criterios de salud del pipeline

| Stage | 🟢 OK | 🟡 Vigilancia | 🔴 Crítico |
|-------|--------|---------------|------------|
| Pending Installation | < 30 días | 30–60 días | > 60 días |
| In Trial | < 21 días | > 21 días | — |
| Awaiting Payment | < 14 días | 14–30 días | > 30 días |

## 🔒 Privacidad

El dashboard funciona **100% en el navegador**. Los datos del CSV **no se envían a ningún servidor**. Todo el procesamiento ocurre localmente.

---

Construido con [Chart.js](https://chartjs.org) y [PapaParse](https://papaparse.com).
