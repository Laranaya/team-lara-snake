
# 🐍 GitHub Copilot Snake Game Challenge 
> **QualiTEC – Copilot Challenge** 
> Teams: up to 5 people  Duration: ~45 minutes  Tool: GitHub Copilot in VS Code 
--- 
## The Goal 
Build a working Snake game using **only GitHub Copilot** — but in the *right order*, using the right Copilot mode at each stage. 
The challenge is not just about the game. It is about learning to use Copilot's different modes purposefully: **Chat → Plan → Agent**, with slash commands and prompt refinement along the way. 
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
Goal: Understand what you are going to build *before* writing a single line of code. 
**Steps:** 
1. Open Copilot Chat (`Ctrl+Alt+I` on Windows/Linux · `Cmd+Alt+I` on Mac). 
2. Use the starter prompt from `prompts.md → Phase 1` as your opening message. 
3. Read the response as a team. Discuss what you learned. 
4. Ask at least **one follow-up question** — go deeper on something you didn't fully understand. 
5. Copy your best exchange (your prompt + Copilot's response) into `evidence/phase1-chat.md`. 
**GitHub (optional commit):** Commit with message `feat: phase1 - research` 
**ZIP teams:** Save the evidence file and move on. 
--- 
### Phase 2 – Design with Plan Mode (8 minutes) 
**Mode: GitHub Copilot Plan** 
Goal: Generate a structured implementation plan *before* writing code. 
**Steps:** 
1. In Copilot Chat, click the **mode selector** (bottom-left of the Chat panel) and choose **"Plan"**. 
2. Use the starter prompt from `prompts.md → Phase 2`. 
3. Review the plan as a team. Ask Copilot to adjust anything that seems wrong or missing. 
4. Copy the final agreed plan into `evidence/phase2-plan.md`. 
**GitHub (optional commit):** Commit with message `feat: phase2 - plan` 
**ZIP teams:** Save the evidence file and move on. 
--- 
### Phase 3 – Build with Agent Mode (12 minutes) 
**Mode: GitHub Copilot Agent** 
Goal: Implement the game *step by step*, one TODO at a time. 
**Steps:** 
1. Switch to **Agent mode** — it can now read and edit your files 
2. Open `snake.html` — you'll see 4 TODO comments inside `<script>` 
3. Address **one TODO at a time** using **prompts.md → Phase 3** 
4. Use `/explain` or `/fix` 
5. Save best prompt to `evidence/phase3-prompt.md` 
**GitHub (optional commit):** Commit with message `feat: phase3 - base game` 
**ZIP teams:** Save evidence. 
--- 
### Phase 4 – Refine (8 minutes) 
**Mode: GitHub Copilot Agent** 
**Steps:** 
1. Add at least **2 extra features** (ideas in prompts.md) 
2. Use prompts + refine 
3. Save list in `evidence/phase4-features.md` 
**GitHub (optional commit):** Commit with message `feat: phase4 - refinements` 
**ZIP teams:** Save. 
--- 
### Phase 5 – Submit (4 minutes) 
Checklist: 
- `snake.html` runs 
- Evidence files filled 
- Slash command used 
- At least 2 extra features 
Submit via Google Form: 
- Team name 
- **GitHub (optional commit):** GitHub URL 
- **ZIP teams:** Upload ZIP 
- Screenshot optional 
--- 
## Scoring (100 points) 
 Category | GitHub | ZIP | Points 
---|---|---|---
 Evidence files | Required | Required | 20 
 Phase Progress Evidence (commits or progress file) | Required | N/A | 10 
 Game playable | Required | Required | 30 
 Extra features | Assessed | Assessed | 20 
 Slash command | Required | Required | 10 
 Best prompt | Judged | Judged | 10 
**Total 100** 
--- 
