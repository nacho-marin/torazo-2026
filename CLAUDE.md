# CLAUDE.md — Torazo 2026

Proyecto personal (no UbiqWare): guía visual de un viaje familiar a la **Hostería de Torazo** (Cabranes, Asturias), **5–9 julio 2026**, con Sara (20 años, cumplió el 17 jun) y Laura (14, cumple 15 el 18 jul). Viaje en **coche propio**, ritmo tranquilo.

## Entregable

Dos páginas autocontenidas (CSS inline, fuentes nativas de Apple, sin dependencias externas ni CDN), servidas vía **GitHub Pages** (público, sin login — para que las hijas lo abran en el móvil):
- **`index.html`** = **el plan completo** → <https://nacho-marin.github.io/torazo-2026/> (la raíz, con todos los detalles; el usuario invirtió la disposición el 2026-07-04).
- **`teaser.html`** = **el teaser** → <https://nacho-marin.github.io/torazo-2026/teaser.html> — resumen sin spoilers para Sara y Laura (no menciona Parque Principado: "desintoxicación rural" sorpresa).

- El diseño es editorial-cálido: paleta verde musgo + óxido teja sobre papel cálido. Móvil-first.
- Ambas llevan meta `http-equiv` de no-cache para que un refresco del navegador baste. **Ojo**: eso NO controla el CDN de GitHub Pages (~10 min de `max-age`, no configurable en Pages). Para saltarse el CDN al verificar, añadir `?v=<timestamp>` a la URL.
- **Despliegue vía GitHub Actions** (`.github/workflows/pages.yml`), NO legacy. El modo `legacy` de Pages se rompió (fallos repetidos `Deployment failed, try again later`); migramos con `gh api -X PUT repos/.../pages -f build_type=workflow` + el workflow oficial. Verificar deploys por el **run de Actions** (`gh run view <id> --json status,conclusion`), no por el estado de `pages/builds` (puede quedar colgado en `errored`/`building`). GitHub tiene baches intermitentes en la fase de deploy aunque su status diga "operational"; reintentar (`gh workflow run pages.yml`) suele resolver. Límites (todos comprobables por API, ninguno fue el problema): Actions ilimitado en repo público, Pages ~10 builds/h, API 5000 req/h.
- **Fuente única de datos (anti copy-paste)**: los datos repetidos (temperaturas, lluvia, iconos, tiempos de coche, hora del partido) viven SOLO en el objeto `DATA` al inicio del `<script>` de `index.html`. Los textos i18n los referencian con tokens `{{tmax.lun}}`; el HTML crudo (celdas de tablas, chips) usa `data-wx="tmax.dom"` (meteo, con formato) o `data-val="drive.rio"` (verbatim). Para cambiar la previsión o un tiempo de coche, editar únicamente `DATA`. Ojo al hacer replaces globales: no tocar los valores dentro del propio `DATA` (bug ya sufrido).
- Nombres: firmar/enumerar siempre como **"Sara, Laura y Papol"** (ver memoria [[papol-nombre-familiar]]).
- Para actualizar: editar → commit → `git push`. Pages reconstruye en ~1 min.

## Git

- Repo **individual**, trabajo directo sobre `main` (sin PRs).
- Remoto **SSH**: `git@github.com:nacho-marin/torazo-2026.git` (repo **público**).
- Identidad local del commit configurada en `.git/config` (no se anota aquí por norma).
- Conventional Commits. Sin trailers de co-autoría.

## Plan del viaje (reparto de días)

Previsión (The Weather Channel, actualizada 2026-07-04): dom 30°/6%, **lun 33° (día más caluroso)**, mar 27°/4%, mié 26°/19%, jue 26°/18%. Criterio: evitar ruta el día más caluroso (lunes → hotel); Parque Principado el miércoles. **Los valores canónicos viven en el objeto `DATA` de `index.html`** — esta tabla es orientativa.

| Día | Meteo | Plan |
|---|---|---|
| Dom 5 | 31° real | ✅ Check-in 14:00 + comidón en El Balcón + piscina 16:00 + spa Les Agües 19:30 + cena 22:00 (**Nature Menu**) |
| Lun 6 | **36° real** | ✅ Día de hotel: piscina mañana y tarde + ⚽ **España 1-0 Portugal** (Mikel Merino, min 90). El pueblo se movió al martes |
| Mar 7 | 27°→20° ⛈️ | 🔁 **Camín Encantáu CANCELADO** (coche largo + calor; tormenta desde 14:30 lo confirmó). ✅ Piscina mañana + pueblo + **masajes** (Sara: Ritual Nature Completo; Laura: Espalda y Piernas Relax) + Argentina 3-2 Egipto + cena hotel |
| Mié 8 | 26°/19% | **Río Profundu** (corta ~1,5-2 h o larga 19 km/4h40; con la larga también da tiempo a Parque) + sidrería (~5 min del parking) + **Parque Principado**: cine (Spider-Man BND / Supergirl / Toy Story 5) + cena McDonald's + **recado: ventilador/cooler en MediaMarkt** |
| Jue 9 | 26°/18% | Check-out + **Misterios del Mar** (Colunga, de camino) + vuelta a **Gijón (nuestra casa)** + **visita a la Abuelita Enedina (95 años)** por la tarde |

**Tres rutas efectivas** (las nenas las quieren las tres): Camín Encantáu (mar), Río Profundu (mié mañana), **Misterios del Mar** (jue, de camino a casa tras el check-out). Misterios del Mar = Colunga, PR-AS 196, circular ~5,9 km, fácil, ~25-30 min, costera (acantilados, Sierra del Sueve, Lastres, playa de La Isla). Nota: discrepancia de desnivel entre fuentes (30 m FEMPA vs 183 m Turismo Colunga), sin reconciliar → no se pone cifra de desnivel. (Bimenes quedó descartada.)

**Dónde cenar** (noches fuera del hotel): sidrerías de Villaviciosa (~20 min). Seguras para cena: **Bedriñana** (985 89 11 52) y **El Roxu** (984 83 31 97, cierra dom noche y lunes). Confirmar por tel.: El Gallineru (984 06 73 69), Sidrería Plaza / Nava (984 84 25 71).
**Descartado esta vez**: Picos de Europa / Lagos de Covadonga (en julio el bus lanzadera es obligatorio, 1 jun–18 oct).

## Datos verificados (fuentes reales)

- **Hostería de Torazo** 4★ · Plaza de la Sienra 1, 33310 Torazo (Cabranes) · **985 89 80 99** · reservas@hosteriadetorazo.com · hosteriadetorazo.com. Restaurante propio "El Balcón de Torazo" (4 tenedores). Circuito termal **Les Agües** (90 min): hidroterapia + sauna + hammam + zona relax. Piscina exterior confirmada. Acceso spa: gorro + chanclas obligatorios.
- **Torazo**: Pueblo Ejemplar de Asturias **2008** (no 2007). Iglesia de **San Martín** (1685). Grafía asturiana oficial: "Torazu".
- **Rutas** (detalle en `index.html`): Camín Encantáu ~9 km circular (tallas mitológicas); Río Profundu lineal, vuelta a gusto (larga: hasta Buslaz + carretera, 19 km/4h40); Misterios del Mar ~5,9 km circular costera. **Avituallamiento**: Panadería de Torazo y Casa Suárez (a pie), Alimerka Infiesto (~17 min), Mercadona Villaviciosa (~19 min). **Family Room** (por confirmar cuál).
- **Clima julio**: ~22 °C máx, mes seco pero con orbayu. Maleta: trekking + chubasquero ligero + bañador/gorro/chanclas.

## ⚠️ Pendiente de reconfirmar antes del viaje

- **LLAMAR al 985 89 80 99**: reservar circuito spa (dom tarde) + **masaje del martes** + preguntar horarios. (La piscina interior con chorros YA está confirmada como parte del circuito.)
- Reconfirmar **tiempos de coche en Google Maps** la víspera (los del plan son estimaciones).
- **Seguimiento en vivo**: desde el 5 de julio, Nacho irá contando novedades para marcar hecho vs. planificado en la web.
