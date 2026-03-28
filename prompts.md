# Starter Prompts – GitHub Copilot Snake Game Challenge

These are **starting points**, not answers. Read each response carefully, discuss as a team, and refine the prompt based on what you get back. The teams that iterate will always score higher than teams that accept the first response.

> **How to use this file:** Find the prompt for your current phase and step. Use it as your opening message to Copilot — then improve it.

---

## Phase 1 – Research (Copilot Chat Mode)
### Starter Prompt

```
I'm going to build a Snake game using HTML canvas and vanilla JavaScript.
Before I write any code, help me understand the key components I'll need to build.
For each component, briefly explain what it does and why it matters.
```

### Follow-up ideas (choose one to explore deeper)

- "How does collision detection work in a grid-based game like Snake?"
- "What's the best data structure to represent the snake's body, and why?"
- "Should I use setInterval or requestAnimationFrame for the game loop — what are the trade-offs?"
---


## Phase 2 – Design (Copilot Plan Mode)

### Starter Prompt

```
Create a step-by-step implementation plan for a Snake game using HTML canvas
and vanilla JavaScript.

The implementation will live inside a single <script> tag in an existing
snake.html file that already has:
  - A 400x400 canvas element with id="gameCanvas"
  - A score display element with id="score"
  - The canvas context already retrieved as: const ctx = canvas.getContext('2d')

Break the work into exactly 4 steps matching these TODOs already in the file:
  1. Game constants and variables
  2. Keyboard event listeners
  3. Main game loop function
  4. Starting the game loop

For each step, describe what needs to be implemented and any important
considerations (edge cases, gotchas, design decisions).
```

---

## Phase 3 – Build (Copilot Agent Mode)

> Work through these **one at a time**. Wait for each step to be implemented and tested before moving to the next. Do NOT send all 4 at once.

### Step 1 – Game Variables

```
In snake.html, inside the <script> tag under the comment
"TODO – PHASE 3, STEP 1", add the game constants and variables.

Include:
- GRID_SIZE: the pixel size of each tile (20px, giving a 20x20 grid on 400px canvas)
- TILE_COUNT: number of tiles across (400 / GRID_SIZE)
- snake: an array of {x, y} objects. Start with 3 segments in the centre of the grid, moving right
- food: an {x, y} object placed at a random grid position
- dx and dy: direction variables (start moving right: dx=1, dy=0)
- score: a number initialised to 0
- gameLoop: a variable to hold the setInterval reference (initialise to null)

Do not add any functions yet — just the variables and constants.
```

### Step 2 – Keyboard Controls

```
Under the comment "TODO – PHASE 3, STEP 2" in snake.html, add a keydown
event listener on the document that changes dx and dy based on arrow key presses.

Requirements:
- ArrowUp    → dy = -1, dx = 0  (only if not currently moving down)
- ArrowDown  → dy = 1,  dx = 0  (only if not currently moving up)
- ArrowLeft  → dx = -1, dy = 0  (only if not currently moving right)
- ArrowRight → dx = 1,  dy = 0  (only if not currently moving left)
- No other keys should have any effect
- The snake must not be able to reverse directly into itself
```

### Step 3 – Game Loop Function

```
Under the comment "TODO – PHASE 3, STEP 3" in snake.html, create a function
called gameStep().

It must do the following in order:
1. Calculate the new head position: { x: snake[0].x + dx, y: snake[0].y + dy }
2. Check for wall collision (x < 0, x >= TILE_COUNT, y < 0, y >= TILE_COUNT)
   → if so, call gameOver()
3. Check for self-collision (new head x,y matches any existing snake segment)
   → if so, call gameOver()
4. Add the new head to the FRONT of the snake array (unshift)
5. If new head matches food position:
   - increment score
   - update scoreEl.textContent to the new score
   - place food at a new random grid position (not on the snake)
   - do NOT remove the tail (snake grows)
6. If food was NOT eaten: remove the last element of the snake array (pop)
7. Clear the entire canvas
8. Draw each snake segment as a filled rectangle (GRID_SIZE × GRID_SIZE, 1px inset for grid gap)
   Use a different colour for the head segment (index 0) vs the body
9. Draw the food as a filled circle centred on its tile

Also create a gameOver() function placeholder that stops the gameLoop interval.
```

### Step 4 – Start the Game

```
Under the comment "TODO – PHASE 3, STEP 4" in snake.html, start the game:
  gameLoop = setInterval(gameStep, 150);

Then open snake.html in a browser (right-click → Open with Live Server, or
just open the file directly) and test it.

If anything is broken or not working as expected, use /fix in Copilot Agent
and describe exactly what you observe. For example:
  "/fix The game starts but the snake is invisible — nothing is drawn on the canvas"
```

---

## Phase 4 – Refine (Copilot Agent Mode)

Pick **at least 2** of the following. Be specific in your prompts — describe exactly what you want, including visual details and behaviour edge cases.

---

### Game Over Screen

```
Replace the placeholder gameOver() function with a fully working one that:
- Clears the gameLoop interval so the game stops
- Draws a semi-transparent dark overlay across the entire canvas
- Renders "GAME OVER" in large text, centred on the canvas
- Renders the final score below it
- Renders "Press SPACE to restart" below that
- Adds a keydown listener for the Space key that resets all game variables
  (snake, food, score, direction) and restarts the game loop
```

### Speed Increase

```
Make the snake speed up as the score increases.
- Start at an interval of 150ms
- Every time the score increases by 3 points, reduce the interval by 15ms
- Minimum interval: 60ms (don't go faster than this)
- Clear the old interval and start a new one with the updated speed
  each time the interval changes
```

### High Score with localStorage

```
Add a high score feature:
- Add a "HIGH: 0" display next to the current score display in the HTML
- On page load, read the high score from localStorage (key: 'snakeHighScore')
  and display it
- When gameOver() is called, compare the current score to the high score
- If current score is higher: update the display and save to localStorage
- The high score should survive page refreshes
```

### Visual Polish

```
Improve the visual style of the game canvas:
- Draw a subtle grid pattern on the canvas background (alternating dark tiles)
- Draw snake segments with slightly rounded corners (use ctx.roundRect or
  manual arc-corner technique)
- Draw the food as a glowing circle (use a radial gradient instead of solid fill)
- Add a brief white flash effect on the head tile when food is eaten
```

### Walls-Off Wrap Mode

```
Add a toggle for "walls on" vs "walls off" mode:
- Add a button above the canvas labelled "Mode: Walls ON"
- When clicked, toggle between walls-on (hitting edge = game over) and
  walls-off (snake wraps to the opposite side)
- Update the button label to reflect the current mode
- The toggle should work mid-game without resetting the score
```

---

## Slash Command Quick Reference

Use these at any point during Phase 3 or 4:

| Command | When to use |
|---|---|
| `/explain` | Highlight a block of generated code you don't understand — ask Copilot to walk through it |
| `/fix` | Describe a bug or unexpected behaviour — Copilot will diagnose and fix it |
| `/doc` | Generate a JSDoc comment for a function |

### Example `/fix` prompt

```
/fix The snake grows every frame even when it hasn't eaten food.
The tail is not being removed. The score stays at 0 but the snake
keeps getting longer from the moment the game starts.
```

### Example `/explain` prompt

```
/explain Can you walk through the collision detection logic in the gameStep()
function? I want to understand why we check the new head position before
adding it to the array, and what happens at the array boundary.
```
