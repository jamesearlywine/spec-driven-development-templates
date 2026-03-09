# Application spec template

This template describes the **application-spec** structure used by **example-app-task-tracker** and how to create a new instance for your own app. Specs are co-located near their application scope under a single **spec/** root.

---

## Reference: example-app-task-tracker

The folder **example-app-task-tracker** is a concrete instance of this template for the app **Task Tracker**. Its `spec/` directory layout is the source of truth for the structure below. Use it to copy files or to compare when creating a new instance.

---

## Spec root layout

All specification artifacts live under one root: **spec/** (or **specs/**). That root contains:

- **Governance and root-level design**
  - `constitution.md` — Principles and constraints for the project.
  - `spec-rules.md` — (Optional) Rules for how specs are written and linked.
  - `user-personas.spec.md` — Who the product serves.
  - `application-events.spec.md` — (Optional at root; can live under system-design/application/) What actions happen; sequence/flow.
  - `application-entities.spec.md` — Entities the system operates on; can be at root or under system-design/application/.
  - `application-entities.drawio` — (Optional) Entity relationship diagram.
  - `application-events.drawio` — (Optional) Events/sequence diagram at root.
  - `as-built.md` — (Required once you track state) Current system state for drift review.

- **product-design/** — Product vision, requirements, user flows, and epics.
- **system-design/** — Application, security, observability, deployment, testing.

---

## Product design

```
spec/product-design/
├── product-vision.spec.md      # Why we're building this
├── product-requirements.md     # What to build
├── user-flows/
│   ├── README.md
│   ├── application.figma.md    # (Optional) Figma links
│   └── style-guide.md          # (Optional) Visual/UX guidelines
└── epics/
    └── <epic-name>/
        └── <story-name>/
            ├── research.md     # (Optional)
            ├── spec.md         # Definition of done, acceptance criteria
            ├── plan.md         # Which components change
            └── tasks.md        # Actionable steps
```

Epics are large units of work (what and why); each feature story has spec → plan → tasks (and optional research).

---

## System design

### Application domain

```
spec/system-design/application/
├── backend/
│   ├── technology-selection.spec.md
│   ├── technology-selection.research.md
│   ├── backend-architecture.drawio   # (Optional)
│   ├── services-map.drawio           # (Optional)
│   └── <component-name>/             # e.g. service-A, data-store-A
│       ├── overview.md               # (Optional)
│       ├── constitution.md
│       ├── configuration.md         # or service-configuration.md
│       ├── deployment-strategy.spec.md
│       ├── observability.spec.md
│       ├── testing-strategy.spec.md
│       ├── technology-selection.spec.md
│       ├── technology-selection.research.md
│       ├── application-events.spec.md            # (Optional)
│       ├── application-events.sequence-diagram.drawio  # (Optional)
│       ├── coding-style.spec.md                  # (Optional)
│       └── security.md                           # (Optional)
│   └── cron-driven-processes/        # (Optional) Scheduled/async processes
│       ├── constitution.md
│       ├── deployment-strategy.spec.md
│       ├── observability.spec.md
│       ├── testing-strategy.spec.md
│       ├── technology-selection.spec.md
│       ├── technology-selection.research.md
│       └── process-A/
│           ├── research.md
│           ├── spec.md
│           ├── plan.md
│           └── tasks.md
└── frontend/
    ├── (optional at frontend level: ui-layout.drawio, ui-container drawio)
    └── <frontend-name>/              # e.g. frontend-A (named instance)
        ├── deployment-strategy.spec.md
        ├── observability.spec.md
        ├── testing-strategy.spec.md
        ├── technology-selection.spec.md
        ├── technology-selection.research.md
        ├── ui-application-events.spec.md
        ├── styleguide.md             # (Optional) or style-guide.md
        ├── ui-layout.drawio          # (Optional) UI layout diagram
        ├── ui-general-layout.drawio  # (Optional)
        ├── pages/
        │   └── page-1.requirements.spec.md, .research.md, .wireframe.drawio, .figma.md
        └── components/
            └── component-1.requirements.spec.md, .research.md, .wireframe.drawio
```

### Security

```
spec/system-design/security/
├── security-controls.spec.md
├── security-controls.research.md
├── authentication/
│   ├── authentication.spec.md
│   ├── technology-selection.spec.md
│   └── technology-selection.research.md
├── authorization/
│   ├── authorization.spec.md
│   ├── authorization.model.drawio
│   ├── technology-selection.spec.md
│   └── technology-selection.research.md
└── network/
    └── network.drawio                # optionally network.md
```

### Observability

```
spec/system-design/observability/
├── technology-selection.spec.md
├── technology-selection.research.md
├── logging.spec.md
├── alerts.spec.md
├── metrics/
│   └── metric-A.spec.md
└── dashboards/
    ├── technology-selection.spec.md
    ├── technology-selection.research.md
    └── dashboard-A/
        ├── dashboard-A.spec.md
        └── dashboard-A.wireframe.drawio
```

### Deployment and testing

```
spec/system-design/deployment/
└── deployment-strategy.spec.md

spec/system-design/testing/
├── testing-strategy.spec.md         # (Optional; recommended)
└── e2e-testing-strategy.spec.md
```

---

## How to create a new application-spec instance

Use these steps to create a new app spec from this template (e.g. for a new product or repo).

1. **Create the app folder and spec root**
   - Create a folder for the app (e.g. `my-app-name/`).
   - Inside it, create `spec/` (or `specs/`) as the single root for all spec artifacts.

2. **Add root-level governance and design**
   - Add `spec/constitution.md` (principles and constraints).
   - Optionally add `spec/spec-rules.md` (how specs are written and linked).
   - Add `spec/user-personas.spec.md`.
   - Add `spec/application-events.spec.md` and `spec/application-entities.spec.md` (at root and/or under `spec/system-design/application/` later).
   - Add `spec/as-built.md` when you start tracking current system state (can be a placeholder at first).

3. **Scaffold product-design**
   - Create `spec/product-design/`.
   - Add `product-vision.spec.md` and `product-requirements.md`.
   - Create `product-design/user-flows/` with README.md (and optionally application.figma.md, style-guide.md).
   - Create `product-design/epics/`. For each epic, create `<epic-name>/<story-name>/` with `spec.md`, `plan.md`, `tasks.md` (and optional `research.md`).

4. **Scaffold system-design**
   - Create `spec/system-design/` with subfolders: `application/`, `security/`, `observability/`, `deployment/`, `testing/`.
   - **application/**
     - Add `application-events.spec.md` and `application-entities.spec.md` if not only at root.
     - Optionally add `services-map/` with services.md and drawios when you need service topology; or use backend-level drawios (e.g. backend-architecture.drawio, services-map.drawio).
     - Under **backend/**: add `technology-selection.spec.md` and `technology-selection.research.md`; add backend-level drawios (backend-architecture.drawio, services-map.drawio); for each backend component create `<component-name>/` with constitution, configuration (or service-configuration), deployment-strategy, observability, testing-strategy, technology-selection. Add cron-driven-processes and process subfolders if needed.
     - Under **frontend/**: optionally add frontend-level layout drawios (e.g. ui-layout.drawio); create a named instance (e.g. `<frontend-name>/`) with deployment-strategy, observability, testing-strategy, technology-selection, ui-application-events, and optionally styleguide.md and UI layout drawios (ui-layout.drawio, ui-general-layout.drawio), and `pages/` and `components/` subfolders.
   - **security/**
     - Add security-controls.spec.md (and optional .research); create `authentication/` and `authorization/` with authentication.spec.md, authorization.spec.md, technology-selection; create `network/` with network.drawio (and optionally network.md).
   - **observability/**
     - Add technology-selection, logging.spec.md, alerts.spec.md; create `metrics/` and `dashboards/` with at least one metric and one dashboard if needed.
   - **deployment/**
     - Add deployment-strategy.spec.md.
   - **testing/**
     - Add e2e-testing-strategy.spec.md; optionally add testing-strategy.spec.md (recommended).

5. **Copy from example-app-task-tracker (optional)**
   - To save time, copy the full `example-app-task-tracker/spec/` tree into your new app folder, then rename and edit:
     - Replace placeholders (e.g. frontend-A, service-A, data-store-A, epic and story names) with your app’s names.
     - Update constitution, product-vision, product-requirements, user-personas, and application-events/entities with your content.
     - Add or remove backend/frontend components and epics to match your scope.

6. **Link and maintain**
   - Add explicit references between product requirements → epics/stories → system-design components.
   - Keep `as-built.md` updated after each deploy or milestone for drift review.

---

## Traceability

- **Product → features:** product-requirements and product-vision link to epics and stories.
- **Features → implementation:** Each story’s plan.md and tasks.md reference which system-design components (backend, frontend) change.
- **Application → components:** application-events and application-entities are referenced by backend services and frontend pages/components.
- **As-built:** Compare as-built.md to specs and system design to detect drift; update either code or specs when they diverge.
