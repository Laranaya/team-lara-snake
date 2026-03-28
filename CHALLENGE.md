# 🐍 GitHub Copilot Snake Game Challenge

> **QualiTEC – Copilot Challenge**
> Teams: up to 5 people | Duration: ~45 minutes | Tool: GitHub Copilot in VS Code

---

## The Goal

Build a working Snake game using **only GitHub Copilot** — but in the _right order_, using the right Copilot mode at each stage.

The challenge is not just about the game. It is about learning to use Copilot's different modes pur      posefully: **Chat → Plan → Agent**, with slash commands and prompt refinement along the way.

---

## Rules

1. **Follow the phases in order.** Do not skip ahead.
2. **Fill in your evidence files** after each phase. Empty evidence = zero points for that phase.
3. **One driver per team** builds in VS Code. Others suggest prompts, discuss, and review — that counts.
4. **Use the starter prompts** in `prompts.md` as a starting point — then refine and improve them. The best teams iterate.
5. **Do not** use any other AI tool or copy code from the internet.

---

## Phases

### Phase 0 – Setup (5 minutes)

1. **Claim your copy of the starter files:**
   - **Git path:** Click **"Use this template"** on the GitHub repo → name it `team-[your-team-name]-snake` → clone it locally
   - **ZIP path:** Download and unzip the starter files → rename the folder `team-[your-team-name]-snake`
2. Open the folder in **VS Code**.
3. Confirm GitHub Copilot is active (look for the Copilot icon in the status bar — it should not be crossed out).
4. Nominate your **driver** (the person typing in VS Code). Everyone else is a prompt coach.

---

### Phase 1 – Research with Chat (8 minutes)

**Mode: GitHub Copilot Chat**

Goal: Understand what you are going to build _before_ writing a single line of code.

**Steps:**

1. Open Copilot Chat (`Ctrl+Alt+I` on Windows/Linux · `Cmd+Alt+I` on Mac).
2. Use the starter prompt from `prompts.md → Phase 1` as your opening message.
3. Read the response as a team. Discuss what you learned.
4. Ask at least **one follow-up question** — go deeper on something you didn't fully understand.
5. Copy your best exchange (your prompt + Copilot's response) into `evidence/phase1-chat.md`.

**Git teams:** Commit with message `feat: phase1 - research`
**ZIP teams:** Save the evidence file and move on.

---

### Phase 2 – Design with Plan Mode (8 minutes)

**Mode: GitHub Copilot Plan**

Goal: Generate a structured implementation plan _before_ writing code.

**Steps:**

1. In Copilot Chat, click the **mode selector** (bottom-left of the Chat panel) and choose **"Plan"**.
2. Use the starter prompt from `prompts.md → Phase 2`.
3. Review the plan as a team. Ask Copilot to adjust anything that seems wrong or missing.
4. Copy the final agreed plan into `evidence/phase2-plan.md`.

**Git teams:** Commit with message `feat: phase2 - plan`
**ZIP teams:** Save the evidence file and move on.

---

### Phase 3 – Build with Agent Mode (12 minutes)

**Mode: GitHub Copilot Agent**

Goal: Implement the game _step by step_, one TODO at a time.

**Steps:**

1. Switch to **Agent mode** (mode selector → "Agent").
2. Open `snake.html`. You will see **4 `TODO – PHASE 3` comments** in the `<script>` tag.
3. Address **one TODO at a time** using the matching starter prompt from `prompts.md → Phase 3`. Do not send all 4 at once.
4. After each step, read the generated code. Use `/explain` if anything is unclear.
5. If something is wrong or broken, use `/fix` and describe what you observe.
6. You **must use at least one slash command** (`/explain` or `/fix`) during this phase — it is worth points.
7. Pick your **single best prompt** from this phase and paste it (with your notes on why it worked) into `evidence/phase3-prompt.md`.

**Git teams:** Commit with message `feat: phase3 - base game`
**ZIP teams:** Save the evidence file and move on.

---

### Phase 4 – Refine (8 minutes)

**Mode: GitHub Copilot Agent (stay in it)**

Goal: Make the game better. Show off what Copilot can do when prompted well.

**Steps:**

1. Look at the `TODO – PHASE 4` comment at the bottom of `snake.html`.
2. Pick **at least 2 extra features** to add (ideas and starter prompts are in `prompts.md → Phase 4`).
3. Use Agent mode to implement them. Refine your prompts if the first attempt isn't quite right.
4. List every feature you added — and the prompt you used — in `evidence/phase4-features.md`.

**Git teams:** Commit with message `feat: phase4 - refinements`
**ZIP teams:** Save the evidence file and move on.

---

### Phase 5 – Submit (4 minutes)

Before submitting, run through this checklist:

- [ ] `snake.html` opens in a browser and the game is fully playable
- [ ] All 4 evidence files in `evidence/` are filled in (not just the template text)
- [ ] At least one slash command was used and noted in `evidence/phase3-prompt.md`
- [ ] At least 2 extra features are listed in `evidence/phase4-features.md`

Then submit via the **Microsoft Form** (link shared by your facilitator):

- Team name
- **Git teams:** GitHub repo URL
- **ZIP teams:** OneDrive link with `team-[name]-snake.zip`
- Screenshot of your favourite prompt moment (optional but encouraged)

See `HOW-TO-SUBMIT.md` for full instructions.

---

## Scoring (100 points)

| Category                                 | Git teams            | ZIP teams | Points  |
| ---------------------------------------- | -------------------- | --------- | ------- |
| All 4 evidence files filled in           | Required             | Required  | 20      |
| 4 phase commits with correct messages    | Required             | Required  | 10      |
| Game runs and is playable                | Required             | Required  | 30      |
| Extra features added in Phase 4          | Assessed             | Assessed  | 20      |
| Slash command used & documented          | `/explain` or `/fix` | same      | 10      |
| Best prompt quality (`phase3-prompt.md`) | Judged               | Judged    | 10      |
| **Total**                                |                      |           | **100** |

---

## Tips for a Great Score

- **Specificity wins.** "Add keyboard controls for arrow keys that prevent reversing direction" beats "add controls".
- **Give context.** Tell Copilot what already exists before asking for the next thing.
- **Iterate.** A refined second prompt is almost always better than the first — and judges can tell the difference.
- **Use `/explain`** when you don't understand generated code. It shows engagement and counts toward your score.

---

Good luck! 🐍
