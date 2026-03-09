# spec-driven-development-templates

## Purpose

This repository provides **spec-driven development templates** for human and AI collaboration. Teams use these templates to author and maintain linked specifications that guide what to build, how it fits together, and how to verify it.

- **What it is**: Reusable structure and conventions for specs (product, design, system, and delivery artifacts) so that intent, acceptance criteria, and as-built state stay traceable.
- **Who uses it**: Product, design, architecture, security, data, and engineering collaborators—and AI agents that need to read, author, and update specs in alignment with those roles.
- **How to use it**: Copy or adapt the templates for a new effort; author specs by scope (system, domain, component, feature); keep specs linked and update as-built after deploy or milestone.

---

## Quick Start

1. **Copy the template** from `app-spec-template-jle-1` (or create a spec root from this README and the Example folder structure below).
2. **Create product-design/** with product vision, product requirements, and (as needed) user-flows. Create root-level user personas and (optionally) application-events and application-entities at spec root or under system-design/application.
3. **Create your first epic and feature story** under product-design/epics/: add an epic (what/why), then a feature story with `spec.md` (definition of done), `plan.md` (which components change), and `tasks.md` (actionable steps).
4. **Link specs** and maintain **as-built**: use explicit references between product → domains → components → tasks; add `as-built.md` at spec root when you start tracking current state; update after each deploy or milestone.
5. **Use the Spec-complete checklist** (below) before treating a scope as spec-complete.

---

## Spec lifecycle

Work flows through these phases; each phase ties to concrete artifacts:

| Phase | Artifacts |
|-------|-----------|
| **Discovery** | Research, design decisions (e.g. `research.md`, decision docs). |
| **Spec** | `spec.md`, definition of done, acceptance criteria. |
| **Plan** | `plan.md` (which system components require change). |
| **Tasks** | `tasks.md` (granular steps to update, test, deploy). |
| **Build** | Implementation. |
| **Verify** | Tests, demos, QA notes. |
| **As-Built** | `as-built.md` describing current system state. |
| **Drift Review** | Compare as-built to specs and system design; update either the system or the design docs when drift is found. |

---

## Glossary

Use these terms consistently so that epic, feature story, domain, and component are unambiguous.

- **System** — The entire product or system.
- **Domain** — A major sub-system (e.g. Security, Observability, Application stack).
- **Component** — A concrete instance (e.g. a service, datastore, frontend app) within a domain.
- **Epic** — A large unit of work (what and why); contains feature stories and design/research.
- **Feature story** — A deliverable unit (how and who); has `spec.md`, `plan.md`, and `tasks.md`.
- **Task** — A single actionable step in `tasks.md`.

---

## Specification conventions

### Structure and hierarchy

- Specs live **by scope**: system (root), domain, component, and feature. See **Example folder structure** for where each artifact lives.
- Each specification file has a defined purpose; the hierarchy is system → domain → component → feature → task.

### Rules

- **Where specs live**: Organize by scope as in the Example folder structure. Product vision and product requirements live under **product-design/**; user-personas at spec root; governance (constitution, spec-rules) at spec root; application-events and application-entities at spec root and/or under **system-design/application/**; network under **system-design/security/network/**; deployment and testing under **system-design/deployment/** and **system-design/testing/**; component docs under the component; feature docs under **product-design/epics/<epic>/<story>/**.
- **When to read**: At the start of work for that scope; when tracing impact across scopes.
- **How to link**: Use explicit references (file paths, section refs). Maintain traceability: product requirements → domains → components → tasks. Downstream docs reference upstream; upstream docs can reference downstream where useful.
- **When to update**: When the scope changes; when design decisions change; after verification; and when drift is found in drift review. When you update one artifact, consider upstream and downstream references and update them as needed.

### Traceability (git-spec alignment)

- Linked specs and traceability are required. Define required references between files (e.g. feature spec → plan → tasks; component overview or service-configuration → parent domain).
- When changes propagate: downstream changes (e.g. new feature) may require updates to plan, tasks, and eventually as-built; upstream changes (e.g. product requirement) may require updates to epics, stories, and component docs. Treat product requirements and system design as source of truth for *what* and *how the system is intended to work*; as-built is source of truth for *what is actually built*.

---

## Product management

### Requirements artifacts

- **Epics** (what and why): Contain user-oriented and tech-oriented stories, design documents, research, and decisions. Require **acceptance criteria** and **definition of done** at epic scope.
- **Feature stories** (how and who): May have optional `research.md` (may reference research at epic scope). Require **acceptance criteria** and **definition of done** at feature scope.
- **Design, research, and decisions**: Kept with the epic or feature; linked from spec and plan as needed.

### Delivery artifacts

- **plan.md** — Identifies which system components require update for the feature.
- **tasks.md** — Granular set of actionable steps to update, test, and deploy each component.
- **Test cases / E2E** — Part of definition of done; verification artifacts (tests, demos, QA notes) are encouraged at each scope.

---

## System design documents

- **What exists**: Product vision and product requirements under **product-design/**; application-level docs (application-events, application-entities, optionally **services-map/**) under **system-design/application/** or at spec root; domain docs (security, observability, deployment, testing) under **system-design/**; component docs per component.
  - **application-events.spec.md**, **application-entities.spec.md**: Can live at spec root or under system-design/application/ (optionally with application-entities.drawio at root).
  - **services-map/** (optional): Under system-design/application/, add when needed — `services.md`, `service-dependency-graph.drawio`, `services-integration-use-case-A.data-flow.drawio` for data flow and service topology.
  - **network**: Under **system-design/security/network/** — `network.drawio` (optionally `network.md`). Not at spec root.
  - **deployment**: **system-design/deployment/** — e.g. deployment-strategy.spec.md.
  - **testing**: **system-design/testing/** — e.g. testing-strategy.spec.md, e2e-testing-strategy.spec.md.
  - **observability**: Includes **dashboards/** (e.g. dashboard-A with dashboard-A.spec.md, dashboard-A.wireframe.drawio) in addition to technology-selection, logging, alerts, metrics.
- **Where they live**: See **Example folder structure**; product-design/ for vision, requirements, user-flows, epics; system-design/ for application, security, observability, deployment, testing; components under their domain.
- **When to read**: Before changing a domain or component; when doing impact analysis for a feature.
- **When to update**: When a new feature touches that area, when doing a major refactor, or when drift is found during drift review.

---

## Application domains

Domains are sub-systems that contain system components.

- **Generalized domains**: Reusable capabilities (e.g. `document-templating-service`) that are not specific to one product.
- **Application domains**: Product-specific (e.g. `bespoke-document-generation-service`) that consume or depend on generalized domains.

**Dependency links**: Document dependencies between domains explicitly. Example: an application domain (e.g. bespoke-document-generation-service) depends on a generalized domain (e.g. document-templating-service). Record this in the domain overview or architecture diagram and, where useful, in a short dependency section (e.g. "Depends on: document-templating-service").

---

## System components

### Component instance vs component type template

- **Component instance**: Each deployed instance (e.g. service-A, data-store-A, frontend-A) has a set of docs. Some are **required** or recommended; others are **optional**.
- **Component type template**: Each component type has a template (scaffold) so that key files exist even if minimal (e.g. placeholder markdown).

### Backend components

- **Required or recommended**: deployment-strategy.spec.md, observability.spec.md, testing-strategy.spec.md; **service-configuration.md** (or configuration.md); constitution.md per component or area. **overview.md** and **security.md** are recommended; add when needed.
- **Optional**: technology-selection.spec.md, technology-selection.research.md, caching.md, technology-research.md. Service-specific: application-events.spec.md, application-events.sequence-diagram.drawio, coding-style.spec.md, openapi, system-events drawio.
- **Cron/process components**: e.g. cron-driven-processes/process-A/ can have spec.md, plan.md, tasks.md, research.md (story-style) where the process is a unit of delivery.

### Frontend components (named instances)

- **Named frontend instances** (e.g. frontend-A): Each frontend app is a component under system-design/application/frontend/<frontend-name>/.
- **Per instance**: deployment-strategy.spec.md, observability.spec.md, testing-strategy.spec.md, technology-selection.spec.md, technology-selection.research.md, ui-application-events.spec.md; **pages/** (e.g. page-1 with requirements.spec.md, research.md, wireframe.drawio, figma.md); **components/** (e.g. component-1 with requirements.spec.md, research.md, wireframe.drawio).

### Rules

- **overview.md** (when present): References an architectural diagram that explains where the component lives in the broader system; describes component behavior, public and private state, state management, data lifecycle, and component lifecycle. Link to the parent domain spec.
- Encourage linking component overview (or service-configuration) to architecture diagrams and parent domain specs.

### Component types (reference)

- **Backend**: Authentication, Authorization, Datastore, Filestore, Service, Cache, SearchIndex, DataPipeline, Orchestration, CronJob, Eventbus (EventProducer, EventConsumer), cron-driven-processes.
- **Frontend**: Named frontend instances (e.g. frontend-A) with pages and components.
- Other types as needed.

---

## As-Built

As-Built is a **required** artifact for verification and drift detection.

- **What it is**: A description of the current system state as it is built right now.
- **Placement**: A **system-level** as-built at spec root (e.g. `as-built.md`). Add when you start tracking current state. **Optional** per-domain as-built docs where useful.
- **Update cadence**: After each deploy or milestone (or both).
- **Use**:
  - Compare as-built to epics and features to evaluate system completeness.
  - Compare as-built to system design documents to evaluate correctness.
  - When drift is found, prompt the developer to determine whether the system or the system design documents need to be updated.

---

## Example folder structure

Tree reflects `app-spec-template-jle-1/example-app-task-tracker/spec`.

```
spec/
├── constitution.md
├── user-personas.spec.md
├── application-events.spec.md
├── application-entities.spec.md
├── application-entities.drawio        (optional)
├── as-built.md
├── product-design/
│   ├── product-vision.spec.md
│   ├── product-requirements.md
│   ├── user-flows/
│   │   ├── README.md
│   │   ├── application.figma.md
│   │   └── style-guide.md
│   └── epics/
│       └── <epic-name>/
│           └── <story-name>/
│               ├── research.md        (optional)
│               ├── spec.md
│               ├── plan.md
│               └── tasks.md
└── system-design/
    ├── application/
    │   ├── application-events.spec.md
    │   ├── application-entities.spec.md
    │   ├── services-map/              (optional; add when needed)
    │   │   ├── services.md
    │   │   ├── service-dependency-graph.drawio
    │   │   └── services-integration-use-case-A.data-flow.drawio
    │   ├── backend/
    │   │   ├── technology-selection.spec.md
    │   │   ├── technology-selection.research.md
    │   │   ├── service-A/             (or data-store-A, etc.)
    │   │   │   ├── constitution.md
    │   │   │   ├── service-configuration.md
    │   │   │   ├── deployment-strategy.spec.md
    │   │   │   ├── observability.spec.md
    │   │   │   ├── testing-strategy.spec.md
    │   │   │   ├── technology-selection.spec.md
    │   │   │   ├── technology-selection.research.md
    │   │   │   ├── application-events.spec.md
    │   │   │   ├── application-events.sequence-diagram.drawio
    │   │   │   ├── coding-style.spec.md
    │   │   │   └── (optional: overview.md, security.md)
    │   │   ├── data-store-A/
    │   │   │   ├── constitution.md
    │   │   │   ├── deployment-strategy.spec.md
    │   │   │   ├── observability.spec.md
    │   │   │   ├── testing-strategy.spec.md
    │   │   │   ├── technology-selection.spec.md
    │   │   │   ├── technology-selection.research.md
    │   │   │   └── entity-relationship-diagram.drawio
    │   │   └── cron-driven-processes/
    │   │       ├── constitution.md
    │   │       ├── deployment-strategy.spec.md
    │   │       ├── observability.spec.md
    │   │       ├── testing-strategy.spec.md
    │   │       ├── technology-selection.spec.md
    │   │       ├── technology-selection.research.md
    │   │       └── process-A/
    │   │           ├── research.md
    │   │           ├── spec.md
    │   │           ├── plan.md
    │   │           └── tasks.md
    │   └── frontend/
    │       └── frontend-A/            (named frontend instance)
    │           ├── deployment-strategy.spec.md
    │           ├── observability.spec.md
    │           ├── testing-strategy.spec.md
    │           ├── technology-selection.spec.md
    │           ├── technology-selection.research.md
    │           ├── ui-application-events.spec.md
    │           ├── pages/
    │           │   └── page-1.requirements.spec.md, page-1.research.md, page-1.wireframe.drawio, page-1.figma.md
    │           └── components/
    │               └── component-1.requirements.spec.md, component-1.research.md, component-1.wireframe.drawio
    ├── security/
    │   ├── security-controls.spec.md
    │   ├── security-controls.research.md
    │   ├── authentication/
    │   │   ├── authentication.spec.md
    │   │   ├── technology-selection.spec.md
    │   │   └── technology-selection.research.md
    │   ├── authorization/
    │   │   ├── authorization.spec.md
    │   │   ├── authorization.model.drawio
    │   │   ├── technology-selection.spec.md
    │   │   └── technology-selection.research.md
    │   └── network/
    │       └── network.drawio          (optionally network.md)
    ├── observability/
    │   ├── technology-selection.spec.md
    │   ├── technology-selection.research.md
    │   ├── logging.spec.md
    │   ├── alerts.spec.md
    │   ├── metrics/
    │   │   └── metric-A.spec.md
    │   └── dashboards/
    │       ├── technology-selection.spec.md
    │       ├── technology-selection.research.md
    │       └── dashboard-A/
    │           ├── dashboard-A.spec.md
    │           └── dashboard-A.wireframe.drawio
    ├── deployment/
    │   └── deployment-strategy.spec.md
    └── testing/
    │   ├── testing-strategy.spec.md
    │   └── e2e-testing-strategy.spec.md
implementation/
├── frontend/
├── backend/
```

---

## Spec-complete checklist

Use this minimal checklist per scope before treating that scope as spec-complete.

| Scope | Checklist |
|-------|-----------|
| **Epic** | Intent stated; acceptance criteria present; definition of done stated; feature stories linked. |
| **Feature** | `spec.md` with definition of done; `plan.md` and `tasks.md` present; acceptance criteria stated. |
| **Domain** | Domain doc present; components listed; links to system design (or root) where relevant. |
| **Component** | Required docs present (e.g. deployment-strategy, observability, testing-strategy; service-configuration or configuration); linked to parent domain and architecture diagram. overview.md and security.md recommended where applicable. |

---

## Alignment with git-spec and bmad

### git-spec

- **Linked specs and traceability**: Required references between files (e.g. feature → plan → tasks; component → parent domain). Document how changes propagate upstream and downstream; keep a clear source of truth (e.g. product requirements → domain → component → tasks).

### bmad

- **Intent and acceptance criteria**: Require intent and acceptance criteria at each scope (epic, feature, domain, component as applicable).
- **Definition of done**: Explicit definition of done at epic and feature scope.
- **Verification**: Encourage verification artifacts (tests, demos, QA notes) and tie them to definition of done.
