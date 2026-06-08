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
- Extrae cada movimiento con: `Banco`, `Tarjeta`, `Extensión` (titular del adicional), `Fecha mov.`, `Cierre TC`, `Descripción`, `Moneda`, `ARS`, `USD`, `Proveedor`, `Concepto`.
- Clasificador heurístico de proveedor/concepto (Google Ads, Meta Ads, Adobe, Canva, Uber, Mercado Pago, PedidosYa, ARBA, IVA, RG 5617, peajes, etc.).
- Filtros multi-select dropdown por banco / tarjeta / extensión / proveedor / concepto / moneda — afectan tabla y dashboard.
- Checkbox de **subido** por fila + columna de nota (se guardan en `localStorage` del navegador).
- Dashboard con vistas agrupadas (por banco, proveedor, extensión, concepto) y % de avance de carga (por cantidad y por saldo).
- Click en checkbox de un grupo del dashboard → marca todos los movimientos de ese proveedor/extensión/etc.
- Export a CSV, Excel y TSV (portapapeles).

## Privacidad

Todo corre en el navegador. Los PDFs no se suben a ningún servidor — el parseo es 100% client-side con PDF.js.

## Stack

- HTML + Tailwind CSS (CDN) + JavaScript vanilla
- PDF.js 3.11 (CDN)
- Sin build step. Un solo archivo `index.html`.
