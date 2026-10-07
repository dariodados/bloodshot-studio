# BLOODSHOT STUDIO - Visual Genesis
Editor visual de niveles para motor raycast estilo 90s para **Sega Genesis / Mega Drive** usando SGDK.

[Genesis](https://img.shields.io/badge/platform-GENESIS%20%7C%20SGDK-red?style=for-the-badge)
[Status](https://img.shields.io/badge/status-v0.91b%20PROTOTYPE-yellow?style=for-the-badge)
[Resolution](https://img.shields.io/badge/res-320x224-black?style=for-the-badge)
[License](https://img.shields.io/badge/license-MIT-blue?style=for-the-badge)

## 🎮 Demo Live

**👉 https://dariodados.github.io/bloodshot-studio/**

Herramienta web que exporta:
- `level_data.h` - Mapa 32x32, player start, config FOV/RAYS
- `engine.h` / `engine.c` - Stub del motor BLOODSHOT con sin/cos tables
- `.zip` completo con estructura lista para SGDK

## ⚠️ Estado del Engine

> **El engine actual es un prototipo base funcional. Las ROMs compiladas necesitan actualizar su lógica para funcionar más cercanas al juego original (Bloodshot / Battle Frenzy - Domark 1994).**

### Lo que ya hace:
- Raycasting base 80 rayos @ 320x224 (NTSC)
- Colisión simple por tile sólido
- Tablas sin/cos precalculadas (1024)
- Export de mapa y posición del jugador a C

### Lo que necesita actualización:
- Texturizado real con X-Plane y sombreado por distancia (hoy son colores sólidos)
- Sprites de enemigos / objetos con billboarding
- Sistema de alturas, puertas deslizantes y elevadores
- VDP optimizado con double buffer y DMA para hardware real
- Tank controls + física fiel al original
- IA básica y sistema de daño

**En resumen:** BLOODSHOT STUDIO hoy es un Level Editor + boilerplate. El core de render debe reescribirse con el sistema de texturas de SGDK para acercarse al motor original.

## 🗺️ Roadmap

- [ ] v0.92 - Texturas reales 8x8 desde BMP
- [ ] v0.93 - Sprites de enemigos
- [ ] v0.94 - Puertas y elevadores  
- [ ] v1.0 - Demo jugable cercana al original

## 🚀 Como usar

1. Abre la [demo](https://dariodados.github.io/bloodshot-studio/)
2. Dibuja el mapa (0=vacío, 1=METAL_GRAY, 2=RUST_RED, 3=BLUE_TECH)
3. Posiciona al jugador
4. Exporta como C o descarga el ZIP para SGDK

```c
#include "level_data.h"
#include "engine.h"

int main() {
    ENG_init();
    ENG_loadMap(level_map);
    // TODO: ENG_renderSprites() + texturas reales
    // loop: JOY_readJoypad, ENG_move, ENG_rotate, ENG_render
}
```

Requiere [SGDK](https://github.com/Stephane-D/SGDK)

## 👾 Creditos

**Creado por Dario Dados - Pergamino, Buenos Aires, Argentina**

- **Autor / Dev:** Dario Dados ([@dariodados](https://github.com/dariodados))
- **Inspiración:** Bloodshot / Battle Frenzy (Domark, 1994) - FPS pionero en Mega Drive
- **SDK:** SGDK de Stephane Dallongeville
- **Testing:** BlastEm, Exodus, hardware con Mega EverDrive

**Licencia MIT** - Libre para usar, modificar, aprender y crear tus propios FPS retro. Si usas este editor, un crédito o link al repo se agradece.

---
*Hecho con pasión retro en Argentina - 2026*
