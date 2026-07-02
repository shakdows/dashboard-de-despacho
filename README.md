# 📦 Control de Despachos · Dashboard Operativo

Dashboard analítico de **despachos a provincia** — 100 % client-side
(HTML + CSS + JavaScript vanilla + Chart.js 4.4.1 vía CDN). Un solo archivo,
sin build step, listo para **GitHub Pages** y **Vercel**.

<p align="center">
  <img src="logo-shakdows.png" width="120" alt="Grima · Shakdows">
</p>

> Creado por **Alexis Ramírez** · alias **Shakdows** — la historia del sigilo
> de los seis ojos está en [GRIMA.md](GRIMA.md).

---

## 🗂️ Estructura

```
index.html                → dashboard completo (datos + logos embebidos, ~230 KB)
logo-shakdows.png         → sigilo Grima oscuro 256 px (extra, no requerido)
logo-shakdows-white.png   → sigilo Grima blanco 256 px (extra, no requerido)
GRIMA.md                  → la leyenda de Grima y el origen de Shakdows
vercel.json               → configuración de sitio estático
README.md                 → este archivo
```

El dashboard **no depende** de los PNG sueltos: los logos van embebidos como
data URI dentro de `index.html`.

## 📊 Los datos

- Fuente: `CONTROL_DE_DESPACHO.xlsx` (hoja 2026) + `CONTROL_DE_RUTAS.xlsx`
- Período: **18 – 30 de junio de 2026**
- 226 despachos · 376 bultos · 41 destinos · 37 transportistas (normalizados)
- 29 viajes de despacho a provincia (vehículos CKR-900, BHX-742, CKU-731)

Los datos están embebidos en `index.html` (constante `DATA`). Para actualizar
el período, se regenera el archivo con el nuevo Excel.

## 🖥️ Funcionalidades

- 8 tarjetas KPI + panel de **hallazgos clave** en lenguaje simple
- 7 gráficos interactivos (evolución diaria, estado, destinos,
  transportistas, día de semana, bultos, tiempos por vehículo)
- Filtros por fecha, destino, transportista y estado
- Toggle de métrica **Despachos ↔ Bultos**
- Tabla de detalle con buscador
- **Acceso por token mensual** (ver abajo)

## 🔑 Acceso por token mensual

Al abrir el dashboard aparece una pantalla de acceso. Cada token vale solo
durante su mes y **vence automáticamente**; la sesión se guarda en
`localStorage` (`despachos_dashboard_token`).

Los tokens de 2026 están definidos en `index.html`, en la constante
`VALID_TOKENS` (final del script). Para el año siguiente basta agregar
12 filas nuevas con sus fechas `expiry`.

> ⚠️ **Nota de seguridad:** es un candado del lado del cliente — controla el
> acceso mensual de usuarios normales, pero los tokens son visibles en el
> código fuente. Para acceso realmente seguro se requiere validación en
> backend (p. ej. Supabase).

## 🚀 Despliegue

**Vercel** (recomendado)
1. Sube este repo a GitHub.
2. En Vercel: *Add New → Project → Import* el repo.
3. Framework preset: **Other** (sitio estático, sin build). Deploy.

**GitHub Pages**
1. Repo → *Settings → Pages*.
2. Source: rama `main`, carpeta `/ (root)`. Guardar.
3. La URL queda como `https://<usuario>.github.io/<repo>/`.

---

© 2026 **Alexis Ramírez (Shakdows)**. Diseño y desarrollo originales.
