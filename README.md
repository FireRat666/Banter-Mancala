# Banter Mancala

A fully synced multiplayer Mancala game for Banter using Space State Properties.

## Quick Start

Add to your Banter world HTML:

```html
<script src="https://banter-mancala.firer.at/Mancala.js"></script>
```

## Configuration

Pass parameters via URL query string on the script src:

```html
<script src="https://banter-mancala.firer.at/Mancala.js?boardPosition=0%201.5%20-2&lighting=lit"></script>
```

### Available Parameters

| Parameter | Default | Description |
|-----------|---------|-------------|
| `boardPosition` | `0 1.1 -2` | Position of the game board (x y z) |
| `boardRotation` | `0 0 0` | Rotation of the game board (euler angles) |
| `boardScale` | `1 1 1` | Scale of the game board |
| `resetPosition` | `0 0 1.5` | Position of the reset button |
| `resetRotation` | `0 0 0` | Rotation of the reset button |
| `resetScale` | `1 1 1` | Scale of the reset button |
| `instance` | Page URL | Unique instance ID for multiple boards |
| `hideUI` | `false` | Hide the reset button |
| `hideBoard` | `false` | Make board transparent (for custom boards) |
| `useCustomModels` | `false` | Use GLB models instead of geometry |
| `lighting` | `unlit` | `lit` or `unlit` shader mode |
| `addLights` | `true` | Add directional light when using lit mode |

## Custom GLB Models

When `useCustomModels=true`, place these files in `Models/` relative to the script:

- `MancalaPit.glb` - The pit/hole geometry
- `MancalaStore.glb` - The larger store/mancala geometry
- `MancalaStone.glb` - Individual stone/seed

## Game Rules

Standard Mancala (Kalah) rules:
- 2 players, 6 pits each + 1 store
- 4 stones per pit at start
- Pick up all stones from a pit, distribute counter-clockwise
- Skip opponent's store when distributing
- Land in your store = extra turn
- Land in empty pit on your side = capture opposite pit's stones
- Game ends when one side is empty; most stones wins

## Board Layout

```
    [12] [11] [10] [9] [8] [7]    ← Player 2's pits
[13]                          [6] ← Stores
    [0]  [1]  [2]  [3] [4] [5]    ← Player 1's pits
```

## Sync

Uses Banter Space State Properties with key `mancala_game_{instance}` for real-time multiplayer sync.
