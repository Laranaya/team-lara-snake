# Phase 2 Evidence – Design (Copilot Plan Mode)

**Team name:** _Lara_
**Completed at:** _e.g. 14:11_

---

## The Plan Copilot Generated

PROMPT: Create a step-by-step implementation plan for a Snake game using HTML canvas
and vanilla JavaScript.

The implementation will live inside a single <script> tag in an existing
snake.html file that already has:

A 400x400 canvas element with id="gameCanvas"
A score display element with id="score"
The canvas context already retrieved as: const ctx = canvas.getContext('2d')
Break the work into exactly 4 steps matching these TODOs already in the file:

Game constants and variables
Keyboard event listeners
Main game loop function
Starting the game loop
For each step, describe what needs to be implemented and any important
considerations (edge cases, gotchas, design decisions).

Paste the full plan from Plan mode below.

Plan: Snake Game Implementation (Phase 3)
TL;DR: Implement a functional Snake game in 4 sequential steps: set up game state (variables/constants), add keyboard controls, create the core game loop (movement/collision/rendering), then start it with setInterval at 150ms. Each step builds on the previous one—no parallelization possible.

Step 1: Game Constants and Variables
Location: TODO – PHASE 3, STEP 1

Set up foundational game state:

GRID_SIZE = 20 and TILE_COUNT = 20 (400px ÷ 20 = 20×20 grid)
snake array with 3 segments: [{x:10, y:10}, {x:9, y:10}, {x:8, y:10}] (head first)
food object at random position not on snake
Direction: dx = 1, dy = 0 (moving right)
score = 0 and gameLoop = null
Helper: randomTile() returns 0–19
Key insight: Snake stores grid coordinates, not pixels. Index 0 is the head.

Step 2: Keyboard Event Listeners
Location: TODO – PHASE 3, STEP 2

Single keydown listener that prevents reversals:

ArrowUp → dx=0, dy=-1 (only if dy===0)
ArrowDown → dx=0, dy=1 (only if dy===0)
ArrowLeft → dx=-1, dy=0 (only if dx===0)
ArrowRight → dx=1, dy=0 (only if dx===0)
Key insight: The condition dy===0 on Up/Down prevents 180° reversals that would kill the snake instantly.

Step 3: Main Game Loop Function (gameStep)
Location: TODO – PHASE 3, STEP 3

In order:

Calculate new head: {x: snake[0].x + dx, y: snake[0].y + dy}
Check wall collision → call gameOver() if out of bounds
Check self-collision → call gameOver() if new head on any segment
Add new head: snake.unshift(newHead)
Check food eaten:
If eaten: increment score, update display, place new food, don't pop tail (growth)
If not: pop tail (normal movement)
Render:
Clear canvas with background colour
Draw head (snake[0]) with one colour, body segments with another (1px inset for grid effect)
Draw food as a circle
Create gameOver() stub that calls clearInterval(gameLoop)
Key insight: Collisions checked before rendering prevents dead snakes flickering on screen. Food eating is the only case where the snake doesn't shrink.

Step 4: Start the Game Loop
Location: TODO – PHASE 3, STEP 4

Place this at the very end of the script (after all function definitions).

Key insight: Saving the interval ID to gameLoop allows gameOver() to stop it later.

Verification Checklist
Variables exist — DevTools console: type snake, food, score ✓
Arrow keys work — snake changes direction, no 180° reversal ✓
Snake moves — visible on canvas, no trails (canvas clears) ✓
Food eaten — score increases, snake grows ✓
Collisions work — hitting walls or self stops the game ✓
No console errors during 30-second play test ✓
Critical Architectural Patterns
Movement model: Remove tail, add head (creates flowing effect)
Collision detection: Check new head coords against bounds and existing segments
Data structure: Array of {x, y} objects (grid units, 0–19 range)
Rendering: Always clear first, then draw snake + food
Game state: All in globals; no classes needed for Phase 3
Ready to implement? Each step is small and testable. Build them sequentially—don't skip ahead or combine steps. Use /explain in Copilot Agent if any generated code is unclear, and /fix if something breaks.

Claude Haiku 4.5 • 1x

---

## Refinements You Made

Did you ask Copilot to adjust or improve any part of the plan? What changed?

_describe here — what did you push back on, and what did Copilot change?_

I typed this prompt: firstly, this is phase 2 NOT 3, please tell me why you thought it was phase 3 and SECONDLY, why the time specifically 150 ms?

Response from Copilot: You're absolutely right on both counts. Let me explain my mistakes:

1. Why I thought it was Phase 3
I misread the context. You were giving me the Phase 2 prompt to help me understand what you wanted, but I treated it as a request to create a Phase 3-level implementation guide instead of a Phase 2 planning-level overview.

The difference:

Phase 2 (Plan mode): High-level architecture, structure, and decisions. What needs to be built and why, not how in detail.
Phase 3 (Agent mode): Step-by-step implementation with code patterns, edge cases, and specific line-by-line guidance.
I delivered Phase 3 depth when you asked for Phase 2 abstraction. My bad—I should have recognized that from context.

2. Why 150ms specifically
I took it directly from the starter prompts in prompts.md (Phase 3, Step 4: "Start with an interval of ~150ms"). But that's not a justification—just where I copied it from.

The actual reasons 150ms is standard for Snake:

~6.67 FPS (1000ms ÷ 150ms) — slow enough to see each frame, fast enough to feel responsive
Player reaction time — humans can react to movement at this speed and adjust direction
Classic Snake timing — original implementations ran at this ballpark speed
Difficulty sweet spot — faster feels frantic and unfair; slower feels sluggish and boring
But 150ms isn't sacred. It's just a reasonable starting point. Phase 4 even includes a feature to ramp speed up as the score increases, so 150ms is tunable.

Claude Haiku 4.5 • 1x

Then, I challenged it to redo the initial answer to the prompt: could you please give me answer for this prompt AGAIN but remember it is phase 2: Create a step-by-step implementation plan for a Snake game using HTML canvas
and vanilla JavaScript.

The implementation will live inside a single <script> tag in an existing
snake.html file that already has:

A 400x400 canvas element with id="gameCanvas"
A score display element with id="score"
The canvas context already retrieved as: const ctx = canvas.getContext('2d')
Break the work into exactly 4 steps matching these TODOs already in the file:

Game constants and variables
Keyboard event listeners
Main game loop function
Starting the game loop
For each step, describe what needs to be implemented and any important
considerations (edge cases, gotchas, design decisions).

And this was the response: Plan: Snake Game Implementation
TL;DR: Build a Snake game by setting up game state (constants & variables) → adding player input (keyboard controls) → implementing core game logic (the game loop with movement, collision, and rendering) → starting the game. The game loop is the heart; everything else feeds into it.

Steps
Step 1: Game Constants and Variables
Establish the foundation of game state.

What to define:

Grid parameters (GRID_SIZE, TILE_COUNT) that define how the canvas is divided
Snake data structure (position and body segments)
Food position
Direction variables (how the snake moves each frame)
Score counter
Game loop reference (needed to stop the game later)
Design considerations:

Data structure choice: Represent the snake as a collection of coordinates. This makes movement straightforward (add to front, remove from back) and collision detection simple (check if any segment matches a point)
Coordinate system: Use grid units (0–19 on a 20×20 grid) rather than pixels. This decouples game logic from rendering and makes math cleaner
Initial state: Snake starts in the center, moving right. Food appears at a random grid location
Why it matters: All of Steps 2–4 depend on these variables. Choosing the right data structures now prevents pain later
Step 2: Keyboard Event Listeners
Give the player control over the snake's direction.

What to add:

A keyboard event handler that listens for arrow key presses
Logic to update direction variables based on player input
Design considerations:

Direction reversal prevention: The player shouldn't be able to reverse the snake 180° into itself. This requires checking the current direction before allowing the opposite one
Timing: Keyboard events come in at human speed (tens to hundreds of milliseconds), but the game loop runs every 150ms. Between input and execution, the snake has already moved. A guard condition prevents instant-death bugs
Single listener vs. per-key: One listener that branches on key type is simpler than multiple listeners
Why it matters: Without this, the player has no agency. The game is unplayable
Step 3: Main Game Loop Function
Implement the core game tick: where state updates and rendering happen together.

What to implement:

Move the snake (calculate new head position based on current direction)
Validate the move (check for wall and self-collisions)
Check if food was eaten (grow the snake or move food)
Render the updated state to the canvas
Design considerations:

Order of operations: Move first, check collisions, update score, render. This sequence prevents visual glitches
Collision detection scope: Two types of collisions (walls and self). Both are fatal, so both end the game immediately
Growth vs. movement: When food is eaten, don't remove the tail—this creates visual growth. Otherwise, remove the tail after adding a head (no net change in length)
Rendering: Clear the canvas, draw snake, draw food. If you render out of order or don't clear, you'll see trails
Why it matters: This is where the game logic lives. Everything else supports this function
Step 4: Start the Game Loop
Trigger the game by repeatedly calling the game loop function at a fixed interval.

What to do:

Use setInterval() to call the game loop function repeatedly
Choose an interval that feels responsive without being overwhelming
Design considerations:

Interval timing: ~150ms gives a natural feel—fast enough to be responsive, slow enough to be playable. This is tunable; faster is harder, slower feels sluggish
Saving the interval reference: Store the returned ID so you can later call clearInterval() to stop the game (e.g., when the player hits a wall)
When to call this: Place it at the very end of your script, after all functions are defined. Otherwise, you'll call a function that doesn't exist yet
Why it matters: Without this, the game never starts. The loop is the heartbeat
Relevant Files
snake.html — single file to modify; all code goes in the <script> tag
Key Design Decisions
Coordinate system: Grid units, not pixels. Cleaner math and separation of concerns
Data structure: Array of coordinate objects. Simple, performant, and easy to reason about
Collision prevention: Guard conditions on direction changes prevent 180° reversals
Single loop: All game logic runs in one function called at a fixed interval. No race conditions, deterministic
Separation of concerns: Step 1 (state), Step 2 (input), Step 3 (logic + rendering), Step 4 (timing). Each builds on the previous
Open Questions for Your Team (Consider These During Phase 2)
Visual style: What colors for the snake head, body, and food? What about the background?
Difficulty scale: Is 150ms the right starting speed, or would you prefer slower/faster?
Game over behavior: Should the game go to a "game over" screen, or just freeze? (Hint: Phase 4 is where you add this)
Stretch goals: Are you planning to add high scores, speed ramp-up, wrapping walls, or other features beyond the base game?
This plan is ready for Phase 3 (Agent mode implementation). Your team should have a shared understanding of the 4-step structure, the key design choices (grid coordinates, array data structure, collision guards), and how each step connects to the next.

Claude Haiku 4.5 • 1x

Reflection for this interaction: when I asked Copilot to redo the prompt, it made the answer slightly less technical, less variable names, more just overall idea

---

## Team Notes

_What surprised you about the plan? Was anything missing or wrong? What would you have done differently?_

NOTE: the title reponse from the first prompt, I received an incorrect phase numbering, it should have been Phase 2 but it gave me Phase 3 instead, even though I GAVE CONTEXT FROM *CHALLENGE MD*