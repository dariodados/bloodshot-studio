# BLOODSHOT STUDIO - Visual Genesis
Editor visual de niveles para motor raycast estilo 90s para **Sega Genesis / Mega Drive** usando SGDK.

![Genesis](https://img.shields.io/badge/platform-GENESIS%20%7C%20SGDK-red?style=for-the-badge)
![Status](https://img.shields.io/badge/status-v0.91b%20NTSC-yellow?style=for-the-badge)
![Resolution](https://img.shields.io/badge/res-320x224-black?style=for-the-badge)

Herramienta web que exporta:

- `level_data.h` - Mapa 32x32, player start, config FOV/RAYS
- `engine.h` / `engine.c` - Stub del motor BLOODSHOT con sin/cos tables, movimiento y colisiones
- `.zip` completo con estructura lista para SGDK

## Demo Live

Una vez que actives GitHub Pages, tu editor va a estar en:
`https://TU_USUARIO.github.io/bloodshot-studio/`

## Como usar

1. Abre `index.html` o entra a la demo
2. Dibuja el mapa (0=vacío, 1=METAL_GRAY, 2=RUST_RED, 3=BLUE_TECH)
3. Posiciona al jugador
4. Exporta como C o descarga el ZIP para SGDK

## Estructura del repo

```
/
├── index.html          # El editor completo (React artifact)
├── README.md
├── LICENSE
├── .gitignore
└── docs/
    └── preview.png     # (opcional) screenshot
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
}
```

## Creditos

Creado por Dario Dados - BLOODSHOT STUDIO v0.91b
