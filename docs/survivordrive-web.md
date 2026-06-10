# SurvivorDrive Web

SurvivorDrive Web is a small Three.js arcade driving prototype. The car moves forward by itself; the player steers, jumps, shoots, picks up resources, crashes, upgrades and tries to get farther next run.

## Current Prototype

The repo now has a playable MVP instead of only design notes:

- Vite + TypeScript + Three.js.
- Auto-forward driving with desktop, click-to-shoot and touch input.
- Generated road chunks with obstacles, pickups and damaged road sections.
- Armor, ammo, scrap, spare parts, shooting, limited jumps, run end and restart.
- Local `localStorage` progression with a small garage upgrade loop.
- Core rules split away from rendering so Vitest can cover resources, damage and upgrades without WebGL.

The source is deliberately small: `src/core` for loop/input/random, `src/entities` for car/collision, `src/game` for resources/scoring/damage/upgrades, `src/world` for chunk generation and spawn rules, `src/render` for Three.js scene/meshes/materials, and `src/ui` for the HUD.

## Design Notes

The design goal is readability at speed. Obstacles should look like obstacles, pickups should be obvious, and upgrades should change how the car feels instead of only moving numbers up.

The loop is short on purpose: drive, dodge, collect, shoot, crash, spend scrap, retry.

## Status

Private alpha. It is playable, but still a prototype. The next work would be better vehicle feel, clearer hit feedback, more varied chunks and a stronger upgrade economy.
