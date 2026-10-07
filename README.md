# BLOODSHOT STUDIO - Visual Genesis
Editor visual de niveles para motor raycast estilo 90s para **Sega Genesis / Mega Drive** usando SGDK.

[Genesis](https://img.shields.io/badge/platform-GENESIS%20%7C%20SGDK-red?style=for-the-badge)
[Status](https://img.shields.io/badge/status-v0.91b%20PROTOTYPE-yellow?style=for-the-badge)
[Resolution](https://img.shields.io/badge/res-320x224-black?style=for-the-badge)

Herramienta web que exporta:

- `level_data.h` - Mapa 32x32, player start, config FOV/RAYS
- `engine.h` / `engine.c` - Stub del motor BLOODSHOT con sin/cos tables, movimiento y colisiones
- `.zip` completo con estructura lista para SGDK

## 🎮 Demo Live

**👉 https://dariodados.github.io/bloodshot-studio/**

## Como usar

1. Abre la [demo](https://dariodados.github.io/bloodshot-studio/) o `index.html` local
2. Dibuja el mapa (0=vacío, 1=METAL_GRAY, 2=RUST_RED, 3=BLUE_TECH)
3. Posiciona al jugador
4. Exporta como C o descarga el ZIP para SGDK

## ⚠️ Estado actual del Engine - IMPORTANTE

> **El engine actual es un prototipo base funcional. Las ROMs compiladas necesitan actualizar su lógica para funcionar más cercanas al juego original.**

El export de Bloodshot Studio te da la estructura del nivel y el stub de render, pero para lograr el feeling de Bloodshot real (1994 - Domark) todavía falta implementar:

### Lo que ya hace:
- Raycasting base 80 rayos @ 320x224
- Colisión simple por tile sólido
- Tablas sin/cos precalculadas (1024)
- Export de mapa y posición del jugador

### Lo que necesita actualización para acercarse al original:
- **Texturizado real con X-Plane y sombreadores por distancia** - ahora usa tiles sólidos de color
- **Sprites de enemigos / objetos billboarding** - sistema de sprites escalados
- **Sistema de altura (pisos / techos diferentes)** - el original no era full 2.5D plano
- **Colisión fina y puertas / paredes deslizantes**
- **Manejo de VDP optimizado** - double buffer y DMA para evitar flicker en hardware real
- **Input y física de tanque (tank controls) + strafing limitado**
- **IA básica de enemigos y sistema de daño**

En resumen: **BLOODSHOT STUDIO hoy es un Level Editor + boilerplate.** El core de render necesita ser reescrito para usar el sistema de texturas del SGDK y acercarse al motor del juego original.

Si querés contribuir, revisa los Issues.

## Estructura del repo

```
/
├── index.html          # El editor completo
├── README.md
├── LICENSE
└── .gitignore
```

## Para compilar en Genesis

Requiere [SGDK](https://github.com/Stephane-D/SGDK)

```c
#include "level_data.h"
#include "engine.h"

int main() {
    ENG_init();
    ENG_loadMap(level_map);
    // loop: JOY_readJoypad, ENG_move, ENG_rotate, ENG_render
    // TODO: agregar ENG_renderSprites() + texturas reales
}
```

## Roadmap

- [ ] v0.92 - Texturas reales 8x8 desde BMP
- [ ] v0.93 - Sprites de enemigos
- [ ] v0.94 - Puertas y elevadores
- [ ] v1.0 - Demo jugable cercana al original

## Creditos
