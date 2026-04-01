# Phase 3 Evidence – Build (Copilot Agent Mode)

**Team name:** Lara
**Completed at:** _17:54_

---

## Your Best Prompt

Paste the **single best prompt** you used during Phase 3 below.
This is what the judges will read — make it your most specific, well-crafted, context-rich prompt.

### The prompt

Under the comment "TODO – PHASE 3, STEP 2" in snake.html, add a keydown
event listener on the document that changes dx and dy based on arrow key presses.

Requirements:
- ArrowUp    → dy = -1, dx = 0  (only if not currently moving down)
- ArrowDown  → dy = 1,  dx = 0  (only if not currently moving up)
- ArrowLeft  → dx = -1, dy = 0  (only if not currently moving right)
- ArrowRight → dx = 1,  dy = 0  (only if not currently moving left)
- No other keys should have any effect
- The snake must not be able to reverse directly into itself

### Why this was your best prompt

_Explain in 1–2 sentences: what made it effective? (specificity, context it provided, constraints it set...)_

Simple instructions, Copilot did EXACTLY what was asked of it

---

## Slash Command Used

Which slash command did you use?

**Command used:** /explain

**What you asked:** /explain Please explain this (Done! I've added the keyboard event listener for Phase 3, Step 2 to snake.html.

The listener handles all four arrow keys with reversal prevention:

ArrowUp → dy = -1, dx = 0 (blocked if already moving down)
ArrowDown → dy = 1, dx = 0 (blocked if already moving up)
ArrowLeft → dx = -1, dy = 0 (blocked if already moving right)
ArrowRight → dx = 1, dy = 0 (blocked if already moving left)
The guard conditions (dy !== 1, dy !== -1, etc.) prevent the snake from instantly reversing into itself. Any other key presses are ignored.

Next step: When ready for Phase 3 Step 3, add the main game loop function (gameStep) that moves the snake, checks collisions, handles food, and renders everything to the canvas.

Claude Haiku 4.5 • 1x)

**What happened:**

_Describe the result in 1–2 sentences — did it fix the problem? Did it surprise you?_ It helped explain the logic of dy and dx, and explaining how the variables change based on the movement, say -1 for left and +1 for right when moving horizontally. Also the arrow key checks are explained well and re-iterating the fact that we have to prevent instant 180 degree reversal. Also explaining the importance of guard conditions, w/o them, it would cause instant death.

I also asked a follow up prompt for more clarity: /explain what do you mean by prevents instant 180 degree reversal? and what is guard condition and the reversal prevention gotcha concept?

It explained: 
- A 180° reversal is when the snake tries to turn directly backward into itself. And provided a visual example, w/o me having to ask, saving me time and being more clear. 
- And explained guard condition: an if statement that checks: "Is this action safe before allowing it?" Without guard condition, if snake moving right and player press left, snake dies but with guard condition, if snake moving right, left arrow ignored.
- The gotcha is that without this guard, the game feels broken or unfair. 
- The guard silently discards bad inputs. It doesn't say "you can't turn that way"—it just ignores the keypress. This is a UX choice (better than instant death, but can feel unresponsive if not explained).

I asked another follow up for gotcha since it didn't explain that as well as the other concepts(/explain i still dont understand gotcha): A gotcha is a hidden trap or unexpected behavior that surprises you. Copilot gave a nice simple example so I could see this being applied.
The gotcha = silent rejection of input

Finally, I asked this, since I was genuinely confused: 
/explain so what is the difference between guard and gotcha? they seem almost the same to me but i could be wrong

Response:
Guard Condition	- A piece of code (if statement) that prevents something bad from happening
Gotcha - A hidden problem or unexpected behavior that surprises the user

The relationship: 
Guard Condition = The SOLUTION
Gotcha = The PROBLEM that the solution creates

TL;DR
Guard = The bodyguard (code that blocks bad inputs)

Gotcha = The unintended side effect (player confusion from silent blocking)

The guard solves the 180° death problem, but creates the gotcha of silent input rejection. They're not the same—one is the solution, one is the problem that solution creates.

I learnt a new concept: gotcha
My curiosity led me to further research but due to time constraints, I parked it and moved on to finish the rest of the code for Phase 3.

And it led to me asking just for the sake of clarity in Copilot after my quick research, my prompt: /explain so the gotcha isnt actually code, its just a concept?

In sum, Copilot returned to me that I am correct and that it is just a concept about UX. It is a description of what happens when a user interacts with the code.
---

## Team Notes

_What did your team learn about writing good prompts from this phase? What will you do differently next time?_

Ask for /explain STRAIGHT away after I received response rather than keep prompting and realise later oh I need help and having to copy and paste the answer/prompt.