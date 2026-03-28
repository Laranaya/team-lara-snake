# Phase 1 Evidence – Research (Copilot Chat)

**Team name:** Lara
**Completed at:** _e.g. 14:03_

---

- NOTE FROM USER LARA:
I tested Phase 1 *two* ways: 1 way I pasted the prompts into Copilot *WITHOUT any context from any files*. The 2nd way I did so was *WITH the context from the file CHALLENGE.md*. For the follow up prompt, both versions gave me the same overall solution: *the best data structure for the snake to be ARRAY OF COORDINATE OBJECTS*. The 2nd ver had more context however so it was a bit easier to follow through with the first prompt.

## Your Best Chat Exchange

Paste your best prompt and Copilot's full response below.

### Your prompt

PROMPT: I'm going to build a Snake game using HTML canvas and vanilla JavaScript.
Before I write any code, help me understand the key components I'll need to build.
For each component, briefly explain what it does and why it matters.

### Copilot's response

ANSWER: I'll break down the essential components for a Snake game like the one in this challenge:

Key Components
1. Canvas Setup
The drawing surface where everything is rendered
You'll need a 2D context to draw rectangles (snake segments, food) and text (score)
Matters because it's where all visuals appear

2. Game State
Variables tracking the snake (position, segments, direction), food location, score, and game status (running/paused/over)
Matters because it's the "source of truth" — all logic reads from and updates this state

3. Snake Data Structure
Usually an array of coordinate pairs representing each body segment
The head is typically the first (or last) element; new segments added when eating food
Matters because it determines collision detection and rendering

4. Movement & Direction Logic
Snake moves by removing the tail segment and adding a new head in the current direction
Must prevent 180° reversals (can't go directly backward)
Matters because smooth movement and direction handling feel responsive and prevent cheap deaths

5. Input Handler
Listens for keyboard events (arrow keys or WASD) and updates the snake's intended direction
Matters because it's the only way the player interacts with your Game

6. Collision Detection
Three types: wall collision (game over), self collision (game over), food collision (grow snake + increase score)
Matters because without it, there's no challenge, no feedback, and no win condition

7. Game Loop
requestAnimationFrame or setInterval that repeatedly: updates state → checks collisions → renders frame
Matters because it's the heartbeat that makes everything happen at a consistent speed

8. Rendering
Draw the grid/background, snake segments, food, and score text
Matters because the player sees nothing without it

Quick tip: Start by getting the canvas working and drawing a static snake. Then add movement. Then collision. Then food. This layered approach keeps each phase simple and testable. Good luck! 🐍

*AI model used: Claude Haiku 4.5*
---

## Your Follow-up Question

Paste the follow-up question you asked and a summary of the answer.

### Follow-up prompt

PROMPT: What's the best data structure to represent the snake's body, and why?

### Key insight from the answer

ANSWER: 

Best Data Structure: Array of Coordinate Objects
The winning choice: snake: [{x, y}, {x, y}, {x, y}]

This is what the challenge prompts use, and here's why it's the best approach:

Why This Works
Simple to understand

Each segment is just {x, y} — clear and readable
No magic indices; the structure is self-documenting
Natural movement mechanics

Add to front: snake.unshift({x: newX, y: newY}) — new head
Remove from back: snake.pop() — old tail
This elegantly models how the snake "flows" forward
Easy collision detection

Check if new head coords match any existing segment: snake.some(seg => seg.x === newX && seg.y === newY)
Check if new head is the head itself: snake[0]
Simple rendering

Loop through and draw each segment — no extra logic needed
Different colors for snake[0] (head) vs the rest
Alternatives & Why They're Weaker
Alternative	Issue
Single flat array [x1, y1, x2, y2, ...]	Need index math (even = x, odd = y). Error-prone
Linked list of nodes	Overkill. Adds complexity with no benefit in a grid-based game
Set of "x,y" strings	Works for collision detection, but loses order (you need order to render and move)
Just store head + direction + length	Can't detect self-collision without reconstructing the path
The Only Real Consideration
Performance: With a standard grid (20×20), even a snake that fills half the board is ~200 segments. Array operations (unshift, pop, some()) stay fast enough. No optimization needed for this scale.

Bottom line: Array of objects is intuitive, performant for Snake scale, and maps directly to your game logic. Stick with it.

Claude Haiku 4.5 • 1x


---

## Team Notes

_What was the single most useful thing your team learned from Chat in this phase?_

That context can be very important in terms of answering prompts (in terms of which files to tag on for the AI to have context) and the AI was able to explain everything in a clear manner.