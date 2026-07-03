# CLAUDE.md — Torazo 2026

Proyecto personal (no UbiqWare): guía visual de un viaje familiar a la **Hostería de Torazo** (Cabranes, Asturias), **5–9 julio 2026**, con Sara (20 años, cumplió el 17 jun) y Laura (14, cumple 15 el 18 jul). Viaje en **coche propio**, ritmo tranquilo.

## Entregable

Dos páginas autocontenidas (CSS inline, fuentes nativas de Apple, sin dependencias externas ni CDN), servidas vía **GitHub Pages** (público, sin login — para que las hijas lo abran en el móvil):
- **`index.html`** = **el teaser** → <https://nacho-marin.github.io/torazo-2026/> — resumen sin spoilers para Sara y Laura. **No menciona Parque Principado** (es sorpresa: "desintoxicación rural"). Es lo que sirve la raíz, a propósito.
- **`plan-papol-torazo-idqyy4.html`** = **el plan completo** (para Papol) → URL con nombre poco adivinable, para que no se sirva por descuido al entrar en la raíz. Contiene el itinerario, restaurantes y la sorpresa (Parque Principado). No enlazar desde el teaser.

- El diseño es editorial-cálido: paleta verde musgo + óxido teja sobre papel cálido. Móvil-first.
- Ambas llevan meta `http-equiv` de no-cache para que un refresco del navegador baste. **Ojo**: eso NO controla el CDN de GitHub Pages (~10 min de `max-age`, no configurable en Pages). Para saltarse el CDN al verificar, añadir `?v=<timestamp>` a la URL.
- **Despliegue vía GitHub Actions** (`.github/workflows/pages.yml`), NO legacy. El modo `legacy` de Pages se rompió (fallos repetidos `Deployment failed, try again later`); migramos con `gh api -X PUT repos/.../pages -f build_type=workflow` + el workflow oficial. Verificar deploys por el **run de Actions** (`gh run view <id> --json status,conclusion`), no por el estado de `pages/builds` (puede quedar colgado en `errored`/`building`). GitHub tiene baches intermitentes en la fase de deploy aunque su status diga "operational"; reintentar (`gh workflow run pages.yml`) suele resolver. Límites (todos comprobables por API, ninguno fue el problema): Actions ilimitado en repo público, Pages ~10 builds/h, API 5000 req/h.
- Nombres: firmar/enumerar siempre como **"Sara, Laura y Papol"** (ver memoria [[papol-nombre-familiar]]).
- Para actualizar: editar → commit → `git push`. Pages reconstruye en ~1 min.

## Git

- Repo **individual**, trabajo directo sobre `main` (sin PRs).
- Remoto **SSH**: `git@github.com:nacho-marin/torazo-2026.git` (repo **público**).
- Identidad local del commit configurada en `.git/config` (no se anota aquí por norma).
- Conventional Commits. Sin trailers de co-autoría.

## Plan del viaje (reparto de días)

Reparto ajustado a la previsión meteorológica real (The Weather Channel, consultada 2026-07-02): dom 30°, **lun 31° (día más caluroso)**, mar 27° seco, mié 27°/20% lluvia, jue 27°/18%. Criterio del usuario: evitar ruta el día más caluroso (lunes → hotel); Parque Principado el miércoles.

| Día | Meteo | Plan |
|---|---|---|
| Dom 5 | 30° | Llegada + check-in + **comida en El Balcón** + **circuito termal Les Agües por la tarde** + (opcional) pueblo |
| Lun 6 | **31°** | **Día de hotel** (el más caluroso, sin ruta): piscina exterior + **comida en El Balcón** (hotel; Los Llaureles cerrado hasta 17 jul) + Torazo pueblo + relax + **⚽ España–Portugal 21:00** (octavos; España clasificada) |
| Mar 7 | 27° seco | **Camín Encantáu** (Ardisana, Llanes) — la ruta estrella, jornada completa (~1 h 15–30 de coche, ~9 km circular) |
| Mié 8 | 27° / 20% | **Parte del Río Profundu de mañana** (Villaviciosa, ~20 min; se da la vuelta antes) + comida sidrería + **Parque Principado por la tarde**. La versión completa (la de 2020: ida por senda del río hasta Buslaz, vuelta por carretera) son ~19 km / media / 4h40 — queda como opción si se hace la jornada entera (sin Parque ese día). |
| Jue 9 | 27° | Check-out + **ruta Misterios del Mar** (Colunga, de camino a casa) + vuelta |

**Tres rutas efectivas** (las nenas las quieren las tres): Camín Encantáu (mar), Río Profundu (mié mañana), **Misterios del Mar** (jue, de camino a casa tras el check-out). Misterios del Mar = Colunga, PR-AS 196, circular ~5,9 km, fácil, ~25-30 min, costera (acantilados, Sierra del Sueve, Lastres, playa de La Isla). Nota: discrepancia de desnivel entre fuentes (30 m FEMPA vs 183 m Turismo Colunga), sin reconciliar → no se pone cifra de desnivel. (Bimenes quedó descartada.)

**Dónde cenar** (noches fuera del hotel): sidrerías de Villaviciosa (~20 min). Seguras para cena: **Bedriñana** (985 89 11 52) y **El Roxu** (984 83 31 97, cierra dom noche y lunes). Confirmar por tel.: El Gallineru (984 06 73 69), Sidrería Plaza / Nava (984 84 25 71).
**Descartado esta vez**: Picos de Europa / Lagos de Covadonga (en julio el bus lanzadera es obligatorio, 1 jun–18 oct).

## Datos verificados (fuentes reales)

- **Hostería de Torazo** 4★ · Plaza de la Sienra 1, 33310 Torazo (Cabranes) · **985 89 80 99** · reservas@hosteriadetorazo.com · hosteriadetorazo.com. Restaurante propio "El Balcón de Torazo" (4 tenedores). Circuito termal **Les Agües** (90 min): hidroterapia + sauna + hammam + zona relax. Piscina exterior confirmada. Acceso spa: gorro + chanclas obligatorios.
- **Torazo**: Pueblo Ejemplar de Asturias **2008** (no 2007). Iglesia de **San Martín** (1685). Grafía asturiana oficial: "Torazu".
- **Rutas** (ver detalle en `index.html`): Bimenes ~7 km circular; Río Profundu lineal (dar la vuelta a gusto); Camín Encantáu ~9 km circular con tallas mitológicas.
- **Clima julio**: ~22 °C máx, mes seco pero con orbayu. Maleta: trekking + chubasquero ligero + bañador/gorro/chanclas.

## ⚠️ Pendiente de reconfirmar antes del viaje

- **LLAMAR al 985 89 80 99**: reservar sesión de spa; confirmar si hay piscina interior climatizada con chorros *aparte* del circuito de hidroterapia (la "piscina interior con chorros" que se recordaba es, casi seguro, la piscina de hidroterapia del spa); horarios reales de piscina/spa.
- Reconfirmar **tiempos de coche en Google Maps** la víspera (los del plan son estimaciones).
- Comprobar previsión de **orbayu** por si toca activar el Plan B (Parque Principado).
