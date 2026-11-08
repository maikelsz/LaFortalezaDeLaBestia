# La Fortaleza

Reconstrucción web de **La Fortaleza**, la aventura conversacional escrita en la década de 1990 por Miguel Enrique Cepero (Merchise Software, Instituto de Informática, Universidad Central de Las Villas "Marta Abreu", Cuba) en lenguaje de programación Pascal para MS-DOS.

El jugador es un hombre común enviado a matar a "la Bestia" dentro de una fortaleza. Deberá explorar 50 habitaciones, resolver acertijos, enfrentarse a criaturas y destruir los cuatro Centros de la Bestia antes de poder vencerla.

**Este es un trabajo en progreso**

---

## 🎮 Jugar

Abre `Fortaleza.html` en cualquier navegador moderno. No requiere servidor, instalación ni conexión a internet.

O en este vinculo: <https://maikelsz.github.io/LaFortalezaDeLaBestia/Fortaleza_I.html>

Todo el juego —datos, lógica, estilos y gráficos SVG— vive en **un único archivo HTML**.

---

## ✨ Características

- **50 habitaciones** y **~90 objetos** fielmente reconstruidos del original en Pascal.
- **Parser en español** con sinónimos (`ir`/`atravesar`/`cruzar`, `coger`/`tomar`, `matar`/`asesinar`, etc.).
- **Sistema de comandos armados**: pulsa un botón, haz clic en los objetos, y el comando se compone y ejecuta solo.
- **Puertas con estado compartido**: si abres una puerta y cruzas, en la habitación de enfrente ya aparece abierta.
- **Colores de puertas derivados del nombre** (azul, verde, roja, dorada, de cristal…).
- **Guardado y carga** en `localStorage` con confirmación diegética.
- **Mapa opcional** con advertencia previa (el juego original recomendaba dibujarlo a mano).
- **Inventario visible** con barra de peso y comentario dinámico.
- **Modales en el tono del juego** para introducción, ayuda, mapa, cargar y terminar.
- **Historial de comandos** navegable con las flechas ↑ ↓.
- **Sin dependencias externas.** Sin frameworks. Sin build.

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

---

## 📁 Estructura del repositorio

```
la-fortaleza/
├── index.html              ← el juego completo (CSS + JS + datos embebidos)
├── README.md               ← este archivo
├── docs/
│   ├── REPORTE-GUION.md    ← catálogo de habitaciones, objetos, contraseñas y puzzles
│   └── INFORME-CONTINUIDAD.md  ← handoff entre sesiones de trabajo
└── (opcional)
    ├── LICENSE
    └── screenshots/
        ├── habitacion.png
        ├── inventario.png
        └── mapa.png
```

---

## 🛠️ Desarrollo

### Requisitos

Ninguno más allá de un navegador moderno (Chrome/Edge/Firefox/Safari de los últimos 3 años) para jugar.

Para desarrollar cómodamente:
- Editor con resaltado de sintaxis HTML/CSS/JS.
- Opcionalmente, un servidor estático local (`python -m http.server`, `npx serve`, etc.) — útil para recargar más rápido durante la edición.

### Comprobaciones antes de un commit

Abre `index.html` y verifica contra el **checklist de pruebas** en `docs/INFORME-CONTINUIDAD.md` (§13). En resumen:

- [ ] El flujo principal llega a la victoria.
- [ ] Las puertas sincronizan su estado entre habitaciones.
- [ ] Los chips arman comandos correctamente.
- [ ] Los modales (mapa, cargar, terminar) piden confirmación con el tono correcto.
- [ ] No se ha roto el guardado/carga en `localStorage`.

### Convenciones

- **Español** en todos los textos visibles al jugador (la obra es en español).
- **Tonillo diegético** para mensajes nuevos: nada de "Error 404"; siempre con el registro del juego.
- **Fidelidad al original**: no se reescriben descripciones ni diálogos. Los mensajes nuevos solo van en modales o en contextos que el original no cubría.
- **Un solo archivo**: `index.html` contiene todo. Se mantiene así para portabilidad.
- **Sin dependencias**: no se añaden librerías JS/CSS externas.

---

## 🗺️ Roadmap

### Fase 2 — Pulido visual (prioridad alta)

- [ ] Plantillas SVG por tipo de habitación (exterior, interior, órgano, jardín, laberinto).
- [ ] Iconos reutilizables (`<symbol>`) por objeto.
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

- [ ] Decisión sobre el porcentaje de progreso (ver `docs/INFORME-CONTINUIDAD.md` §3.4).
- [ ] Decisión sobre el Troll y el Polvo Mágico (ver §3.5).
- [ ] Modo CRT / mono opcional.
- [ ] Modo "asistido" con guía lateral.

---

## 📚 Documentación

- **[`docs/REPORTE-GUION.md`](docs/REPORTE-GUION.md)** — catálogo completo de habitaciones, objetos, contraseñas, puzzles, esquemas SVG y warnings del original. Es la **referencia canónica** del contenido del juego.
- **[`docs/INFORME-CONTINUIDAD.md`](docs/INFORME-CONTINUIDAD.md)** — handoff entre sesiones de trabajo: qué está hecho, qué falta, decisiones de diseño tomadas, checklist de pruebas, roadmap.

Si vas a contribuir al contenido (añadir descripciones, corregir contraseñas, resolver claves pendientes), **actualiza el reporte del guion en el mismo PR**.

---

## 📜 Créditos

**Obra original:**
- Diseño y programación: **Miguel Enrique Cepero** ([[]])
- Instituto de Informática, Universidad Central de Las Villas.
- Editado por Merchise Software.

**Reconstrucción web:**
- HTML + CSS + JavaScript + SVG.
- Un solo archivo, sin dependencias externas.
- Fiel al guion y a las mecánicas del original en Pascal.

La Fortaleza es un producto de Merchise Software. Esta reconstrucción se ofrece como homenaje, con el máximo respeto por la obra y su autor.

---

## 🤝 Contribuir

1. Fork del repositorio.
2. Nueva rama: `git checkout -b feature/mi-aporte`.
3. Edita `index.html` (o `docs/` si trabajas en documentación).
4. Verifica contra el checklist de pruebas.
5. Pull request describiendo el cambio y su motivación.

**Ideas para contribuir:**
- Diseñar SVG de habitaciones por tipo.
- Decodificar `key[26]` y `key[39]` de los bytes originales.
- Escribir autocompletado del input.
- Implementar sonidos con Web Audio.
- Traducir el README a otros idiomas.
- Reportar bugs con un ejemplo reproducible.

---

## 🐛 Reportar un bug

Abre un issue con:

- Descripción breve del problema.
- Pasos para reproducirlo (comando, habitación, objeto involucrado).
- Comportamiento esperado vs. observado.
- Navegador y sistema operativo.
- Si es posible, captura de pantalla.

---

## ❓ Preguntas frecuentes

**¿Por qué un solo archivo y no una estructura modular?**
Portabilidad total: se abre desde el disco sin servidor ni build. La experiencia de "clic y jugar" era parte del espíritu del original (que también era un único `.EXE`).

**¿Puedo cargar mi partida en otro dispositivo?**
Sí, si exportas el `localStorage` manualmente o (en el futuro) cuando se implemente la exportación `.json` (Fase 4).

**¿Por qué el Troll hay que matarlo aunque le des el Polvo?**
Es una rareza del original que la versión web reproduce fielmente. Hay una discusión abierta sobre si corregirlo (ver `docs/INFORME-CONTINUIDAD.md` §3.5).

**¿Por qué el porcentaje de progreso no llega a 100% como en otros juegos?**
En el original hay un bug (`Visits / 32` con `NRooms = 33`) y se cuenta de más. La versión web actualmente usa `/50`. Hay una decisión pendiente para alinearlo (ver `docs/INFORME-CONTINUIDAD.md` §3.4).

---

**Disfruta de La Fortaleza. Y recuerda: tenga siempre lápiz y papel a mano.**
