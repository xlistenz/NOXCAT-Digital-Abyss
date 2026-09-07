# NOXCAT-Digital-Abyss

## Problem & Goal

NOXCAT-Digital-Abyss turns blockchain and NOXCAT ecosystem knowledge into an interactive pixel-platform experience. It is designed for players who are new to Web3, wallets, and digital assets, making complex concepts easier to explore through gameplay.

## Core Features

- 2D side-scrolling gameplay with movement, double jump, hazards, checkpoints, and moving platforms.
- Enemy encounters trigger blockchain and NOXCAT multiple-choice questions.
- Correct answers defeat enemies without damage; wrong answers reduce HP.
- Browser-based gameplay with keyboard, mobile touch controls, score, timer, and Web Audio sound.

## System Architecture

```text
Player Browser
│
├─ HTML / CSS Interface
├─ JavaScript Game Loop
│  ├─ Canvas Rendering
│  ├─ Player Physics and Collision
│  ├─ Platform and Enemy Systems
│  ├─ Quiz and HP Logic
│  ├─ Camera, Score, Timer, UI
│  └─ Web Audio Sound and Music
│
└─ Local Assets
   ├─ Player and Enemy Sprites
   ├─ Platform Atlas
   ├─ Background Art
   └─ Token and UI Assets
```

This project is a static frontend game. It has no backend, database, AI model, login system, or external API. Questions, levels, and game logic are stored locally in the project.

## Technologies Used

| Category | Technology / Service | Purpose |
| --- | --- | --- |
| AI Model | None | No AI model is used at runtime |
| Frontend | HTML5, CSS3, JavaScript, Canvas API | Game rendering, UI, input, collision |
| Audio | Web Audio API | Original sound effects and chiptune-style music |
| Backend | None | Static browser game |
| Database | None | Questions and level data are stored in `game.js` |
| Sponsor Technology | NOXCAT / Web3 knowledge content | Quiz topics and game world concept |

## Installation & Run

```bash
# Clone the repository
git clone https://github.com/xlistenz/NOXCAT-Digital-Abyss.git

# Enter the project directory
cd NOXCAT-Digital-Abyss

# Open index.html in a modern browser
# Or double-click OPEN_GAME.bat on Windows

# Optional local server
python -m http.server 8000
```

No Node.js setup, database, account, API key, or backend service is required.

## Demo

- Project URL: 
https://noxcat-minigame.netlify.app/
- Demo video: 
https://www.youtube.com/watch?v=nviSa3RCRCw

## Limitations & Future Work

- The current quiz bank contains 30 built-in questions.
- The game currently includes one playable level.
- There is no online leaderboard, account system, or blockchain reward integration.
- Mobile gameplay is optimized for landscape orientation.
- Future work may include multiple levels, boss encounters, multilingual support, dynamic quiz management, leaderboard support, and optional on-chain achievements.

## Third-Party Services, Data & Assets

| Item | Source | License / Usage |
| --- | --- | --- |
| NOXCAT character and branding assets | Project-provided assets | Used only with permission from the applicable IP owner |
| Enemy, platform, background, and token artwork | Project-provided assets | Used for this project demonstration |
| Canvas API | Native browser API | Rendering and animation |
| Web Audio API | Native browser API | Original procedural sound and music |

No API keys, tokens, wallet private keys, personal data, or sensitive credentials are included in this repository.

## Team Members

- | Name | Responsibility |
- |官承逸|Game design|development|asset integration|
- |吳亮廷|quiz content|Game design|development|asset integration|
- |王雍(warren)||github support|


## License

This project is licensed under the [MIT License](LICENSE).
