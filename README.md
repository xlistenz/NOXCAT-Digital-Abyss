# NOXCAT-Digital-Abyss
Digital Abyss is an original 2D cyber-pixel platformer. Guide NOXCAT through digital ruins, double jump across platforms, collect Bitcoin-style tokens, activate NOX Beacons, and reach the NOX CORE. Enemy encounters trigger NOXCAT, blockchain, Web3, wallet, and crypto quiz questions: answer correctly to win safely; answer wrong to lose HP.
NOXCAT-Digital-Abyss

# NOXCAT-Digital-Abyss

**NOXCAT-Digital-Abyss** is an original browser-based 2D side-scrolling pixel platformer featuring NOXCAT in a futuristic Web3 digital world.

The project combines retro 16-bit-inspired platform gameplay with blockchain education, NOXCAT ecosystem knowledge, cyber-pixel environments, interactive enemy encounters, original procedural audio, and mobile-friendly browser controls.

> The project is designed to run directly in a modern browser with no backend, database, login system, API key, account, or package installation required.

---

## Table of Contents

- [Game Overview](#game-overview)
- [Core Gameplay](#core-gameplay)
- [Player Character](#player-character)
- [Level Design](#level-design)
- [Platform Types](#platform-types)
- [Enemy System](#enemy-system)
- [Blockchain and NOXCAT Quiz System](#blockchain-and-noxcat-quiz-system)
- [Collectibles and Score](#collectibles-and-score)
- [Health, Damage, and Checkpoints](#health-damage-and-checkpoints)
- [Visual Style](#visual-style)
- [Sprite and Collision Architecture](#sprite-and-collision-architecture)
- [Audio System](#audio-system)
- [Controls](#controls)
- [Mobile Support](#mobile-support)
- [User Interface](#user-interface)
- [Project Structure](#project-structure)
- [Run Locally](#run-locally)
- [Customization](#customization)
- [Debug Mode](#debug-mode)
- [Asset Notice](#asset-notice)

---

## Game Overview

Players control **NOXCAT**, a black cat with neon-green eyes, goggles, dark clothing, blue pants, white shoes, and a recognizable pixel-art appearance.

The objective is to survive the digital abyss, collect energy, activate NOX Beacon checkpoints, answer knowledge challenges, and reach the final **NOX CORE** before the countdown ends.

The game world is built around a futuristic cyber-city atmosphere, blending blockchain-inspired visuals, digital market imagery, technology platforms, neon light effects, and original pixel platform gameplay.

---

## Core Gameplay

The main objective is to travel from the left side of the level to the NOX CORE at the far end of the map.

Players can:

- Move left and right
- Perform a double jump
- Travel across ground, floating, and moving platforms
- Use bounce platforms for higher jumps
- Avoid hazards and falling
- Collect Bitcoin-inspired energy tokens
- Activate NOX Beacon checkpoints
- Encounter enemies
- Answer blockchain and NOXCAT questions
- Earn score from gameplay actions
- Complete the mission before the timer reaches zero

The default mission duration is **180 seconds**.

---

## Player Character

NOXCAT is the only playable character.

### Character Features

- Black cat design
- Bright neon-green eyes
- Flight goggles
- Dark jacket or vest
- Dark blue pants
- White shoes
- Pixel-art sprite animation
- Left and right facing directions
- Idle, run, jump, fall, hurt, and victory-related animation states

### Player Movement

The player uses acceleration, gravity, friction, collision detection, and a double-jump system.

- Ground speed and air speed use the same movement speed behavior.
- Players can jump once from the ground.
- Players can jump once more while airborne.
- Falling below the level removes HP and returns the player to the latest checkpoint.
- The player cannot leave the level’s horizontal boundaries.

---

## Level Design

The current level is a cyber-themed digital ruin containing multiple platform heights, enemy zones, collectibles, hazards, moving paths, checkpoints, and a final core objective.

### Level Components

- Long ground platforms
- Elevated platform routes
- Floating platform sequences
- Moving platform sections
- Breakable platform sections
- Bounce platform routes
- Hazard sections
- Enemy patrol zones
- Two NOX Beacon checkpoints
- Final NOX CORE destination

The side-scrolling camera follows player progress horizontally while keeping vertical movement stable and readable.

---

## Platform Types

The game includes multiple platform and terrain types.

| Type | Description |
|---|---|
| `stone` | Base stone terrain platform |
| `metal` | Reinforced industrial metal platform |
| `pulse` | Futuristic pulse or circuit-style platform |
| `energy` | Technology platform with an energy-core visual |
| `float` | Floating platform |
| `break` | Breakable platform that collapses after repeated landings |
| `bounce` | Platform that launches the player upward |
| `hazard` | Dangerous platform that damages the player |
| `moving` | Horizontally moving platform |

Platform art is rendered using source rectangles from the platform atlas.

To preserve each platform asset’s appearance:

- Platform sprites keep their original aspect ratio.
- Platform tiles are repeated as complete visual units.
- The game does not stretch individual platform sprites.
- The game does not show half platform sprites at the left or right edge.
- Platform collision boxes remain independent from visual sprite dimensions.

---

## Enemy System

The game contains two original enemy types.

### BLOCK BOT

A compact black technology robot with neon-green eyes.

Behavior:

- Patrols left and right
- Turns around at platform edges
- Can be defeated by a top-down stomp
- Triggers a knowledge question when touched from another direction

### GLITCH BEETLE

A digital cyber-beetle with purple and neon-green glitch details.

Behavior:

- Patrols platforms
- Can move faster during its glitch movement state
- Can be defeated by a top-down stomp
- Triggers a knowledge question when touched from another direction

### Enemy Spawn System

Enemy creation uses a platform-aware spawn process.

Each enemy receives:

- Enemy type
- Spawn world X position
- Calculated spawn world Y position
- Independent collision box
- Independent sprite visual offset
- Movement direction
- Current state
- Question lock
- Collision cooldown
- Spawn reference data

The spawn system finds the supporting platform under an enemy spawn point and calculates the position using:

```text
enemy.y = platform.y - enemy.colliderHeight
```

This keeps each enemy’s collision box aligned with the platform surface while allowing the visual sprite to be positioned separately.

---

## Blockchain and NOXCAT Quiz System

Enemy encounters are part of the game’s educational mechanic.

### Contact Rules

- A precise descending top-down stomp defeats an enemy directly.
- Any other contact direction triggers a quiz.
- Side contact triggers a quiz.
- Bottom contact triggers a quiz.
- General overlapping contact triggers a quiz.
- The collision itself does not directly remove HP.

### Answer Rules

| Result | Outcome |
|---|---|
| Correct answer | Enemy is defeated, HP remains unchanged, score is awarded |
| Wrong answer | Player loses one HP and returns to the latest checkpoint |
| Top-down stomp | Enemy is defeated without opening a quiz |

### Question Categories

The question bank includes 30 multiple-choice questions covering:

- Blockchain fundamentals
- Distributed ledgers
- Decentralization
- Cryptocurrency
- Wallets
- Private keys
- Smart contracts
- Gas fees
- Tokens
- DeFi
- RWA
- NFT
- Multi-chain systems
- Public blockchain verification
- NOXCAT ecosystem concepts
- Arbitrum
- $NOX
- NOXCAT Wallet
- Social login
- UID
- MPC security
- NOXCAT Escrow
- Smart-contract-based settlement
- Social transfers
- Staking
- Governance
- Web3 usability

### Collision Protection

To prevent repeated questions or repeated damage:

- Every enemy has `questionLock`.
- Every enemy has `questionCooldown`.
- The player receives a short invulnerability period after damage.
- A question pauses gameplay by changing the game state to `quiz`.
- Collision events are only processed when the game state is `playing`.
- A player cannot lose multiple HP from a single enemy contact event.
- A defeated enemy is removed from future collision checks.

---

## Collectibles and Score

The main collectible is a Bitcoin-inspired energy token.

### Token Behavior

- Tokens float slightly over time.
- Tokens rotate visually.
- Each token adds score.
- Token collection creates particles and plays an original sound effect.

### Score Sources

| Action | Score |
|---|---:|
| Collect an energy token | +100 |
| Defeat an enemy by stomp | +200 |
| Answer a question correctly | +350 |
| Activate a NOX Beacon | +250 |
| Complete the level | +1000 |
| Remaining time | +10 per second |

---

## Health, Damage, and Checkpoints

The player begins with **3 HP**.

### Damage Sources

- Incorrect quiz answer
- Hazard platform contact
- Falling below the level

### NOX Beacon Checkpoints

Two NOX Beacon checkpoints are placed in the level.

When activated:

- The Beacon becomes visually active.
- The player’s respawn location is updated.
- The player receives a score reward.
- A checkpoint sound effect and particle effect are played.

If HP reaches zero, the game displays a **SYSTEM FAILURE** screen and offers a retry option.

---

## NOX CORE

The NOX CORE is the final mission objective.

When the player reaches the NOX CORE:

- The level ends successfully.
- The game displays **MISSION COMPLETE**.
- Completion score is awarded.
- Remaining time is converted into bonus score.
- The result panel displays time, score, energy, and combo information.

---

## Visual Style

The visual direction is built around the NOXCAT identity.

### Art Direction

- Original retro 16-bit-inspired pixel art
- Neon-green highlights
- Black, deep blue, dark steel, cyan, and purple technology palette
- Dark glass UI panels
- Cyber-city background
- Digital market chart atmosphere
- Futuristic ruins and technology platforms
- Clear pixel edges through Canvas image smoothing control

### Included Visual Assets

```text
NOXCAT player sprite sheet
BLOCK BOT and GLITCH BEETLE enemy sprite sheet
Bitcoin-inspired token image
Platform atlas
Cyber-city background
NOX-themed UI treatment
```

---

## Sprite and Collision Architecture

The project separates game physics from visual sprite rendering.

### Collision Box

Each entity uses world coordinates and collider dimensions:

```text
entity.x
entity.y
entity.w
entity.h
```

These values control gameplay behavior, platform collision, enemy contact, and player movement.

### Sprite Rendering

Visual sprites use source rectangles:

```text
sourceX
sourceY
sourceWidth
sourceHeight
destinationX
destinationY
destinationWidth
destinationHeight
```

This prevents the game from rendering an entire sprite sheet as one image.

### Atlas Management

Sprite source rectangles are centralized in:

```javascript
SPRITES
PLATFORM_SPRITES
```

This ensures that:

- Player frames use only the correct player frame.
- Enemy frames use only the correct enemy frame.
- Platform frames use only the correct platform image.
- Adjacent atlas frames do not appear in-game.
- Sprite offsets do not modify collision box positions.

---

## Audio System

The game uses original browser-generated Web Audio API sound effects.

### Sound Effects

- Jump
- Footsteps
- Token collection
- Enemy stomp
- Damage
- Checkpoint activation
- Mission completion
- Game over
- Correct answer feedback

### Music

The background music is a procedural chiptune-style loop created with Web Audio oscillators.

Audio begins after the player presses **START GAME**, which follows browser autoplay requirements.

---

## Controls

### Desktop

| Input | Action |
|---|---|
| `A` / `D` | Move left / right |
| `←` / `→` | Move left / right |
| `Space` | Jump |
| `W` | Jump |
| Second jump while airborne | Double jump |
| `F3` | Toggle debug overlay |

### Mobile

The game includes bottom-screen touch controls:

| Button | Action |
|---|---|
| `←` | Move left |
| `→` | Move right |
| `JUMP` | Jump / double jump |

Landscape orientation is recommended for mobile devices.

---

## User Interface

The UI is styled as a NOXCAT cyber system interface.

### HUD

The top HUD displays:

```text
NOXCAT
HP
ENERGY
SCORE
TIME
```

### Screens

The game includes:

- Start screen
- Controls prompt
- Quiz interface
- Mission complete screen
- System failure screen
- Restart button
- Mobile orientation prompt

---

## Project Structure

```text
NOXCAT-Digital-Abyss/
│
├─ index.html
├─ game.js
├─ style.css
├─ theme.css
├─ quiz.css
├─ OPEN_GAME.bat
├─ README.md
│
└─ assets/
   ├─ player/
   │  ├─ noxcat-spritesheet-source.png
   │  └─ noxcat-spritesheet-clean.png
   │
   ├─ enemies/
   │  ├─ nox-enemies-source.png
   │  └─ nox-enemies-clean.png
   │
   ├─ blocks/
   │  ├─ platform-atlas-source.png
   │  └─ platform-atlas-clean.png
   │
   ├─ background/
   │  └─ cyber-city-background.png
   │
   ├─ ui/
   │  └─ energy-token-clean.png
   │
   └─ audio/
```

---

## Run Locally

### Windows

Double-click:

```text
OPEN_GAME.bat
```

### Any Modern Browser

Open:

```text
index.html
```

Supported browsers include:

- Google Chrome
- Microsoft Edge
- Mozilla Firefox
- Safari

No Node.js installation is required.

---

## Customization

### Change the Time Limit

In `game.js`, locate:

```javascript
this.time = 180;
```

Change `180` to the desired number of seconds.

### Add Questions

Edit the `questions` collection in `game.js`.

Each question contains:

```javascript
{
  q: 'Question text',
  a: ['Answer A', 'Answer B', 'Answer C'],
  ok: 0
}
```

`ok` is the zero-based index of the correct answer.

### Add Platforms

Edit `Level.make()` in `game.js`.

Platform types include:

```text
stone
metal
pulse
energy
float
break
bounce
hazard
moving
```

### Add Enemies

Use the enemy spawn system inside the level definition.

Each enemy spawn calculates its vertical position from the platform beneath it, avoiding floating or ground clipping.

### Replace Assets

Replace images inside the relevant `assets/` folder.

When replacing an atlas or sprite sheet, update the corresponding source rectangle entries in:

```javascript
SPRITES
PLATFORM_SPRITES
```

---

## Debug Mode

Press `F3` during gameplay to enable the developer debug overlay.

Debug mode can display:

- Player collision box
- Enemy collision boxes
- Platform collision boxes
- Current game state
- Player HP
- Sprite debugging information

The browser Console also provides development logs:

```text
[EnemySpawn]
[EnemyCollision]
[Question]
[Answer]
[Damage]
[Enemy]
```

---

## Asset and IP Notice

NOXCAT-related branding and visual assets should only be used with the permission of the relevant IP owner.

This project’s game code, browser implementation, collision flow, quiz system, UI layout, platform logic, visual composition, and procedural audio are designed as an original standalone implementation.
