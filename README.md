# Torazo 2026 🏔️

Guía visual del viaje familiar a la **Hostería de Torazo** (Cabranes, Asturias), del **5 al 9 de julio de 2026**. Para Sara, Laura y Papol.

## 🌐 Ver la guía

**https://nacho-marin.github.io/torazo-2026/**

Página pública, se abre en cualquier móvil sin necesidad de login. Es un resumen de lo que nos espera en el viaje: hotel, piscina y spa, comidas, rutas, previsión del tiempo y qué llevar en la maleta.

## Estructura

- **`index.html`** — la página de resumen (la que se ve en la URL de arriba).
- El plan completo día a día vive en un fichero aparte con URL propia (no enlazado desde el resumen, a propósito).

## Cómo editar

Los ficheros son HTML autocontenidos (CSS inline, sin dependencias externas). Para actualizar:

```bash
# editar el .html correspondiente
git add -A
git commit -m "docs: <qué cambió>"
git push
```

GitHub Pages reconstruye la web en ~1 min sobre la misma URL.
