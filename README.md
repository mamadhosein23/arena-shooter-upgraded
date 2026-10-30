🚀 2D Arena Shooter






A fast-paced, top-down arena shooter built with Vanilla JavaScript and the HTML5 Canvas API. Fight through enemy waves, switch between weapons, and choose upgrades as you progress.

The game requires no build tools, package managers, or runtime libraries. Optional web fonts may be loaded by the stylesheet; system fonts are used as fallbacks.

🎮 Features
Combat and weapons
Pistol: Reliable single-shot weapon with unlimited ammo.
Shotgun: Fires six projectiles in a spread.
Laser: Hitscan attack with line-based target detection and visual effects.
Rocket Launcher: Fires explosive projectiles that deal area-of-effect damage.
Enemy types
Normal: Pursues the player at a standard pace.
Fast: Moves quickly but has less health.
Tank: Has a large health pool and deals more collision damage, but moves slowly.
Bomber: Charges the player and detonates at close range.
Shooter: Keeps its distance and fires projectiles at the player.
Waves and upgrades
Survive each wave to choose from three randomized upgrades, including increased max health, movement speed, fire rate, damage, bullet velocity, lifesteal chance, and reduced cooldowns.

Visual effects and interface
Screen shake, particle bursts, bullet trails, shockwave rings, and hit flashes.
A futuristic HUD with progress bars, status indicators, and themeable accent colors.
High scores saved locally in the browser using localStorage.
🕹 Controls

Action	Input
Move	W, A, S, D
Aim	Mouse cursor
Fire	Hold left mouse button
Select weapon	1, 2, 3, 4
Choose an upgrade	1, 2, 3 or click an upgrade card
Pause / resume	Escape
Restart after game over	R or click the game-over screen
🛠 Technical Overview
The game uses a lightweight browser-based architecture:

Canvas and viewport: Resizes the canvas to fit the viewport and accounts for display pixel ratio.
Input handling: Tracks keyboard state and mouse position for movement, aiming, and firing.
Collision detection:
Circle-to-circle checks use squared distances to avoid unnecessary square-root calculations.
Laser attacks use line-segment intersection checks.
Entity lifecycle: Removes expired projectiles and visual effects to keep active game objects manageable.
Game loop: Uses requestAnimationFrame and elapsed time to update and render the game.
🚀 Getting Started
No installation or build step is required.

bash
git clone https://github.com/mamadhosein23/arena-shooter-upgraded.git
cd arena-shooter-upgraded
Open index.html in a modern browser to play.
