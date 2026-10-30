# <p align="center">⚡ ARENA SHOOTER UPGRADED ⚡</p>

<p align="center">
  <strong>A high-performance, deterministic 2D top-down arena shooter engineered from scratch with pure Vanilla JavaScript (ES6+) and HTML5 Canvas API. Zero external dependencies. Zero build step overhead. Maximum frame budget.</strong>
</p>

<p align="center">
  <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript"><img src="https://img.shields.io/badge/Language-Vanilla%20ES6%2B-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript" /></a>
  <a href="https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API"><img src="https://img.shields.io/badge/Graphics-Canvas%202D%20Hardware-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="Canvas" /></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-00F0FF?style=for-the-badge" alt="License" /></a>
  <img src="https://img.shields.io/badge/Dependencies-0%20(Pure%20Web%20Primitives)-brightgreen?style=for-the-badge" alt="Zero Dependencies" />
  <img src="https://img.shields.io/badge/Frame%20Rate-Locked%2060%2B%20FPS-purple?style=for-the-badge" alt="60 FPS Locked" />
</p>

<p align="center">
  <a href="#-overview--philosophy">Overview</a> •
  <a href="#-core-features--mechanics">Core Features</a> •
  <a href="#-weapon-arsenal--tactical-breakdown">Arsenal</a> •
  <a href="#-enemy-ai-taxonomy">Enemy AI</a> •
  <a href="#-controls--input-mapping">Controls</a> •
  <a href="#-technical-architecture--deep-dive">Technical Architecture</a> •
  <a href="#-getting-started--installation">Getting Started</a> •
  <a href="#-license">License</a>
</p>

---

## 🧭 Overview & Philosophy

**Arena Shooter Upgraded** is an arcade-style, top-down survival combat engine built to demonstrate low-level browser game development without abstractions, bundlers, or third-party engines (such as Phaser, PixiJS, or Three.js).

The project implements a deterministic, frame-rate-independent physics loop, continuous collision detection (CCD) for high-velocity bodies, in-place zero-allocation memory compaction, and a diegetic cyberpunk HUD accelerated entirely via GPU compositing layers.
┌─────────────────────────────────────────────────────────────┐

│ [HUD] GPU Layer: Data-Driven CSS Tokens (–sys-hue) │

├─────────────────────────────────────────────────────────────┤

│ [CANVAS] Render Pipeline (Sub-pixel DPI Scaled Context) │

│ ├── Swept Time-of-Impact (ToI) Continuous Collisions │

│ ├── Multi-Plane Sliding, Restitution & Friction Physics │

│ ├── Parametric Hitscan Raycasting & Splash Damage AoE │

│ └── Zero-Allocation In-Place Compaction Memory Pipeline │

└─────────────────────────────────────────────────────────────┘

text

---

## 🎮 Core Features & Mechanics

### 🧬 Roguelite Wave & Progression Loop
Wave completion halts active spawns and prompts an immediate randomized selection from three upgrade cards:
- **Max Health Surge:** Expands current and maximum health pool thresholds.
- **Traversal Velocity:** Scales linear player movement vectors without inertia penalty.
- **Cyclic Fire Rate:** Reduces inter-shot weapon cooldown delays.
- **Damage Multiplier:** Applies global scalar modifiers to bullet and explosive damage.
- **Muzzle Velocity:** Accelerates travel speeds of physical projectile instances.
- **Vampiric Lifesteal:** Probabilistically siphons health points on registered enemy hits.
- **Cooldown Optimization:** Accelerates trigger resets across all weapon classes.

### 💥 Juice & Visual Effects (VFX) Engine
- **Decoupled Viewport Screen Shake:** Bidirectional translational impulse with smooth exponential decay.
- **Debris & Spark Particle Systems:** Directional velocity cones with alpha fading and friction damping.
- **Entity Hit-Flash Shader Emulation:** Instantaneous monochrome/luminance inversion during damage frames.
- **Expanding Radial Shockwaves:** Quadratic falloff shock rings for explosive payload feedback.
- **Persistent High-Score Storage:** Synchronous state serialization using browser `localStorage`.

---

## 🔫 Weapon Arsenal & Tactical Breakdown

| ID | Weapon Class | Trajectory Profile | Damage Mechanism | Tactical Use Case |
| :---: | :--- | :--- | :--- | :--- |
| **[1]** | **Kinetic Pistol** | Linear ballistic projectile | Single-target kinetic impact | Semi-automatic sidearm with unlimited ammo and zero dispersion. |
| **[2]** | **Tactical Shotgun** | 6-pellet conical distribution | Multi-projectile spread with knockback | Close-quarters crowd dispersal with high momentary stopping power. |
| **[3]** | **Hitscan Laser** | Instantaneous parametric line | Ray-segment intersection | Pinpoint long-range engagement bypassing projectile flight times. |
| **[4]** | **Rocket Launcher** | Accelerated self-propelled missile | Proximity detonation with radial AoE | High-value target destruction and dense cluster clearance. |

---

## 👾 Enemy AI Taxonomy

Each enemy type is driven by discrete behavioral routines updated per simulation step:

- **`Normal`:** Employs direct Euclidean vector tracking to close distance with the player entity.
- **`Fast`:** High-velocity, low-inertia skirmisher designed to flank and punish static positioning.
- **`Tank`:** Heavy mass profile, extreme health pool, and high collision impulse at reduced movement speeds.
- **`Bomber`:** Aggressive proximity-fused rusher that executes high-yield explosive self-detonation on target contact.
- **`Shooter`:** Maintains calculated standoff distance (kiting) and discharges targeted ballistic projectiles.

---

## 🕹 Controls & Input Mapping

| Action | Input Vector | Description |
| :--- | :--- | :--- |
| **Movement** | <kbd>W</kbd> <kbd>A</kbd> <kbd>S</kbd> <kbd>D</kbd> | 8-directional kinematic player translation |
| **Aiming** | `Mouse Cursor` | Continuous heading vector calculation |
| **Primary Fire** | `Left Click` (Hold) | Continuous trigger engagement for active weapon |
| **Switch Weapon** | <kbd>1</kbd> <kbd>2</kbd> <kbd>3</kbd> <kbd>4</kbd> | Instantaneous arsenal hot-swapping |
| **Select Upgrade** | <kbd>1</kbd> <kbd>2</kbd> <kbd>3</kbd> or `Click` | Commits selected wave progression card |
| **Pause / Resume** | <kbd>Esc</kbd> | Halts canvas loop and suspends delta-time accumulation |
| **Restart Session** | <kbd>R</kbd> or `Click` | Soft-reinitializes game state on Game Over overlay |

---

## ⚙ Technical Architecture & Deep Dive
arena-shooter-upgraded/

├── index.html → Canvas container, HUD markup, and viewport configuration

├── style.css → GPU-accelerated cyberpunk HUD and diegetic overlay rules

└── src/

├── engine.js → Decoupled delta-time accumulator & requestAnimationFrame loop

├── ccd.js → Swept circle-cast collision engine with multi-plane sliding

├── physics.js → Vector math, friction, restitution, and hitscan projections

├── entities.js → Entity lifecycle, particle pools, and in-place array compaction

└── ui.js → CSS custom property bridge for data-driven HUD updates

text

### 1. Swept Continuous Collision Detection (CCD) & Sliding Physics
Fast-moving projectiles and dynamic entities bypass discrete bounding-box checks to prevent high-velocity tunneling through geometry. The engine calculates an exact **Time-of-Impact (ToI)** using swept circle casting:
- Determines normalized contact time $t \in [0, 1]$ along displacement vectors $(dx, dy)$.
- Applies collision normal decomposition with integrated skin offset margins ($\text{skin} = 0.01$) to eliminate corner snagging and floating-point surface oscillation.
- Supports multi-plane tangent sliding, projecting remaining velocity vectors onto collision tangent planes across iterative iterations ($k_{\max} = 4$).

### 2. Squared Euclidean Distance Optimization
All proximity calculations, collision broadphases, and radial explosion falloffs avoid expensive square-root operations:
$$\Delta x^2 + \Delta y^2 < (r_1 + r_2)^2$$
By evaluating squared Euclidean norms directly, CPU cycles remain unburdened inside dense iteration passes.

### 3. In-Place Zero-Allocation Array Compaction
To eliminate garbage collector (GC) pauses during intense waves containing hundreds of active particle and bullet instances, the engine avoids `Array.prototype.splice` and `Array.prototype.filter`.
- Expired entities are marked for deletion and overwritten in $O(1)$ time by swapping them with the tail element of the array.
- Truncating array length directly prevents heap churn and memory fragmentation.

### 4. GPU-Accelerated Diegetic UI Architecture
The user interface is entirely decoupled from Canvas 2D render context updates:
- Panels utilize browser containment primitives (`contain: strict; will-change: transform;`) to isolate layout and paint calculations.
- Game states dynamically stream changes through reactive CSS Custom Properties (`--sys-hue`, `--progress`) bound to `data-status` selectors, delegating transitions and terminal glitches directly to the GPU compositor thread.

### 5. High-DPI Canvas & Coordinate Normalization
Canvas rendering automatically scales by `window.devicePixelRatio`, keeping lines, fonts, and particle trails sharp across 4K and Retina displays while preserving consistent logical simulation coordinates.

---

## 🚀 Getting Started & Installation

No build steps, node environments, or package managers required.

### 1. Clone the Repository
```bash
git clone https://github.com/mamadhosein23/arena-shooter-upgraded.git
cd arena-shooter-upgraded
2. Run the Game
Open index.html directly in any modern browser:

macOS:
bash
  open index.html
  
Linux:
bash
  xdg-open index.html
  
Windows:
bash
  start index.html
  
Or serve locally with any static web server:

bash
# Node.js
npx serve .

# Python 3
python3 -m http.server 8080
📄 License
Distributed under the MIT License. See LICENSE for full details.

<p align=“center”>

<sub>Architected with precision by <a href=“https://github.com/mamadhosein23”>Mohammad Hossein</a>.</sub>

</p>
