# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A self-contained 3D Pac-Man game built as a single HTML file using Three.js (loaded via CDN). No build system, package manager, or external dependencies to install.

## Running the Game

Open `pacman3d.html` directly in a web browser. No server required.

## Architecture

**Single-file structure**: All HTML, CSS, and JavaScript in one file (`pacman3d.html`).

### Key Components

- **Maze System**: 2D array (21x19) defining walls (1), paths (0), dots (2), power pellets (3), and ghost spawns (4)
- **Three.js Scene**: Cave-themed environment with procedural rock/floor textures, fog, and dynamic lighting (torch flicker effects)
- **Pac-Man**: Character with animated body, arms/legs (walking cycle), eyes, red gloves, and red shoes
- **Ghosts**: 4 ghosts with chase AI (70% directed pursuit, 30% random), scared state during power mode
- **Collision System**: Grid-based position validation against maze array

### Game Constants (top of script)

```javascript
CELL_SIZE = 2        // World units per maze cell
PACMAN_SPEED = 0.08  // Movement speed
GHOST_SPEED = 0.04   // Ghost movement speed
POWER_DURATION = 8000 // Power pellet effect (ms)
```

### Core Functions

- `createPacman()` / `createGhosts()` - Entity creation with Three.js meshes
- `updatePacman()` / `updateGhosts()` - Movement and AI logic per frame
- `isValidPosition(x, z)` - Wall collision check against maze array
- `checkDotCollection()` / `checkGhostCollision()` - Game event handling
- `activatePowerMode()` - Triggers scared ghost state

### Controls

- WASD or Arrow Keys for movement
- Direction changes queue until valid (no immediate wall collision)
- when i say release, it means to update the gihub page of pacman3D