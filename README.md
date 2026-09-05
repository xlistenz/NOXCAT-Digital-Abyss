# NOXCAT-Digital-Abyss
Digital Abyss is an original 2D cyber-pixel platformer. Guide NOXCAT through digital ruins, double jump across platforms, collect Bitcoin-style tokens, activate NOX Beacons, and reach the NOX CORE. Enemy encounters trigger NOXCAT, blockchain, Web3, wallet, and crypto quiz questions: answer correctly to win safely; answer wrong to lose HP.
NOXCAT-Digital-Abyss

An original HTML5 Canvas side-scrolling pixel platformer featuring NOXCAT in a futuristic Web3 digital ruin.

Overview

NOXCAT-Digital-Abyss combines retro 16-bit-inspired platform action with NOXCAT, blockchain education, and cyber-pixel visuals. Players guide NOXCAT through a digital abyss filled with technology platforms, hazards, checkpoints, energy tokens, enemy encounters, and a final NOX CORE objective.

The game is fully browser-based and requires no backend, account, installation, database, or external API.

Core Gameplay

Move left and right through a side-scrolling level

Double jump across elevated, moving, and hazardous platforms

Collect Bitcoin-inspired NOX ENERGY tokens

Activate NOX Beacon checkpoints

Avoid falling, hazards, and enemy encounters

Reach the NOX CORE before the 180-second timer expires

Earn score from tokens, defeated enemies, checkpoints, completion, and remaining time

Knowledge Challenge System

Enemy contact is designed as an educational interaction.

A precise top-down stomp defeats an enemy directly.

Any other player-to-enemy contact opens a multiple-choice question.

Questions cover blockchain, Web3, wallets, private keys, MPC, DeFi, NFTs, RWA, multi-chain concepts, NOXCAT, $NOX, Arbitrum, Escrow, Staking, and crypto ecosystem concepts.

Correct answer: enemy is defeated, player keeps HP, and receives score.

Incorrect answer: player loses one HP and respawns at the latest activated NOX Beacon.

Individual enemy collision locks, cooldowns, and player invulnerability prevent repeated damage from a single contact.

Visual Direction

The game uses an original cyber-pixel visual world built around NOXCAT’s identity:

Black cat protagonist with neon-green eyes and goggles

16-bit-inspired sprite animation

Dark glass UI with neon-green system accents

Cyber city and market-themed background

Original technology, stone, energy, floating, moving, bounce, breakable, and hazard platform types

BLOCK BOT and GLITCH BEETLE enemy designs

Bitcoin-inspired collectible token art

All sprite sheets are rendered through explicit Canvas source rectangles to prevent adjacent atlas frames from appearing in-game. Visual sprite offsets are kept separate from gameplay collision boxes.

Controls

Desktop

A / D or ← / →: Move

Space or W: Jump

Press jump again while airborne: Double jump

F3: Toggle developer collision and sprite debug overlay

Mobile

Use the on-screen ←, →, and JUMP controls.

Landscape orientation is recommended.

Audio

The game uses original Web Audio API sound effects and chiptune-style audio:

Jump

Footsteps

Token collection

Enemy stomp

Damage

Checkpoint activation

Mission completion

Game over

Procedural background music

Game Systems

HTML5 Canvas rendering

Side-scrolling camera

Gravity, acceleration, friction, and double-jump physics

Platform and ground collision

Enemy patrol movement

Spawn-point-based enemy initialization

Player HP and invulnerability system

Checkpoint and respawn system

Score, combo, energy, and countdown timer UI

Start, mission-complete, and game-over screens

Desktop keyboard and mobile touch input

Debug console logs for enemy spawn, collision, question events, answer results, damage, and enemy defeat

Project Structure

index.html
style.css
theme.css
quiz.css
game.js
OPEN_GAME.bat
assets/
  player/
  enemies/
  blocks/
  background/
  ui/
  audio/

Run Locally

Download or clone this repository.

Open the project folder.

Double-click OPEN_GAME.bat on Windows, or open index.html in a modern browser.

Select START GAME.

For the best audio experience, interact with the Start Game button first, as browsers require user interaction before enabling Web Audio.

Customization

Change the game time

In game.js, update the this.time = 180 value.

Add or edit questions

Edit the questions collection in game.js. Each entry includes a question, three choices, and the correct answer index.

Add a level section

Edit Level.make() in game.js to add platforms, enemies, collectibles, Beacons, or a new NOX CORE position.

Replace sprites

Replace assets inside:

assets/player/
assets/enemies/
assets/blocks/
assets/background/
assets/ui/

When replacing sprite sheets, update the matching source rectangle definitions in SPRITES or PLATFORM_SPRITES inside game.js.

License and Asset Notice

NOXCAT-related visual assets should only be used with permission from the applicable IP owner. The game’s original code, gameplay logic, question system, platform layout, UI, and procedural audio are intended as a standalone browser-game project.
