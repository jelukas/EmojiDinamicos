# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an interactive web application that simulates emoji particles with physics. The project consists of two HTML files with embedded CSS and JavaScript, with no external dependencies or build process.

## File Structure

- **index.html**: Landing page with game description, instructions, and play button
- **game.html**: The main game application with physics simulation

## Architecture

**Landing Page (index.html)**: Static welcome page featuring:
- Game title and description
- Preview of game features (interactive, physics effects, explosions, gravity)
- Detailed controls instructions
- Play button linking to game.html

**Game Application (game.html)**: The entire physics simulation is contained in this file:
- **HTML**: Canvas element and control UI
- **CSS**: Inline styles using gradient background and control panel overlays
- **JavaScript**: Vanilla JS with no frameworks

**Physics Engine**: Custom particle system implemented in the `Particle` class (game.html:98-196):
- Gravity simulation with configurable on/off state
- Velocity-based movement with friction
- Edge collision detection with bounce physics
- Particle-to-particle collision detection and response
- Mouse interaction system (attraction when mouse is pressed and dragged)

**Key Systems**:
1. **Particle Management** (game.html:94): Array-based particle storage
2. **Mouse State** (game.html:95): Tracks position and drag state for vortex effect
3. **Animation Loop** (game.html:228-237): RequestAnimationFrame-based rendering
4. **Event Handlers** (game.html:240-262): Canvas mouse events and window resize

## Running the Application

Simply open `index.html` in a web browser:
- **Windows**: `start index.html`
- **Mac/Linux**: `open index.html` or `xdg-open index.html`

No build process, dev server, or dependencies required.

## Development

**Testing Changes**:
- Landing page: Refresh the browser after editing `index.html`
- Game: Refresh the browser after editing `game.html`

**Key Constants to Modify** (in game.html):
- Emoji array (game.html:91-92): Add/remove emoji characters
- Initial particle count (game.html:265): Change number of emojis on load
- Physics parameters in Particle constructor (game.html:108-110):
  - `gravity`: Downward acceleration (default 0.3)
  - `bounce`: Energy retention on collision (default 0.7)
  - `friction`: Velocity decay per frame (default 0.99)

**Interactive Features**:
- Click canvas to spawn emoji at cursor
- Press and drag to create attraction vortex
- Control panel buttons for bulk operations (add, clear, toggle gravity, explosion)

## Code Structure Notes

The codebase uses a class-based particle system where each `Particle` instance:
- Maintains position (x, y) and velocity (vx, vy)
- Updates physics state each frame in `update()` method
- Renders itself with rotation in `draw()` method
- Handles collision detection with both edges and other particles

Mouse interaction creates force field within 200px radius (game.html:125) that attracts particles toward cursor when mouse button is held down.
