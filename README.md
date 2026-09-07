# Endless Runner

A complete responsive HTML5 Canvas endless runner by **tivalsdeveloper**. The player runs automatically through the Neon Wilds, jumping and sliding past procedural hazards, collecting coins, unlocking runners, and chasing a locally saved high score.

## Features

- Delta-time game loop powered by `requestAnimationFrame()`
- Desktop keyboard, mobile swipe, and optional touch-button controls
- Running, jumping, sliding, damage, invincibility, and game-over states
- Procedural rocks, crates, branches, barriers, holes, and moving drones
- Coins, near-miss bonuses, milestones, three unlockable runners, missions, and achievements
- Shield, coin magnet, double score, slow motion, and double-jump power-ups
- Three-layer parallax scenery with a changing day/night atmosphere
- Synthesized sound effects and optional background pulse—no downloads required
- Persistent best score, total coins, settings, selected runner, unlocks, and progress
- Responsive presentation optimized for phones and low-resource computers

## Run the game

No installation, server, build tool, or internet connection is required. Open `index.html` in a modern browser. If your browser restricts local files, run `python3 -m http.server` in this folder and visit `http://localhost:8000`.

## Controls

| Action | Desktop | Mobile |
|---|---|---|
| Jump | Space, W, or Arrow Up | Swipe up or JUMP |
| Slide | S or Arrow Down | Swipe down or SLIDE |
| Pause | P or Escape | Pause button |

## Project structure

```text
endless-runner/
├── index.html
├── style.css
├── script.js
├── assets/
│   ├── images/
│   ├── sounds/
│   └── music/
└── README.md
```

The asset directories are intentionally empty because all original graphics are drawn on Canvas and audio is generated with the Web Audio API. This keeps the game small and fully offline.

## Game loop

`Game.loop()` calculates frame-independent delta time, updates the player and gravity, moves background and world objects, performs procedural spawning and collision checks, advances power-up timers and score, then renders the next frame. Delta time is capped to prevent a large physics leap after a suspended tab resumes.

## Customization

To add an obstacle, add its dimensions to the map in `Obstacle`, draw its appearance in `Obstacle.draw()`, and include its name in `Game.spawnObstacle()` at the desired score threshold. Keep its collision box slightly smaller than its artwork for fair play.

To add a character, append `[name, coinCost]` to `Game.characters` and add a matching color to the player and runner-card color arrays.

To tune difficulty, edit the speed calculation and `spawnTimer` range in `Game.update()`. Larger spawn delays are easier; the current curve shortens gradually and has a safe minimum.

## LocalStorage

The `tivalsRunnerSaveV1` entry stores high score, total coins, settings, selected/unlocked characters, run totals, mission progress, and achievements. Clearing browser site data resets progress.

Powered by **tivalsdeveloper**.
