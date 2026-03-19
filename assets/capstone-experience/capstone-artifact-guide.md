# Ozora Capstone Experience Artifact Guide

## Recommended Themes Based on the Codebase

1. Architecture
   Supported strongly by the coexistence of a SwiftUI app, Express backend, Socket.io rooms, admin dashboard proxy, JSON-backed persistence, and demo scripts.
2. UI and Ordering Flow
   Supported strongly by the five-tab SwiftUI structure, automatic session creation, live tab updates, and the staged order simulator.
3. Data Model and Schema
   Supported strongly by the concrete JSON collections and matching Swift models for users, sessions, tabs, loyalty, promotions, menu, and receipts.
4. Authentication and Access Boundaries
   Supported moderately to strongly by the mock OTP login flow, `AuthService`, `AppStorage`, auto session start, and the separate admin surface.
5. Testing, Feedback, and Revision Evidence
   Supported strongly by the demo checklist plus `simulateOrder.js`, `simulateCheckout.js`, `resetDemoFlow.js`, and the admin dashboard's history-derived analytics.

## Theme Mapping

| Theme | Early Artifact | Revised / Implemented Artifact |
| --- | --- | --- |
| Architecture | `architecture/architecture-early-concept.mmd` | `architecture/architecture-implemented.mmd` |
| UI and ordering | `ui-ordering/ui-early-concept.mmd` | `ui-ordering/ordering-workflow-implemented.mmd` |
| Data model | `data-model/data-model-early-concept.mmd` | `data-model/data-model-implemented.mmd` |
| Authentication and access | `auth-access/auth-early-concept.mmd` | `auth-access/auth-implemented.mmd` |
| Testing and revision | `testing-revision/testing-early-manual.mmd` | `testing-revision/testing-revised-demo-loop.mmd` |

## Figure Titles and Captions

### Architecture

**Figure A1. Early Concept Architecture for Ozora**
This diagram shows the likely first workable architecture implied by the current codebase: a mobile-first prototype centered on REST calls into a single Express API with JSON files as storage and manual operational checks.

**Figure A2. Implemented Multi-Surface Architecture**
This diagram shows the delivered architecture: a SwiftUI client, admin dashboard, Express API, Socket.io event layer, reusable backend services, file-backed persistence, and simulator scripts that drive repeatable demonstrations.

### UI and Ordering Flow

**Figure B1. Early Mobile Information Architecture**
This artifact shows the early product focus on the guest journey from login to the live tab, with loyalty, promotions, and history still acting like secondary extensions to the core dining use case.

**Figure B2. Implemented Ordering Workflow Across App, API, and Demo Scripts**
This sequence captures the real implemented ordering flow from login through session creation, staged webhook updates, real-time tab refreshes, and checkout-driven receipt generation.

### Data Model

**Figure C1. Early Conceptual Data Model**
This model shows the minimum viable entities required to prove the concept: users, dining sessions, tabs, loyalty accounts, and targeted promotions.

**Figure C2. Implemented File-Backed Data Model**
This diagram reflects the schema actually present in the repository, including embedded line items, receipt history, rewards, menu data, and richer session lifecycle fields.

### Authentication and Access

**Figure D1. Early Access Assumption**
This artifact shows the initial assumption that a lightweight customer sign-in flow would unlock the core experience while staff operations lived on a separate surface.

**Figure D2. Implemented Prototype Authentication and Access Flow**
This sequence documents the implemented login path, persistent client-side auth state, automatic session bootstrapping, WebSocket room subscription, and the separate admin boundary.

### Testing and Revision

**Figure E1. Early Manual Validation Loop**
This artifact shows the original validation mindset: run the system, trigger an order, observe the UI, and iterate manually.

**Figure E2. Revised Deterministic Demo and Validation Loop**
This diagram shows the stronger revision workflow that emerged in the repo: reset state, simulate a session, simulate orders, simulate checkout, and verify downstream analytics and loyalty effects.

## Annotation Text for the Portfolio Page

### Architecture

**Before Figure A1**
The project started as a mobile-first restaurant prototype, so the earliest architecture was likely centered on proving that a customer app could log in, start a dining session, and read a live tab from a simple API. The current repository still shows that foundation in the clean separation between the iOS client, the Express routes, and the file-backed `dataService`.

What it shows: A focused first-pass architecture with a single client, a single backend, and JSON persistence.
Stage: Early concept inferred from the present structure.
What changed: The architecture expanded into a multi-surface system with operational tooling, WebSocket events, and repeatable simulation scripts.
Why it mattered: That expansion made the project demonstrable as a system instead of just a mobile mockup.
What I learned: A compelling capstone needs both a usable customer interface and a believable operational backbone.

**Before Figure A2**
As the implementation matured, the project moved beyond a simple request-response prototype and into a more credible smart dining platform. The revised architecture shows how the customer app, backend services, admin dashboard, and simulation scripts work together around shared data and real-time events.

What it shows: The implemented architecture present in the codebase today.
Stage: Revised and implemented version.
What changed: Socket.io rooms, the admin proxy dashboard, and the simulator scripts were added around the original REST core.
Why it mattered: Those additions made the ordering experience observable, repeatable, and easier to explain to evaluators.
What I learned: Real-time features are only convincing when the surrounding tooling makes them visible and testable.

### UI and Ordering Flow

**Before Figure B1**
The strongest user story in Ozora is the in-restaurant tab experience, so the earliest interface concept was likely organized around a short path from sign-in to a live order view. The final app still reflects that priority because the Live Tab remains the most behavior-rich screen in the client.

What it shows: A likely early mobile IA focused on the primary customer task.
Stage: Early concept inferred from the implemented screen structure.
What changed: Supporting screens for loyalty, promotions, and history became first-class tabs instead of remaining secondary ideas.
Why it mattered: The experience evolved from a single-feature demo into a broader customer journey.
What I learned: Even when one feature leads the story, surrounding context screens make the product feel complete and believable.

**Before Figure B2**
Once the project had a reliable backend and simulator, the ordering flow could be expressed as a real end-to-end system instead of a static screen sequence. This implemented workflow shows how the app now reacts to staged order updates and closes the loop with checkout and receipt generation.

What it shows: The real implemented ordering workflow across client, API, WebSocket events, and supporting scripts.
Stage: Revised and implemented version.
What changed: The flow moved from a mostly screen-based concept to an event-driven interaction backed by session creation and webhook updates.
Why it mattered: It demonstrates that the interface is connected to system state rather than acting like a disconnected mockup.
What I learned: Workflow credibility comes from state transitions and side effects, not just polished UI screens.

### Data Model

**Before Figure C1**
A restaurant platform can become over-modeled quickly, so the early data design needed to stay small enough to support a prototype. The core relationships between user, session, tab, loyalty account, and promotion represent the minimum data needed to prove personalized dining behavior.

What it shows: The likely initial conceptual schema for the first working prototype.
Stage: Early concept inferred from the current entity boundaries.
What changed: Receipt history, menu structure, rewards, embedded order items, and richer lifecycle fields were added later.
Why it mattered: Those additions turned a transient demo into a system that could show continuity across visits.
What I learned: Schema growth should follow user scenarios, especially when moving from a one-session demo to a customer relationship story.

**Before Figure C2**
The implemented schema in the repository is richer than a simple tab tracker. It now captures the full story of a dining visit: menu context, tab state, checkout results, loyalty changes, and historical receipts that can feed both the customer app and the admin dashboard.

What it shows: The actual file-backed data model implemented in `backend/data` and mirrored in the Swift models.
Stage: Revised and implemented version.
What changed: The model grew to preserve historical outcomes, reward logic, and menu-backed item structure.
Why it mattered: That richer schema supports more portfolio themes because it connects ordering, analytics, loyalty, and history.
What I learned: Data modeling became the bridge between isolated features and a coherent platform story.

### Authentication and Access

**Before Figure D1**
Ozora is clearly a prototype, so the earliest access model did not need production-grade identity management. What mattered first was protecting the customer flow behind a sign-in step and keeping the staff workflow conceptually separate.

What it shows: The early access assumption behind the project.
Stage: Early concept inferred from the product split between customer and operator surfaces.
What changed: The project implemented a mock OTP flow, persistent local auth state, and automatic session setup after login.
Why it mattered: This made the prototype feel like a real app with continuity between screens and visits.
What I learned: Even a mocked authentication layer changes how seriously the rest of the experience is perceived.

**Before Figure D2**
The implemented access flow is intentionally lightweight, but it is still specific enough to document as part of the portfolio. The repo shows a complete prototype path from sign-in to stored customer state, followed by automatic session creation and room-based real-time updates.

What it shows: The real login and access boundaries present in the codebase.
Stage: Revised and implemented version.
What changed: The project moved from a generic sign-in idea to a concrete mocked OTP workflow plus client-side persistence.
Why it mattered: This tightened the connection between authentication, session state, and the core ordering experience.
What I learned: Access flows influence system design far beyond the login screen, especially when real-time subscriptions depend on identity and session context.

### Testing and Revision

**Before Figure E1**
Early validation for this project was mainly experiential: start the stack, trigger an order, and visually confirm that the tab changed. That kind of manual loop is common in prototypes, and the README checklist still preserves that phase of the project.

What it shows: The likely original validation pattern before the demo tooling became more disciplined.
Stage: Early concept inferred from the setup and testing instructions.
What changed: The project added reset and checkout scripts that make demos and verification more repeatable.
Why it mattered: Repeatability is important in a capstone because it lets feedback focus on product behavior rather than setup luck.
What I learned: The difference between a fragile demo and a strong artifact is often the quality of the validation loop around it.

**Before Figure E2**
The revised validation loop is one of the strongest hidden artifacts in the repository because it shows engineering maturity. Instead of only proving that orders can appear, the project now proves that an end-to-end visit can be reset, replayed, checked out, and reflected in history, loyalty, and admin analytics.

What it shows: The implemented revision loop backed by actual npm scripts and downstream data updates.
Stage: Revised and implemented version.
What changed: Validation expanded from manual UI observation to a deterministic multi-step demo workflow.
Why it mattered: This created much stronger evidence for stakeholder feedback, presentation readiness, and system completeness.
What I learned: Good demo tooling is part of the product story because it proves the system can survive repeated evaluation.

## Suggested Folder Structure

This is the structure already created in the repo:

```text
assets/
  capstone-experience/
    architecture/
      architecture-early-concept.mmd
      architecture-implemented.mmd
    ui-ordering/
      ui-early-concept.mmd
      ordering-workflow-implemented.mmd
    data-model/
      data-model-early-concept.mmd
      data-model-implemented.mmd
    auth-access/
      auth-early-concept.mmd
      auth-implemented.mmd
    testing-revision/
      testing-early-manual.mmd
      testing-revised-demo-loop.mmd
    capstone-artifact-guide.md
```

## Notes

- The early artifacts are informed inferences, not fabricated history. They are grounded in the current project structure, feature priorities, repository documentation, and the implemented code boundaries.
- The revised artifacts map directly to code currently present in the repository.
- Mermaid source files are ready for reuse in documentation, slide decks, or future SVG export workflows.
