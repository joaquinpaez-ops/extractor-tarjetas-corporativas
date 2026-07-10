# Extractor de resúmenes de tarjetas corporativas

Herramienta web 100% client-side para parsear PDFs de resúmenes de tarjetas corporativas y armar una planilla unificada lista para Excel.

**🔗 Abrir la app:** https://joaquinpaez-ops.github.io/extractor-tarjetas-corporativas/

## Bancos soportados

- **Visa BBVA Business**
- **Visa Galicia Business**
- **Visa Banco Provincia**
- **Amex Corporate Platinum**
- **Visa BNA (Corporativa Nación)**

Detecta el banco automáticamente al subir el PDF.

## Qué hace

- Drag & drop de uno o varios PDFs (acumulables).
- Extrae cada movimiento con: `Banco`, `Tarjeta`, `Titular`, `Fecha mov.`, `Cierre TC`, `Descripción`, `Moneda`, `ARS`, `USD`, `CC`, `Naturaleza`, `Concepto`, `Proveedor`.
- Clasifica cada consumo en el **Concepto** oficial del presupuesto (Publicidad, Viáticos, Combustible, Peajes, Licencias/Software, etc.) y deriva la **Naturaleza** (cuenta de P&L).
- **Reglas / Presupuesto**: cargá el plan/RFCST (`.xlsx`) como referencia buscable para pago a proveedores. La app matchea cada movimiento contra las reglas para imputar CC / Concepto / Naturaleza (regla de proveedor primero, CC del titular como fallback).
- Filtros multi-select dropdown por banco / tarjeta / titular / CC / naturaleza / concepto / proveedor / moneda.
- Checkbox de **subido** por fila + columna de nota (se guardan en `localStorage`).
- **Dashboard consolidado**: rollup jerárquico Naturaleza → Concepto (colapsable) + vista por centro de costo + estado de carga.
- Guardar / cargar la revisión completa como `.json`.
- Export a CSV, Excel y TSV (portapapeles).

## Privacidad

Todo corre en el navegador. Ni los PDFs ni el archivo de reglas (proveedores, CUITs, CC) se suben a ningún servidor — se procesan 100% client-side y el presupuesto queda solo en el `localStorage` de tu navegador. **No** se hornea en el código público.

## Stack

- HTML + Tailwind CSS (CDN) + JavaScript vanilla
- PDF.js 3.11 (CDN)
- Sin build step. Un solo archivo `index.html`.
