# Solaris Adventure  
**Educational VR Game — Gameplay Systems & Interaction Design (Unity / C#)**

Solaris Adventure is a virtual reality educational game designed for **middle-school students (grades 5–8)**, focused on **learning through interaction** rather than passive presentation. It was developed as a Bachelor’s thesis project at Vilnius Gediminas Technical University. :contentReference[oaicite:0]{index=0}

---

## What This Project Demonstrates

This project is primarily a **gameplay systems** showcase in a VR context:

- **Gameplay systems built under explicit usability / comfort constraints** (VR readability, low cognitive load, clear feedback)
- **Multi-scene architecture** with consistent interaction rules across different gameplay contexts
- **Reusable interaction layer** to reduce scene-specific duplication
- **Structured progression controllers** per mission, with shared logic and clean responsibilities
- Strong implementation discipline and **attention to detail** in both interaction feel and presentation
- Managing cross-cutting systems (e.g., localization) in an existing codebase

---

## Project Structure

The experience follows a **hub-and-missions structure** where each mission targets a different learning objective while sharing a consistent interaction framework. :contentReference[oaicite:1]{index=1}

Core scenes include:
- Main hub / navigation scene
- Mission scenes:
  - Solar System
  - Orbital Mechanics
  - Moon Phases
  - Constellations
- Free exploration mode

---

## Core Systems (Implementation Highlights)

The following system design choices are reflected directly in the codebase (scripts available in a private archive, not published here).

### 1) Mission Flow & Progression
A mission-level orchestration layer drives progression and scene state.

- `MissionSceneController` coordinates mission flow, UI state, and progression events.
- Per-mission controllers encapsulate rules and objectives:
  - Solar System: `SolarSystemLevel1Controller`, `SolarSystemLevel2Controller`, `SolarSystemLevel3Controller`
  - Orbital Mechanics: `OrbitalMechanicsLevel1Controller`, `OrbitalMechanicsLevel2Controller`, `OrbitalMechanicsLevel3Controller`
  - Moon Phases: `MoonPhasesLevel1Controller`, `MoonPhasesLevel2Controller`, `MoonPhasesLevel3Controller`
  - Constellations: `ConstellationLevel1Controller`, `ConstellationLevel2Controller`, `ConstellationLevel3Controller`

This separation keeps scene logic readable and prevents “one giant script” designs.

---

### 2) Interaction System (Reusable, Consistent)
Core interaction behaviours are implemented as reusable components used across missions:

- Base interaction: `GenericInteractable`
- Drag-based interactions: `GenericDragInteractable` (+ specialized variants like `TwoHandConstellationDragInteractable`)
- Selection-related contracts: `IObjectSelection`

The goal is **consistent interaction rules** across different tasks, so the player learns one interaction language and can reuse it everywhere.

---

### 3) UI & Player Feedback (VR-Aware)
UI is treated as a gameplay system, not an overlay:

- Persistent UI layer: `PersistentUI`
- World/hand-follow behaviour: `UIFollowController`
- Global UI flow and menus: `GlobalMenuManager`
- Settings handling: `SettingsManager`
- Viewers and info canvases: `UIModelViewer`, `StellarInfoCanvas`

Design principles:
- Context-sensitive messaging (avoid overload)
- Clear affordances and immediate feedback
- Ability to reduce UI noise (important for younger users and VR comfort) :contentReference[oaicite:2]{index=2}

UI text and feedback are fully localized and updated dynamically based on the active language setting.

---

### 4) Content & Data Representation
The learning content is represented in structured data objects rather than being hard-coded into one-off scene logic.

Examples:
- `FactData`, `FactObject`
- Constellation puzzle data structure: `IConstellationPuzzleData` + individual constellation data assets (e.g., `OrionPuzzleData`, `CygnusPuzzleData`, etc.)

This allows content iteration without rewriting core mechanics.

---

### 5) Supporting Systems (Polish / Cohesion)
Systems that support immersion and consistency:
- Audio control and scene audio logic: `AudioManager`, `AmbientZone`, `TriggerZoneSFX`, `InteractableSFX`, `UIInteractableSFX`
- Orbital visuals & mechanics helpers: `OrbitLineDrawer`, `OrbitHintLine`, `RealisticOrbiter`, `OrbitObject`
- Scene/world behaviours: `PlanetController`, `SatelliteController`, `SelfRotate`
- XR bootstrapping / tracking glue: `XRTrackingOriginBootstrap`, `HMDTrackedPoseRebinder`

These are smaller, but they contribute heavily to a “finished” feel.

---

## Post-Thesis Improvements — Localization System

After the thesis defense, I implemented a **full localization system** for the project, extending the game beyond its original academic scope.

The entire experience was localized to **Lithuanian**, with English retained as an alternative language. Language selection is exposed through the in-game settings menu and can be **changed seamlessly at runtime**, without restarting the application or reloading scenes.

### Technical Highlights
- Centralized language management and settings integration
- Runtime-safe text updates across active scenes
- Localization applied consistently to:
  - menus and settings
  - mission instructions and feedback
  - informational content and UI panels
- Designed to be extensible for additional languages

This feature significantly improved the project’s **real-world readiness** and required careful coordination across multiple existing systems, making it one of the most technically involved additions to the project.

---

## Evaluation Approach

The original project was designed and evaluated against predefined criteria related to educational clarity, usability, and VR suitability (as part of the thesis process). :contentReference[oaicite:3]{index=3}  
This influenced the system design decisions, especially:
- interaction consistency,
- UI readability and feedback,
- and comfort-aware mechanics.

---

## Build Availability

The full Unity project and playable builds are not publicly available.  
Additional details can be shared on request.

---

## Tech Stack

- **Engine:** Unity
- **Language:** C#
- **Platform:** VR (standalone headset target)

---

## Summary

Solaris Adventure is my flagship example of **gameplay systems work in VR**: structured mission progression, reusable interaction logic, VR-aware UI, and implementation discipline driven by explicit constraints — with additional post-thesis improvements that expanded the project further. :contentReference[oaicite:4]{index=4}

## Screenshots

![Main Hub](images/main-hub.png)
![Solar System Missions Level 3](images/ssm-lvl3.png)
![Orbital Mechanics Missions Level 3](images/omm-lvl3.png)

More screenshots available in **Images** folder

## Media
Gameplay video: https://youtube.com/shorts/7OgnFOWju9Q?feature=share
