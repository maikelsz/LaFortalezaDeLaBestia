# La Fortaleza

Reconstrucción web de **La Fortaleza**, la aventura conversacional en Pascal escrita por Miguel Enrique Cepero (Merchise Software) en la década de 1990 para DOS.

El jugador es un hombre común enviado a matar a "la Bestia" dentro de una fortaleza. Deberá explorar 50 habitaciones, resolver acertijos, enfrentarse a criaturas y destruir los cuatro Centros de la Bestia antes de poder vencerla.

---

## 🎮 Jugar

Abre `Fortaleza_I.html` en cualquier navegador moderno. No requiere servidor, instalación ni conexión a internet.

O en este vinculo: <https://maikelsz.github.io/LaFortalezaDeLaBestia/Fortaleza_I.html>

Todo el juego —datos, lógica, estilos y gráficos SVG— vive en **un único archivo HTML**.

---

## ✨ Características

- **50 habitaciones** y **~90 objetos** fielmente reconstruidos del original en Pascal.
- **Parser en español** con sinónimos (`ir`/`atravesar`/`cruzar`, `coger`/`tomar`, `matar`/`asesinar`, etc.).
- **Sistema de comandos armados**: los botones de acción (`mirar`, `ir`, `coger`…) están bajo la descripción de la sala; pulsa uno, haz clic en los objetos, y el comando se compone y ejecuta solo.
- **Puertas con estado compartido**: si abres una puerta y cruzas, en la habitación de enfrente ya aparece abierta.
- **Sprites SVG detallados** para objetos clave (roble, maza, pastel, pared, órganos, túnel, pozo, Atenea, Hermes, balanza).
- **Sombras de contacto** difusas bajo los objetos apoyados en el suelo (incluidos los que deja el jugador), escaladas con cada sprite.
- **Tooltips al pasar el ratón** sobre objetos en la escena SVG.
- **Guardado y carga** en `localStorage` con confirmación diegética.
- **Mapa opcional** con advertencia previa (el juego original recomendaba dibujarlo a mano).
- **Inventario**: un objeto por fila, icono SVG a doble tamaño, tooltip al pasar el ratón, descripción al hacer clic y barra de peso.
- **Objetos dejados en el suelo**: apoyan sobre la línea del suelo de cada sala, proyectan sombra de contacto y no se solapan con otros objetos.
- **Modales en el tono del juego** para introducción, ayuda, mapa, cargar y terminar.
- **Historial de comandos** navegable con las flechas ↑ ↓.
- **Indicador de progreso** en la barra de estado (X % explorado).
- **Contador de visitas** (visitas/visitantes).
- **Sin frameworks. Sin build.** (una única dependencia: el script externo `vercount` para el contador de visitas).

---

## 🕹️ Cómo se juega

El juego acepta comandos de texto, pero también puedes usar los botones bajo la caja de entrada.

### Comandos principales

| Verbo | Alias | Ejemplo |
|---|---|---|
| `ir` | `atravesar`, `cruzar`, `pasar` | `ir puerta con abracadabra` |
| `coger` | `tomar` | `coger maza` |
| `dejar` | `soltar` | `dejar maza` · `dejar todo` |
| `abrir` | — | `abrir puerta con luz` |
| `matar` | `asesinar` | `matar cíclope con maza` |
| `mirar` | `observar` | `mirar` (sala) · `mirar maza` |
| `ver` | `leer` | `leer inscripción` |
| `romper` | `forzar`, `destrozar` | `romper monolito con maza` |
| `interrogar` | `preguntar` | `interrogar bruja` |
| `dar` | `regalar` | `dar cigarro a llamador` |
| `pesar` | — | `pesar maza` |
| `inventario` | — | `inventario` |
| `porciento` | — | `porciento` |
| `salvar` / `cargar` | — | `salvar` |
| `terminar` | `abandonar` | `terminar` |
| `ayuda` | — | `ayuda` |

**Preposiciones y artículos ignorados:** `el`, `la`, `por`, `al` (y tildes omitidas).

### Botones de comando

Los chips bajo la caja de entrada activan un *modo armado*:

1. Pulsa `matar` → el chip se resalta.
2. Haz clic en el `Cíclope` en la habitación → se añade al comando.
3. Haz clic en la `Maza` en el inventario → se completa `matar Cíclope con Maza` y se ejecuta.

**Reglas:**
- Verbos unarios (`ir`, `coger`, `dejar`, `interrogar`, `pesar`) ejecutan con un solo clic.
- `dar` requiere dos clics (objeto de la bolsa + NPC).
- `matar`, `romper`, `abrir` ejecutan con un clic (arma desnuda) o con dos (arma + `con`).
- `mirar` sin objeto, o clic en el fondo de la habitación = `mirar` sala.
- `terminar` abre confirmación antes de matar al jugador.

Puedes cancelar el modo armado con `Esc`, editando el input o pulsando el mismo chip.

### Convenciones

- **Fidelidad al original**: no se reescriben descripciones ni diálogos. Los mensajes nuevos solo van en modales o en contextos que el original no cubría.
- **Español** en todos los textos visibles al jugador (la obra es en español).
- **Un solo archivo**: `Fortaleza_I.html` contiene todo (CSS, JS, datos, SVG). Se mantiene así para portabilidad.
- **Mínimas dependencias**: solo el script externo `vercount` (contador de visitas). No hay frameworks ni build.

---

## 🗺️ Roadmap

### Fase 2 — Pulido visual (prioridad alta)

- [x] Plantillas SVG por tipo de habitación (exterior, interior, órgano, jardín, laberinto, patio) — 6 fondos en `BACKGROUNDS`.
- [x] Rediseño del **Patio interior** (habitación 4): fondo `patio` con pavimento en espiral, columnas de mármol negro, hiedra, luciérnagas, farol animado y hojas que caen; sprites nuevos de Atenea, Hermes y la Balanza.
- [x] Cierre del **Patio interior**: muro perimetral de sillería, remate, contrafuertes y puertas encastradas con marcos de piedra (`ROOMRENDER/04_patio_interior.png`).
- [x] Retoque del **exterior** (habitación 1): torres almenadas, torre-puerta, portal con antorchas, puerta de roble oscura, roble rediseñado, nubes animadas y viñeta (`ROOMRENDER/01_exterior.png`).
- [x] Rediseño del **Salón de recepciones** (habitación 2): columnas colosales, portal con puerta de roble arquada (cerrada y abierta), puerta negra, monolito de mármol con trébol oculto, retrato de Hitchcock, alfombra, lámpara y estandarte (`ROOMRENDER/02_recepcion.png`).
- [x] Rediseño del **Puente de mármol** (habitación 27): plataforma rocosa, puerta secreta en la roca, estatua alada en hornacina, telaraña, araña, martillo, luna con halo y abismo (`ROOMRENDER/27_puente.png`).
- [x] Rediseño de la **Sala de juegos** (habitación 3): doce mesas con doce erizos cada una, hornacina con puerta de cristal y escalera de 39 peldaños (cerrada/abierta), puertas negra y azul, candelabros y polvo suspendido (`ROOMRENDER/03_sala_de_juegos.png`).
- [x] Rediseño de la **Biblioteca** (habitación 6): estanterías colosales con servilletas, galería, atril con libro-portal, mesa de lectura, lámpara de araña, escalera de mano, puerta verde y puerta de gigantes de madera (cerrada/abierta) (`ROOMRENDER/06_biblioteca.png`).
- [x] Sombras difusas de contacto bajo los objetos apoyados en el suelo; aplicadas a las habs. 1, 2, 4, 27, 3, 6, 13, 12, 14, 15 y 16, con entradas explícitas para bases especiales (libro, ciclo, trébol, cedro).
- [x] Fuego animado con el helper `animatedFlame` en antorchas, velas, candelabros y lámparas; `ant6` conserva su estado apagado con humo.
- [x] Grafo de comunicación de `ROOMS` y orden BFS por niveles (`DOCwork/GRAFO_BFS.md`).
- [x] Rediseño del **Jardín** (habitación 13): fondo dedicado `jardin` con muralla almenada, torres, cinco hornacinas con puertas, fuente, plazuela, lechos de flores, enredaderas/trepadoras y cedro completo cuya copa alcanza la muralla (`ROOMRENDER/13_jardin.png`).
- [x] Rediseño de los **Baños de la Bestia** (habitación 12): fondo dedicado `banos` con bóveda y columnata, estanque de brocal monumental, surtidor con la cabeza de la Bestia, hornacina de la puerta verde, espejo con el reflejo del caballero y el Troll, velas, musgo y ondas de impacto en el agua. Aceptada el 17/11/2026; render en `ROOMRENDER/12_banos.png` e `I_11` archivado en `DONE/`.
- [x] Rediseño de la **Alcoba de la doncella** (habitación 14): fondo dedicado `alcoba` con bóveda, sillería húmeda y musgo; cama de dosel bajo con cabecero acolchado, cortinas recogidas y farolillo animado; tocador con espejo ovalado y banqueta; altar del corazón, rosario, miniatura y cuadro pintado de negro; escaparate dorado a la izquierda del lecho y puerta oculta de cristal a la derecha, velada a medias por una cortina de terciopelo frío; dos alfombras gastadas. Aceptada el 18/11/2026; render en `ROOMRENDER/14_alcoba.png` e `I_12` archivado en `DONE/`.
- [x] Rediseño de la **Sala de infusiones** (habitación 15): fondo dedicado `infusiones` con ventanal nocturno, puertas encastradas, candelabro de velas gastadas, mesas dispersas, arpía con manos y patas visibles, y cigarro en la mesita baja derecha. Aceptada el 19/11/2026; render en `ROOMRENDER/15_infusiones.png` e `I_13` archivado en `DONE/`.
- [x] Rediseño de los **Calabozos** (habitación 16): fondo dedicado `calabozos` con bóveda baja, sillería húmeda, celda enrejada, reja seca, cadenas, antorchas, gotera sobre el charco derecho, suelo de losas en perspectiva, vasijas (una rota), paraguas cerrado colgante y esqueleto caído de costado. Aceptada el 19/11/2026; render en `ROOMRENDER/16_calabozos.png` e `I_14` archivado en `DONE/`.
- [x] Recorrido BFS con render por habitación en `ROOMRENDER/`: hechas 1, 2, 3, 4, 5, 6, 12, 13, 14, 15, 16, 23, 27 y 28 de 50; la siguiente es la 7 (Pasillo).
- [ ] **Fuente del Jardín (habitación 13):** animar el agua que cae del surtidor y añadir ondas concéntricas de impacto donde el agua golpea el pilón.
- [x] **Regla de puertas y nichos (`GUIA_DISENO.md` §2):** hoja que llena el marco, nicho a medida y sin superposiciones. Aplicada en las habitaciones 12, 13, 14, 15, 16, 23 y 27; obligatoria en cada rediseño futuro.
- [x] Iconos por objeto — 60 sprites SVG en `SPRITES` (exterior y sprites detallados desde I_3).
- [x] Paleta de puertas gastada (azul polvoriento, verde salvia, rojo ladrillo, ocre, oro viejo…) con desgaste y canto claro, legible en salas oscuras; renders de las hab. 1, 4, 2, 27, 3, 6, 13 y 12 regenerados.
- [ ] Migrar los sprites a `<symbol>` reutilizables.
- [ ] Animación de transición entre habitaciones.
- [ ] Indicador visual de armado en el objeto clicado.

### Fase 3 — Contenido completo (prioridad media)

- [ ] Modal "Consejos" con el texto íntegro de `ADVIC.PAS`.
- [ ] Modal "Introducción" con el texto íntegro de `INSTR1.PAS` (paginado).
- [ ] Sonidos con Web Audio API (réplica de `Sounds.pas`), conmutables.

### Fase 4 — Ergonomía (prioridad media)

- [ ] Autocompletado en el input (`Tab`).
- [ ] `Ctrl+L` (cls), `F1` (repetir último), `F2` (salvar), `F9` (ejecutar).
- [ ] Exportación de partida como `.json` descargable.
- [ ] Editor de rastro (`.trk`): cargar y ejecutar paso a paso.

### Fase 5 — Refinamiento (prioridad baja)

- [x] Decisión sobre el porcentaje de progreso: **resuelta** — se usa `/50` (ver `DOCwork/REPORTE CONTINUACION.md` §3.4).
- [x] Decisión sobre el Troll y el Polvo Mágico: **resuelta** — se mantiene la fidelidad: el Troll debe morir (ver §3.5).
- [ ] Modo CRT / mono opcional.
- [ ] Modo "asistido" con guía lateral.

---

## 📜 Créditos

**Obra original:**
- Diseño y programación: **Miguel Enrique Cepero** ([[]])
- Instituto de Informática, Universidad Central de Las Villas.
- Editado por Merchise Software.

**Reconstrucción web:**
- HTML + CSS + JavaScript + SVG.
- Un solo archivo (dependencia mínima: script `vercount` para contador de visitas).
- Fiel al guion y a las mecánicas del original en Pascal.

La Fortaleza es un producto de Merchise Software. Esta reconstrucción se ofrece como homenaje, con el máximo respeto por la obra y su autor.

---

## 📄 Licencia

*(Pendiente de definir. Mientras tanto, la obra original permanece bajo los derechos de su autor y Merchise Software; esta reconstrucción web se distribuye con fines educativos y de preservación.)*

Si vas a redistribuir o modificar el proyecto, ponte en contacto con el autor original o con la comunidad que mantiene esta reconstrucción.

---

## ❓ Preguntas frecuentes

**¿Por qué un solo archivo y no una estructura modular?**
Portabilidad total: se abre desde el disco sin servidor ni build. La experiencia de "clic y jugar" era parte del espíritu del original (que también era un único `.EXE`).

**¿Puedo cargar mi partida en otro dispositivo?**
Sí, si exportas el `localStorage` manualmente o (en el futuro) cuando se implemente la exportación `.json` (Fase 4).

**¿Por qué el Troll hay que matarlo aunque le des el Polvo?**
Es una rareza del original que la versión web reproduce fielmente. Decisión tomada: se mantiene la fidelidad (ver `DOCwork/REPORTE CONTINUACION.md` §3.5).

**¿Por qué el porcentaje de progreso no llega a 100% como en otros juegos?**
En el original hay un bug (`Visits / 32` con `NRooms = 33`). La versión web usa `/50` (todas las habitaciones cuentan). Decisión tomada: mantener `/50` (ver `DOCwork/REPORTE CONTINUACION.md` §3.4).

**¿Dónde consigo el código Pascal original?**
El fuente está disponible en archivos como `FORT1.PAS`, `CASTLES.PAS`, `ADVIC.PAS`, `INSTR1.PAS`, etc., conservados por la comunidad de preservación de software en español. El reporte del guion hace referencia continua a ellos.

---

**Disfruta de La Fortaleza. Y recuerda: tenga siempre lápiz y papel a mano.**
