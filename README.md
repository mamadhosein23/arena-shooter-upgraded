# 🚀 2D Arena Shoote

A fast-paced, top-down 2D Arena Shooter built strictly with **Vanilla JavaScript** and the **HTML5 Canvas API**—zero external dependencies or runtime libraries.

---

## 🎮 Core Features & Mechanics

- **Delta-Time Driven Game Loop:** Decoupled physics update and rendering cycles utilizing `requestAnimationFrame`, ensuring consistent behavior regardless of monitor refresh rates.
- **Weapon Arsenal:**
  - `[1] Pistol`: Standard single-shot projectile weapon with infinite ammo.
  - `[2] Shotgun`: Multi-pellet spread attack (6 projectiles per shot).
  - `[3] Laser`: Instantaneous hitscan line-intersection raycasting with visual glow effects.
  - `[4] Rocket Launcher`: High-damage explosive projectile with Area-of-Effect (AoE) splash damage.
- **Enemy AI System:**
  - `Normal`: Standard pursuit behavior.
  - `Fast`: High mobility, low health pool.
  - `Tank`: Heavy health pool, high collision damage, slower movement.
  - `Bomber`: Charges the player and self-destructs upon proximity.
  - `Shooter`: Maintains distance and fires targeted projectiles.
- **Roguelite Wave & Upgrade Loop:** Cleared waves present three randomized stat upgrades (Max HP, Movement Speed, Fire Rate, Damage Multiplier, Bullet Velocity, Lifesteal chance, Cooldown Reduction).
- **VFX & Juice Engine:** Dynamic screen shake, decaying particle bursts, bullet trails, radial shockwave rings, and hit-flash states.
- **State Persistence:** Persistent high-score tracking using the browser's `localStorage`.

---

## 🕹 Controls

| Action | Key / Input |
| :--- | :--- |
| **Movement** | `W`, `A`, `S`, `D` |
| **Aim** | `Mouse Cursor` |
| **Fire** | `Left Click` (Hold to auto-fire) |
| **Select Weapon** | `1`, `2`, `3`, `4` |
| **Choose Upgrade** | `1`, `2`, `3` or `Mouse Click` on card |
| **Pause / Resume** | `Escape` |
| **Restart Game** | `R` or `Left Click` (on Game Over screen) |

---

## 🛠 Technical Architecture

The single-file architecture (`index.html`) is structured into distinct modules:

1. **Setup & Viewport Management:** Dynamic canvas resizing and resolution scaling.
2. **Input State Manager:** Discrete tracking of active keymaps and continuous mouse coordinate polling.
3. **Collision Detection Math:**
   - *Circle-to-Circle Collision:* Distance vector calculations using squared Euclidean norms.
   - *Raycast/Segment Collision:* Point-to-line segment projection for instant laser hits.
4. **Entity Lifecycle & Memory Cleanup:** Array compaction and memory garbage mitigation for particles, lasers, floaters, and expired bullet entities.

---

## 🚀 Getting Started

No build tools, bundlers, or package managers required.

1. Clone or download the repository.
2. Open `index.html` directly in any modern web browser (or serve it via the **Live Server** extension in VS Code).
