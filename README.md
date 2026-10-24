# Defeat Angel War

**Autobattler roguelike 2D hecho con Unity, jugable en el navegador.**

▶️ **Jugar:** https://jesuscarrascofernandez-hash.github.io/juego-uja/

Tu héroe combate solo: tú decides entre combate y combate. Tras cada victoria eliges una de tres cartas para mejorarlo, combinas cartas para activar sinergias y avanzas por 3 fases de 6 combates (con mini jefe y jefe) hasta el jefe final. Si mueres, empiezas de cero.

| Control | Acción |
|---|---|
| Clic | Elegir carta / botones |
| Esc | Pausa · saltar vídeo |
| x1 · x2 · x4 | Velocidad de los combates (arriba a la derecha; se recuerda) |
| MODO DEV · Ctrl+F9 | Modo desarrollador |

### Modo desarrollador

Botón **MODO DEV** (o <kbd>Ctrl</kbd>+<kbd>F9</kbd>). Pausa el juego mientras está abierto y tiene cinco pestañas:

- **Jugador**: vida, ataque, defensa, velocidad de ataque, crítico, esquiva, daño crítico y vidas extra; curar o matar al héroe.
- **Enemigo**: stats del enemigo del combate en curso; curarlo o matarlo al instante.
- **Cartas**: darte cualquier carta Normal o Héroe, completar sinergias y cambiar la probabilidad de cartas Héroe.
- **Combates**: saltar a cualquier combate o jefe de cualquier fase y elegir velocidad (x0.5 a x8).
- **Recuerdos**: desbloquear o reiniciar la colección del menú.

Funciona en las versiones actuales de Chrome, Edge, Firefox y Safari (necesita WebGL 2). Está pensado para ordenador.

## Autores

Realizado por **Alberto Castaño Mercader**, **Uriel Martínez Martínez** y **Jesús Carrasco Fernández** como proyecto intermodular.

## Assets de terceros

El juego usa packs de assets gratuitos cuyas licencias permiten su uso sin fines comerciales. Este proyecto **no tiene ánimo de lucro**. Todos los derechos de los assets pertenecen a sus autores:

- SPUM (personajes pixel art)
- Simple Pixel UI
- Fantasy Cursor Pack
- 2D Pixel Art Skull Icons & Emblems (Screw And Tape)
- Monsters Creatures Fantasy
- Fondos de batalla *Battleground* y fondo parallax de montañas del menú
- Fuentes: Liberation Sans (OFL) y Minecraft

## Contenido del repositorio

Este repositorio solo contiene la versión web compilada (WebGL) y la página que la carga:

```
index.html          Página de inicio y cargador del juego
img/                Imágenes de la página (fondo del menú, icono)
Build/              Archivos generados por Unity (Gzip + descompresión en el navegador)
StreamingAssets/    Vídeos de la intro y los finales (H.264, cargados por URL)
.nojekyll           Para que GitHub Pages sirva los archivos tal cual
```

## Cómo actualizar la versión web

En el proyecto de Unity (Unity 6000.3.11f1 con el módulo **Web** y sesión iniciada en Unity Hub):

1. Ejecuta `construir_web.bat` (o el menú **Herramientas > Construir versión Web (WebGL)**).
   Genera `Builds/WebGL/juego-uja`.
2. Ejecuta `publicar_web.bat`: copia la carpeta `Build` a la copia local de este repositorio
   (`Builds/WebGL/sitio`) y hace commit y push.
3. GitHub Pages se actualiza solo en uno o dos minutos.

Si cambias algún vídeo, conviértelo a H.264 720p con `+faststart` y guárdalo en `StreamingAssets/Videos`
con el nombre en minúsculas y guiones bajos (por ejemplo `game over.mp4` → `game_over.mp4`).

Notas técnicas: compresión Gzip con *Decompression Fallback* (GitHub Pages no envía la cabecera
`Content-Encoding`), caché de datos activada y vídeos cargados por URL, porque WebGL no reproduce `VideoClip`.
