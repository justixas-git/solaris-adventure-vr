# Solaris Adventure  
**Educational VR Game — Gameplay Systems & Interaction Design (Unity / C#)**

Solaris Adventure is an educational VR game developed as part of my Bachelor’s thesis.  
It teaches middle-school astronomy concepts (grades 5–8) through **interactive VR missions** and **free exploration**.

> **Note:** The full Unity project and playable builds are not publicly available. Additional details can be shared on request.

---

## What This Project Demonstrates
- Designing gameplay systems under **VR usability/comfort constraints**
- Building **reusable interaction logic** across multiple gameplay contexts
- Structuring a multi-scene project with clear **system responsibilities**
- Implementing a **cross-cutting localization system** in an existing codebase

---

## Key Systems Overview

| System | What it does | Why it matters |
|---|---|---|
| Mission flow & progression | Controls mission state, objectives, and completion feedback | Keeps gameplay logic structured and scalable |
| VR interaction layer | Handles consistent object interaction across missions | Reduces duplicated scene logic and improves UX consistency |
| UI & feedback | Presents instructions, progress, and contextual info in VR | Prevents overload and improves clarity for younger players |
| Content/data representation | Structures learning content and mission data | Enables iteration without rewriting core mechanics |
| **Localization (post-thesis)** | Full LT localization + runtime language switching in settings | Demonstrates cross-cutting refactor + real-world readiness |
| Audio & polish systems | Ambient/interaction SFX and scene cohesion | Improves readability and “finished” feel |

---

## Project Structure
The game follows a **hub-and-missions structure**:
- Main hub (navigation and progression)
- Missions:
  - Solar System
  - Orbital Mechanics
  - Moon Phases
  - Constellations
- Free-roam exploration mode

---

## Post-Thesis Improvement — Localization System
After the thesis defense, I implemented a **full localization system**:
- Complete Lithuanian localization, with English retained as an option
- **Seamless runtime language switching** via the in-game settings menu
- Applied consistently across menus, mission instructions, feedback UI, and informational panels

This required refactoring UI text flow and ensuring safe updates across active scenes.

---

## My Role
Solo development, including:
- VR interaction and control systems
- Gameplay logic and mission flow
- Scene structure and navigation
- UI flow and player feedback
- Localization system (post-thesis)

---

## Technology
- Unity (VR)
- C#
- XR interaction systems
- Custom gameplay scripts

---

## Media
Gameplay short: https://youtube.com/shorts/7OgnFOWju9Q?feature=share

---

## Screenshots
![Main Hub](images/main-hub.png)  
![Solar System Missions — Level 3](images/ssm-lvl3.png)  
![Orbital Mechanics Missions — Level 3](images/omm-lvl3.png)

More screenshots are available in the `images` folder.
