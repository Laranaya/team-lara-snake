# Phase 4 Evidence – Refinements (Copilot Agent Mode)

**Team name:** Lara
**Completed at:** 18:17

---

## Features Added

List every feature you added in Phase 4. For each one, paste the prompt you used (or the best version of it).

---

### Feature 1

**Name:** Snake interface change

**Prompt used:**
- Change the way the snake looks, make it look like a cartoon snake green with a tail and cute face
- Given the pasted image, make the snake look like that 
- the snake body is too basic, it appears like 3 balls, can you make it more modern and more snake-like, as one body, rather than the circles, it should more like a snake rather than caterpillar, and if possible include a tongue sticking out

**Notes:** _Anything interesting about how Copilot implemented it? Did you have to refine the prompt? Any `/fix` moments?_

- needed to tweak the way the snake looked, needed to paste an image from the internet as reference

---

### Feature(s) 2

**Name:** Fix UI, game over screen, restart button, speed ramp-up, high score, walls off wrap mode, visual effects

**Prompt used:** 
- for this game, implement these features and make it look user friendly, also make buttons glow: game over screen, restart button, speed ramp-up,
// high score (localStorage), walls-off wrap mode, visual effects.
- can you make the UI look a bit cooler? maybe make it feel more like a real video game? and make everything more spaced out such as the speed and the mode of the walls etc it has to be more visually pleasing and user experience should be better :)
- can you make everything spaces on the window WITHOUT having to scroll down? and also put some stars twinkling in the back?
- NICEE it's looking great :) now can you please add a pause button? idk where but do not distrupt the whole interface :)
- but now i cant see the top and bottom of the page properly, can you please tweak it and move everything but keep it so i dont scroll? but nake it so that i can read everything on the page

_paste here_

**Notes:**
- There was an issue, the code randomly showed on the screen so I typed this prompt: 
  - the UI is weird, the code is showing on the website? and the game over keeps coming on

---

### Feature 3 *(if applicable)*

**Name:** Changing Fruit/Snake Tongue

**Prompt used:**

changing fruit:
- can you please make the "food" look like real food?
- is it possible to alternate between different fruits ? such as apple then once the snake eats an apple, a banana will pop up somewhere else and maybe after the snake eats the banana, make a strawberry etc etc more fruits?
- make the fruit all the same size as right now they are different

snake tongue:
  - can you make the snake tongue go horizontally rather than vertically
  - can you make the tongue a bit down so that we can see the eyes properly? see the pasted screenshot
  - ok nvm u can remove the tongue but u can put a cute smiley open mouth
  - ok make a little tongue from the smile but make it a cute snake tongue please and dont make it too long

**Notes:**
- there was an issue where we couldn't see the overall elements on the gameboard (snake + fruits):
  prompt: i dont see the snake!! or the fruits :( what is going on
  response: Found the issue! 🔍 The fruitTypes array is being declared after it's being used. Let me fix that: Let me verify the drawFood function is properly defined: Perfect! ✅ The fix has been properly applied and verified. Here's what I confirmed:

Variables declared in correct order:

Line 402: const fruitTypes = ['apple', 'banana', 'strawberry', 'orange', 'grape'];
Line 403: let fruitType = 'apple';
All fruit drawing functions defined BEFORE use:

snake.html:527 (line 527)
snake.html:565 (line 565)
snake.html:585 (line 585)
snake.html:619 (line 619)
snake.html:646 (line 646)
snake.html:670 (line 670)
Fruit type properly used at three points - all AFTER declaration:

Line 417: Game initialization
Line 510: When food is eaten
Line 863: When game restarts
Your game should now render properly! Refresh your browser and the snake and fruits should be visible. The multi-fruit system is now fully operational with 5 different fruits randomly cycling each time food is eaten. 🎮✨

Claude Haiku 4.5 • 0.33x

- And then the fruit had different sizes: some were smaller etc
Response: I can see the issue. The fruits have different scaling factors:

Banana uses foodRadius * 1.2 (making it wider)
Grapes use fixed pixel sizes (0.8) instead of scaling with foodRadius, making them tiny
I'll normalize all fruits to use foodRadius as the primary dimension:

Done! ✅ I've normalized all fruit sizes:

Banana - Changed from foodRadius * 1.2 to foodRadius (was oversized)
Grapes - Now scale with foodRadius * 0.25 per grape instead of fixed pixel size (was tiny)
All fruits now use foodRadius as their base dimension, so they'll display at the same size when they rotate. Refresh the browser and they should all be perfectly uniform! 🍎🍌🍓🍊🍇

Claude Haiku 4.5 • 0.33x
---

## Team Notes

_Which feature are you most proud of? What was the most interesting prompt refinement moment in this phase?_

- features we have (some extra):
  - alternating fruits
  - starry background 
  - pause button
  - walls on/off mode

I like the idea of using the different kinds of fruit to make the game more interesting, as well as the starry background adding more dimension to the game, and I like that there is a pause button so users can stop the game if needed without losing straight away

Also, given my newfound knowledge of different GitHub Copilot modes, I used the ask mode to ask Copilot what else could be implemented to make the snake game different and stand out more, by using the ask mode, no code changes are made yet; ensuring Copilot does its job correctly, doing what is asked of it. 

Prompt:
what else could we do to make this snake game more fun? give suggestions to make it more unique and more fun for the user

Response:
Great question! Here are some creative ideas to make your snake game more engaging and unique:

🎮 Gameplay Mechanics
Power-ups System

Shield (temporary invincibility - 3 seconds)
Speed Boost/Slow (temporarily change speed)
Double Points (next food worth 2x)
Freeze Enemy (stop the snake growth for 5 seconds)
Random spawning with visual effects
Obstacles & Hazards

Random mines/spikes that appear mid-game
Moving obstacles that drift across the map
Safe zones you must reach
Progressive difficulty: more obstacles as score increases
Combo & Streak System

Consecutive food eaten = multiplier (1x → 2x → 3x)
Visual counter showing current combo
Lose combo if you pause/hit obstacle
Bonus points for maintaining streaks
Special Challenges

Time Attack mode (score as much as possible in 60 seconds)
Survival mode (increasing speed, no high score - just "how long?")
"Cherry Chase" (specific fruit must be eaten in order)
Odd/Even mode (alternate collecting odd/even point fruits)
✨ Visual Enhancements
Particle Effects

Burst of particles when eating food
Trail effect following the snake
Screen flash on milestones (50pts, 100pts, etc.)
Impact effects when hitting walls
Snake Customization

Snake changes color as it grows (gradient effect)
Unlock different snake skins (rainbow, neon, glowing)
Different head styles (crown when high score, etc.)
Snake personality changes (expression varies by performance)
Dynamic Background

Background color shifts with score
Intensity increases (more twinkling stars, glow effects)
Theme changes at milestones
🎵 Audio Design
Sound Effects
Satisfying "pop" when eating food
Different sounds for different fruits
Warning beep before collision
Victory/defeat jingles
Optional background music
📊 Progression & Goals
Achievement System

"First Bite" - eat your first food
"Speed Demon" - reach speed 15 fps
"Fruit Connoisseur" - eat one of each fruit type
"Marathon Run" - snake reaches 10 segments
Display badges in UI
Leaderboard & Statistics

Track best runs
Personal statistics (total food eaten, longest session)
Show "Previous Run" ghost snake overlay
Weekly high score file
🎨 Unique Twists
Portals

Random portals appear - eat one to teleport to safe spot
Different color portals = different effects
Multi-Food Challenge

2-3 foods on screen at once
Must eat them in sequence for bonus
Different foods worth different points
Snake Abilities

Dash move (short speed burst, costs 1 segment)
Shield power (temporary invincibility)
Slow-motion mode (brief time slowdown)
Rotating/Tilting Arena

Canvas slowly rotates
Adds disorientation challenge
Visual dizzy effect
Ghost Run Feature

Toggle on/off a semi-transparent replay of your best run
Race against your own ghost
Competitive but solo
🎯 Quality of Life
Tutorial/Onboarding

First-run interactive tutorial
"How to Play" modal
Control hints
Difficulty Presets

Easy/Normal/Hard/Insane modes
Changes starting speed, number of obstacles, etc.
Display current difficulty
Game Stats Display

Show "Fruits Eaten", "Segments", "Personal Best"
Accuracy percentage (successful moves vs total)
Session duration
🌟 My Top 3 Recommendations for You:
Power-ups - Adds surprise and strategy (shield, speed boost, 2x points)
Combo System - Makes continuous play rewarding, super addictive
Particle Effects + Better Sound - Visual/audio feedback makes eating food feel satisfying
Would you like me to implement any of these? I'd recommend starting with power-ups since it's impactful but not overly complex, or combo system if you want to keep mechanics simple but make scoring more engaging.

I implemened the ghost trail, here are my follow up prompts and responses:

Prompt:
- please implement this feature: Ghost Run Feature
Toggle on/off a semi-transparent replay of your best run
Race against your own ghost
Competitive but solo

Response:
I'll implement the Ghost Run feature! This will let you record your best run and race against it next time. Here's what I'll add:

Record ghost data when you set a new high score
Render a semi-transparent ghost snake that replays your best run
Add a toggle button to show/hide the ghost
Save/load ghost data from localStorage
✅ Ghost Run Feature Implemented!

Here's what I added:

🎮 Features:
👻 Ghost Toggle Button - Purple button in the controls that turns the ghost on/off

Shows "👻 GHOST: ON/OFF" with active state styling
Smart Recording System - Records every frame of your best run

Automatically saves to localStorage when you set a new high score
Loads on game start so your ghost is always there
Real-time Ghost Race - The ghost plays alongside you

Semi-transparent purple outline (25% opacity)
Synchronized frame-by-frame with your current run
Lets you visually compare your performance
Data Persistence - Your best run is saved across sessions

Ghost data stored in localStorage with your high score
No ghost appears until you beat your first 0 score
🎯 How it works:
First playthrough: No ghost (you're setting the baseline)
When you set a new high score: That entire run is saved as the ghost
Next game: Toggle the ghost ON to race against your previous best
Visual feedback: Ghost appears in semi-transparent purple, showing exactly where you went
Try it out! Refresh the browser, play a round, set a new high score, then start a new game and toggle the ghost button to race against yourself! 👻⚡

Claude Haiku 4.5 • 0.33x

Issues, so I typed another prompt:
i dont see the ghost and idont get it, i think the ghost should be there after EACH game, NOT just when the user hits a new high score? I think what you should implement is: a ghost trail AFTER the user plays each game (regardless if they achieved a high score or not - and when the game over screen shows, the user can click - see trail - and it will show the ghost trail of the snake in purple?) and after seeing the ghost trail, there should be an option to start a new game

Response:
Ah, I understand! You want a trail viewer on the game-over screen that appears after every game, not just high scores. Let me redesign this:

Let me fix the implementation in smaller chunks:

Perfect! ✅ Trail Viewer Implemented!

Here's what I redesigned:

👻 How it works now:
After Every Game - Your snake's trail is automatically saved (regardless of score)
Game Over Screen - Shows "👻 See Trail" button + "Play Again" button
Click "See Trail" - Displays your entire snake's path in beautiful purple
Trail fades from light to dark, showing your journey
Head and body rendered semi-transparent
"← Back" - Returns to the score screen
"Play Again" - Goes straight to a new game
🎮 Key differences from before:
✅ Trail saves after every game (not just high scores)
✅ Trail view shows on the game-over screen (not during gameplay)
✅ Purple faded effect shows your complete path through the grid
✅ Clean navigation: Back or Play Again from anywhere
Try it now! Play a game, hit Game Over, and click "👻 See Trail" to watch your snake's entire purple trail! 🐍✨

Result: successfully implemented
