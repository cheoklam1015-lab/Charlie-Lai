# AGENTS.md - Repository Guide for Agentic Coders

## Project Overview
This is a collection of HTML5 web games written in vanilla JavaScript, HTML, and CSS. The repository contains three main games:
- Snake Game (game1.html) - Infinite wall-through snake game
- Bingo Number Guessing Game (game2.html) - 4-digit number guessing logic game  
- Sudoku Game (game3.html) - Classic Sudoku with difficulty levels

**Key Characteristics:**
- Pure vanilla JavaScript (no frameworks, no build tools)
- Mobile-responsive design with touch controls
- Chinese Traditional (zh-TW) interface
- Self-contained single-file games
- Local storage for game statistics

---

## Development Commands

### No Build System
This repository uses static HTML files - **no compilation, bundling, or build process required**.

### Local Development
```bash
# Start a local server (recommended)
python -m http.server 8000
# OR
npx serve .
# OR
live-server

# Open games in browser
# Navigate to http://localhost:8000
# - index.html (game selection menu)
# - game1.html (Snake Game)
# - game2.html (Bingo Number Game) 
# - game3.html (Sudoku Game)
```

### Testing
```bash
# No automated tests configured
# Manual testing required:
# 1. Open each game in different browsers
# 2. Test mobile responsiveness (use browser dev tools)
# 3. Test game functionality and controls
# 4. Verify local storage persistence
```

### Linting/Validation
```bash
# HTML validation
npx html-validate *.html

# JavaScript linting (optional)
npx eslint *.js --ext .html

# CSS validation
npx stylelint *.css
```

---

## Code Style Guidelines

### HTML Structure
- Use semantic HTML5 elements (`<header>`, `<main>`, `<section>`, `<nav>`)
- Include `lang="zh-TW"` for Chinese Traditional content
- Set proper viewport meta tag for mobile responsiveness
- Use consistent DOCTYPE (`<!DOCTYPE html>`)
- Structure games in: Header → Game Controls → Game Area → Instructions/Footer

### CSS Architecture
- Use CSS custom properties (`--primary-color`, `--accent-color`) for theming
- Follow mobile-first responsive design with `@media` queries
- Use CSS Grid for game layouts, Flexbox for UI components
- Organize styles with clear section comments
- Include hover/active states for interactive elements
- Use CSS animations for game effects (transitions, keyframes)

### JavaScript Conventions
- Use `const`/`let` instead of `var`
- Organize code with clear section comments: `--- SECTION NAME ---`
- Use camelCase for variables, PascalCase for functions/classes
- Use semantic function names (`initGame()`, `handleClick()`, `validateInput()`)
- Store DOM element references in objects (`const UI = { ... }`)
- Use event delegation for dynamic content
- Implement proper game state management (`STATE` object)

### Naming Conventions
- Files: kebab-case (`game-controls.css`, `snake-game.js`)
- Functions: camelCase with descriptive names (`generateSudoku()`, `checkWin()`)
- Variables: camelCase, meaningful names (`timerInterval`, `selectedCell`)
- Constants: UPPER_SNAKE_CASE (`GRID_SIZE`, `MAX_ATTEMPTS`)
- CSS classes: kebab-case (`.game-container`, `.sudoku-cell`)
- HTML IDs: camelCase (`gameCanvas`, `submitBtn`)

### Error Handling
- Validate user inputs with visual feedback (shake animations, error states)
- Use try-catch for localStorage operations
- Provide fallback values for missing data
- Log debug information to console (`console.log("Debug: ...")`)
- Show user-friendly error messages in UI (message boxes, overlays)

### Mobile/Touch Support
- Include touch event handlers (`touchstart`, `touchmove`)
- Use `-webkit-tap-highlight-color: transparent` for clean touch
- Implement responsive breakpoints at common screen sizes (480px, 768px, 900px)
- Add mobile-specific controls (D-pad for games)
- Use viewport meta tag to prevent zoom on mobile games

### Performance Guidelines
- Use `requestAnimationFrame` for smooth animations
- Debounce expensive operations (resize events, canvas redraws)
- Minimize DOM queries by caching elements in variables
- Use CSS transforms instead of changing top/left properties
- Implement lazy loading for game assets if needed
- Clean up event listeners in single-page applications

### Localization
- Interface text uses Traditional Chinese (zh-TW)
- Keep language strings separate from logic when possible
- Test with Chinese character rendering on different browsers
- Consider CSS `font-family` stacks that include Chinese fonts

---

## File Structure Pattern
```
index.html              # Game selection menu
game1.html              # Snake Game
game2.html              # Bingo Number Game  
game3.html              # Sudoku Game
AGENTS.md               # This file
```

Each game file contains:
1. HTML structure with semantic elements
2. Internal CSS with mobile-first responsive design
3. Vanilla JavaScript with game logic
4. External dependencies via CDN (Font Awesome icons only)

---

## Browser Compatibility
- Target modern browsers (Chrome 80+, Firefox 75+, Safari 13+)
- Use standard web APIs (localStorage, canvas, CSS Grid)
- Provide fallbacks for older browsers when necessary
- Test on both desktop and mobile devices
- Verify touch/mouse interactions work correctly

---

## Game-Specific Notes

### Snake Game (game1.html)
- Uses HTML5 Canvas for rendering
- Implements collision detection and wall-through mechanics
- Features speed progression and high score tracking
- Supports both keyboard (arrows/WASD) and touch controls

### Bingo Number Game (game2.html)  
- Logic-based number guessing with A/B feedback system
- Includes timer and attempt tracking
- Uses animations for user feedback (shake, slide-in)
- Responsive grid layout for game history

### Sudoku Game (game3.html)
- CSS Grid-based 9x9 game board
- Implements Sudoku validation algorithm
- Features difficulty levels and hint system
- Includes cell highlighting and number conflicts detection