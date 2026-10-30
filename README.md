# <p align="center">⚡ ARENA SHOOTER UPGRADED ⚡</p>

<p align="center">
  <strong>A high-performance, deterministic 2D top-down arena shooter engineered from scratch with pure Vanilla JavaScript (ES6+) and HTML5 Canvas API. Zero dependencies. Zero bloat. Maximum frame rate.</strong>
</p>

<p align="center">
  <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript"><img src="https://img.shields.io/badge/Language-ES6%2B%20Vanilla-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript" /></a>
  <a href="https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API"><img src="https://img.shields.io/badge/Graphics-Canvas%202D%20Hardware-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="Canvas" /></a>
  <a href="https://github.com/mamadhosein23/arena-shooter-upgraded/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-00F0FF?style=for-the-badge" alt="License" /></a>
  <img src="https://img.shields.io/badge/Dependencies-0%20(Zero%20Libs)-brightgreen?style=for-the-badge" alt="Zero Dependencies" />
  <img src="https://img.shields.io/badge/Performance-60%2B%20FPS%20Locked-purple?style=for-the-badge" alt="60 FPS" />
</p>

<p align="center">
  <a href="#-overview--philosophy">Overview</a> •
  <a href="#-core-features--mechanics">Features</a> •
  <a href="#-arsenal--tactical-breakdown">Arsenal</a> •
  <a href="#-enemy-ai-taxonomy">AI Taxonomy</a> •
  <a href="#-controls--input-mapping">Controls</a> •
  <a href="#-technical-architecture--deep-dive">Architecture</a> •
  <a href="#-getting-started">Getting Started</a> •
  <a href="#-license">License</a>
</p>

---

## 🧭 Overview & Philosophy

**Arena Shooter Upgraded** is an arcade-style, top-down survival game designed to showcase bare-metal browser game development. Eschewing heavy external frameworks (like Phaser or Three.js) or bundling pipelines, this engine manages everything natively: from swept time-of-impact collision detection to hardware-accelerated diegetic UI composition.

The engine relies on a **decoupled fixed/variable step architecture**, ensuring physics determinism, frame-independent movement trajectories, and minimal garbage collection overhead across high-refresh-rate displays.

---

## 🎮 Core Features & Mechanics

### 🧬 Roguelite Wave & Upgrades System
Upon clearing sequential arena waves, gameplay pauses to present a randomized draft of upgrade modifiers:
- **Max HP Boost:** Expands survivability thresholds.
- **Velocity Factor:** Enhances vector displacement rates.
- **Fire Rate Tuning:** Decreases inter-shot weapon cooldown delays.
- **Damage Multiplier:** Scales global offensive output.
- **Bullet Velocity:** Speeds up projectile traversal vectors.
- **Lifesteal Chance:** Grants probabilistic health recovery on enemy impact.
- **Cooldown Reduction:** Accelerates secondary ability availability.

### 💥 Juice & Visual Effects (VFX) Engine
- **Dynamic Screen Shake:** Vector-offset viewport translation decaying over time.
- **Particle Burst System:** Pool-allocated decaying velocity sparks on entity collisions.
- **Hit-Flash States:** Immediate canvas tint shifts upon damage registration.
- **Radial Shockwave Rings:** Expanding ring primitives illustrating AoE detonations.

---

## 🔫 Arsenal & Tactical Breakdown

| Weapon ID | Designation | Operational Profile |
| :---: | :--- | :larship |
| **[1]** | **Kinetic Pistol** | Semi-automatic sidearm featuring infinite ammunition, baseline spread, and predictable recoil pacing. |
| **[2]** | **Tactical Shotgun** | Disperses 6 convergent pellets in a conical distribution pattern with high short-range impulse knockback. |
| **[3]** | **Hitscan Laser** | Instantaneous line-segment raycasting intersecting target geometry with bloom rendering effects. |
| **[4]** | **Rocket Launcher** | High-mass ballistic projectile featuring proximity detonation and Area-of-Effect (AoE) splash damage falloff. |

---

## 👾 Enemy AI Taxonomy

- **`Normal`:** Employs standard Euclidean vector pursuit to close distance with the player entity.
- **`Fast`:** High-velocity, low-mass flanker designed to overwhelm positioning and corner maneuvers.
- **`Tank`:** Substantial health pool, high collision mass, and heavy knockdown resistance at reduced traversal speeds.
- **`Bomber`:** Aggressive proximity-fused rusher that executes self-detonation upon entering critical contact radius.
- **`Shooter`:** Maintains tactical standoff range while continuously calculating and firing targeted projectiles.

---

## 🕹 Controls & Input Mapping

| Action Category | Input Vector | Description |
| :--- | :--- | :--- |
| **Translation** | <kbd>W</kbd> <kbd>A</kbd> <kbd>S</kbd> <kbd>D</kbd> | Orthogonal player movement controls. |
| **Orientation** | `Mouse Cursor` | Rotates player heading vector toward pointer coordinates. |
| **Primary Fire** | `Left Click` (Hold) | Continuous engagement of selected weapon system. |
| **Weapon Selection**| <kbd>1</kbd> <kbd>2</kbd> <kbd>3</kbd> <kbd>4</kbd> | Instantaneous hot-switching between arsenal slots. |
| **Upgrade Selection**| <kbd>1</kbd> <kbd>2</kbd> <kbd>3</kbd> or `Click` | Selects roguelite wave progression reward. |
| **Simulation State**| <kbd>Esc</kbd> | Toggles game pause/resume loops. |
| **Session Reset** | <kbd>R</kbd> or `Click` | Reinitializes game session from Game Over overlay. |

---

## ⚙ Technical Architecture & Deep Dive
