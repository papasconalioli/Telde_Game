# Saltos por Telde

Juego de plataformas 2D en *pixel art* sobre la historia de Canarias, ambientado en el municipio de **Telde (Gran Canaria)**. Es un prototipo de cuatro fases hecho con HTML, CSS y JavaScript (canvas) en un único archivo, sin dependencias ni archivos externos aparte de dos fuentes de Google Fonts.

## Cómo jugar

- **En el ordenador:** descarga el repositorio y abre `index.html` en el navegador.
- **Publicado en la web:** si activas GitHub Pages en este repositorio (*Settings → Pages → Deploy from a branch → `main` / root*), el juego queda disponible en `https://papasconalioli.github.io/telde_game/`.

### Controles

| Acción | Teclado | Móvil |
|---|---|---|
| Moverse | ← → o A D | ◀ ▶ |
| Saltar (mantén para saltar más alto) | Espacio, ↑ o W | Saltar |
| Bajar de un balcón, muelle o repisa | ↓ o S | ▼ |
| Lanzar un plátano (parte 4) | X o K | Lanzar |
| Pausa | Esc o P | II |
| Sonido sí/no | M | — |

En los menús, las flechas mueven la selección e Intro confirma.

## Las cuatro fases

| Parte | Lugar | Mecánica propia | Jefe |
|---|---|---|---|
| 1 | Plaza de San Juan y Basílica de San Juan Bautista | Balcones canarios que solo se pisan desde arriba | La Bruja del Barranco (fuegos fatuos y espíritus) |
| 2 | Playa de La Garita y el Bufadero | Bufaderos: chorros de agua que te lanzan sobre el mar | El Tritón del Bufadero (caracolas y medusas) |
| 3 | Montaña de Cuatro Puertas | Repisas agrietadas que se derrumban | El Guardián de Cuatro Puertas (piedras y cabras) |
| — | Súper El Perenquén | Tienda: se gastan las monedas en gofio, papas con mojo y plátanos | — |
| 4 | Barranco Real de Telde, hasta Tara | Acequias que arrastran al jugador | El Tibicena (bolas de fuego y cuervos) |

Todos los jefes y el supermercado son inventados. Al final de cada parte, una pantalla cuenta la historia real del lugar.

Otras funciones: menú principal con portada animada, dificultad Fácil/Difícil, español e inglés, "Continuar" desde la última parte alcanzada, música de 8 bits y efectos generados con Web Audio (sin archivos de audio). La música es original; la de la portada es una isa compuesta para el juego.

## Cómo está organizado el código

Todo está en `index.html`. El script está dividido en bloques numerados y comentados:

| Bloque | Contenido |
|---|---|
| 1. Configuración | Tamaños, física, bufaderos y repisas |
| 1b. Dificultad | Valores de Fácil y Difícil (`DIFICULTADES`) |
| 1c. Sonido | Canciones como notas en texto (`CANCIONES`) y efectos |
| 1d. Textos e idioma | Todos los textos en español e inglés (`TEXTOS`) |
| 2. Niveles | Mapas de las cuatro partes (`NIVELES`) |
| 3–5. Estado, entrada y física | Jugador, teclado y controles táctiles, colisiones, bufaderos, repisas y acequias |
| 5b. Jefes | Ciclo de ataque común y diferencias de cada jefe (`JEFES`), plátanos |
| 6–7. Fondos y dibujo | Paralaje y dibujo de escenarios, personajes, súper y portada |
| 8. Marcador, menús y pantallas | HUD, menú principal, pausa, súper y pantallas entre partes |
| 9. Bucle principal | Bucle de juego a 60 pasos por segundo |

### Cambios habituales

- **Añadir una fase:** añade otra entrada a `NIVELES` (con `crearNivel`), sus textos en `TEXTOS` con la clave de su `id` (por ejemplo `n5.titulo`, `n5.lugar`, `n5.fin.titulo`…) y, si tiene jefe nuevo, una entrada en `JEFES` y su función de dibujo.
- **Ajustar la dificultad:** valores en `DIFICULTADES`; los golpes de cada jefe, en su campo `vida`.
- **Cambiar la música:** las melodías están escritas como notas separadas por espacios (`'C5 E5 G5 -'`), una corchea cada una; `-` es un silencio.
- **Añadir un idioma:** un bloque nuevo en `TEXTOS` y su botón en el menú.
- **Precios del súper:** `PRODUCTOS`.

El juego guarda en el navegador (localStorage) la dificultad, el idioma, el sonido y la última parte alcanzada.

## Fuentes de los datos históricos

- [Bufadero La Garita – Atlas Obscura](https://www.atlasobscura.com/places/bufadero-la-garita)
- [Four Doors cave site, Telde – Wikipedia](https://en.wikipedia.org/wiki/Four_Doors_cave_site,_Telde)
- [Tara y Cendro – Love Me Telde](https://lovemetelde.blogspot.com/2020/11/tara-y-cendro.html)
- [Tibicena – Wikipedia](https://en.wikipedia.org/wiki/Tibicena)
