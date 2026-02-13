# 📘 The Agile Student Playbook: GitHub Projects Edition

This guide outlines how we manage our software development lifecycle. We use **GitHub Projects** to track our work, but we have a specific workflow designed to keep multiple teams organized on a single board.

See the project: https://github.com/users/brim-borium/projects/8  

## 1. The Core Concepts (Read This First)

We use standard GitHub terminology in a slightly unique way to fit our multi-team structure.

### 🧩 Milestones = Teams (Swimlanes)

In this project, we do **not** use Milestones for deadlines.

* **Usage:** A "Milestone" represents your **Team** (e.g., "Discovery World", "KG", "Multi-Agent System").
* **Why:** This creates horizontal "swimlanes" on the board, allowing us to see exactly what each team is doing side-by-side.

### 🔄 Iterations = Sprints (Time)

* **Usage:** We work in 2-week cycles called **Sprints**.
* **Auto-Logic:** GitHub automatically groups dates into `@current` (Active Sprint) and `@next` (Upcoming Sprint).

### 👕 Size = Complexity (Not Time)

* **Usage:** We estimate tasks using **T-Shirt Sizes** (XS, S, M, L, XL).
* **Why:** Don't try to predict exact hours. An "S" is a quick task; an "XL" is a beast that might need breaking down.

## 2. The Workflow: From Idea to Done

This is the lifecycle of every work item. Follow this strictly to keep the board clean.

### Phase 1: Ideation (The Backlog)

1. **Create an Item:** Go to the **Project Backlog** tab or your team's specific backlog tab.
2. **Draft:** Click "Add item" (or `Ctrl+Space`). Type a rough title.
3. **Status:** The status will automatically default to **Backlog**.
4. **Labeling:** Add a label immediately (e.g., `bug`, `enhancement`, `documentation`).
   * *Why?* Labels allow us to visually scan the board to see if we are building new things (green/blue) or just fixing broken things (red).

### Phase 2: Refinement (Getting to "Ready")

An item cannot be worked on until it is **Ready**. To move a ticket status to **Ready**, it *must* meet the definition of done for planning:

* ✅ **Title:** Clear and concise.
* ✅ **Description:** No more "talking points." The description must clearly state *what* needs to be done and the acceptance criteria.
* ✅ **Milestone:** Assigned to your Team (e.g., "KG").
* ✅ **Size:** Estimated (XS - XL).

**🚀 The Rule:** If it doesn't have a size or a clear description, it stays in **Backlog**. Once it has all the above, change Status to **Ready**.

### Phase 3: Planning (The Buffer)

Once an item is **Ready**, move it to the **Next Sprint** bucket.

1. Assign the **Iteration** field to the upcoming sprint.
2. This item will now appear on the **Next Sprint** board.
3. *Note:* This is our "Buffer." If the current sprint finishes early, we pull from here.

### Phase 4: Execution (The Sprint)

When the new sprint begins (or when you pull work forward):

1. The item moves to the **Current Sprint** board (automatically if the date changes, or manually if pulling forward).
2. **In Progress:** When you start coding, move the card to **In Progress**. Assign yourself to the card.
3. **In Review:** When you open a Pull Request (PR), move the card to **In Review**.
4. **Done:** When the PR is merged and verified, move to **Done**.

## 3. Navigating the Board

We have configured several "Views" to help you focus.

| View Name | What it's for |
| :--- | :--- |
| **Current Sprint** | **The Daily Driver.** Shows active work for the current 2-week cycle. Grouped by Team (Milestone). |
| **Next Sprint** | **The On-Deck Circle.** Work queued up for the future. Use this for planning meetings. |
| **Project Backlog** | **The Master List.** Everything everyone wants to do, ever. |
| **[Team] Backlog** | **Focused Planning.** (e.g., "KG Backlog"). Shows only *your* team's items. Use this to refine issues. |
| **Roadmap** | **The Big Picture.** A timeline view showing when tasks land across multiple sprints. |
| **In Review** | **Unblocking.** A list of items waiting for code review. If this list is long, stop coding and start reviewing! |

## 4. Setup Guide (For Admins)

*Instructions on how to recreate this board from scratch.*

### Initial Initialization

1. Create a new Project in GitHub.
2. Select the **"Iteration"** template (this provides the base fields like Iteration).
3. In this specific setup, go to your Repository -> Issues -> Milestones. Create three milestones: `Discovery World`, `KG`, `Multi-Agent System`. Set them to "No due date".

### View Configuration

#### View 1: Current Sprint
* **Layout:** Board.
* **Column Field:** Status.
* **Group by:** Milestone (This creates the swimlanes).
* **Filter:** `iteration:@current -status:Backlog`
* **Sort:** Status (Ascending).

#### View 2: Next Sprint
* **Layout:** Board.
* **Column Field:** Status.
* **Group by:** Milestone.
* **Filter:** `iteration:@next`.

#### View 3: Project Backlog
* **Layout:** Table.
* **Filter:** `-iteration:@current` to hide work from current sprint.
* **Group by:** Milestone.

#### View 3: Team Backlogs (e.g., KG Backlog)
* **Layout:** Table.
* **Filter:** `milestone:"Multi-Agent System" -iteration:@current` to hide work from current sprint.

#### View 4: Roadmap
* **Layout:** Roadmap.
* **Date Fields:** Start Date / Target Date (or use Iteration start/end).
* **Markers:** Enable "Markers" to show Sprint lines.

## 5. Summary of Rules

1. **No Size?** It's not Ready.
2. **No Description?** It's not Ready.
3. **No Team (Milestone)?** It's not Ready.
4. **Don't work on "Backlog" items.** Only work on "Ready" items that are in `@current`.
