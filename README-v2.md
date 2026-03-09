# spec-driven-development-templates

## Purpose

This repository provides **spec-driven development templates** for human and AI collaboration. Teams use these templates to author and maintain linked specifications that guide what to build, how it fits together, and how to verify it.

- **What it is**: Reusable structure and conventions for specs (product, design, system, and delivery artifacts) so that intent, acceptance criteria, and as-built state stay traceable.
- **Who uses it**: Product, design, architecture, security, data, and engineering collaborators—and AI agents that need to read, author, and update specs in alignment with those roles.
- **How to use it**: Copy or adapt the templates for a new effort; author specs by scope (system, domain, component, feature); keep specs linked and update as-built after deploy or milestone.

---

## Quick Start

1. **Copy the template** from `app-spec-template-jle-1` (or create a spec root from this README and the Example folder structure below).
2. **Create root design docs**: product vision, product requirements, user personas, and (as needed) application events and entities.
3. **Create your first epic and feature story**: add an epic (what/why), then a feature story with `spec.md` (definition of done), `plan.md` (which components change), and `tasks.md` (actionable steps).
4. **Link specs** and maintain **as-built**: use explicit references between product → domains → components → tasks; update system-level (and optional per-domain) as-built after each deploy or milestone.
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
- **Component** — A concrete instance (e.g. a service, datastore, UI) within a domain.
- **Epic** — A large unit of work (what and why); contains feature stories and design/research.
- **Feature story** — A deliverable unit (how and who); has `spec.md`, `plan.md`, and `tasks.md`.
- **Task** — A single actionable step in `tasks.md`.

---

## Specification conventions

### Structure and hierarchy

- Specs live **by scope**: system (root), domain, component, and feature. See **Example folder structure** for where each artifact lives.
- Each specification file has a defined purpose; the hierarchy is system → domain → component → feature → task.

### Rules

- **Where specs live**: Organize by scope as in the Example folder structure. System-level and domain-level docs live at root or under domain folders; component docs live under the component; feature docs live under `epics/<epic>/<story>/`.
- **When to read**: At the start of work for that scope; when tracing impact across scopes.
- **How to link**: Use explicit references (file paths, section refs). Maintain traceability: product requirements → domains → components → tasks. Downstream docs reference upstream; upstream docs can reference downstream where useful.
- **When to update**: When the scope changes; when design decisions change; after verification; and when drift is found in drift review. When you update one artifact, consider upstream and downstream references and update them as needed.

### Traceability (git-spec alignment)

- Linked specs and traceability are required. Define required references between files (e.g. feature spec → plan → tasks; component overview → parent domain).
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

- **What exists**: Global system docs (e.g. product vision, requirements, application events/entities), domain docs (per domain), and component docs (overview plus optional docs per component type). Under `specs/`, global system design can include:
  - **services-map/** — `services.md`, `service-dependency-graph.drawio`, `services-integration-use-case-A.data-flow.drawio` (data flow diagrams and service topology).
- **Where they live**: See **Example folder structure**; global at root (and in `network/`, `services-map/`), domains in domain folders, components under their domain.
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

- **Component instance**: Each deployed instance (e.g. service-A, data-store-A) has a set of docs. Some are **required**; others are **optional**.
- **Component type template**: Each component type has a template (scaffold) so that all required files exist even if minimal (e.g. placeholder markdown).

### Required and optional docs per instance

- **Required**: `overview.md`, `configuration.md`, `deployment-strategy.md`, `observability.md`, `security.md`, `testing-strategy.md`.
- **Optional**: `caching.md`, `technology-research.md`, `technology-selection.md`.

### Rules

- **overview.md**: References an architectural diagram that explains where the component lives in the broader system; describes component behavior, public and private state, state management, data lifecycle, and component lifecycle. Link to the parent domain spec.
- Encourage linking component overview to architecture diagrams and parent domain specs.

### Component types (reference)

- **Backend**: Authentication, Authorization, Datastore, Filestore, Service, Cache, SearchIndex, DataPipeline, Orchestration, CronJob, Eventbus (EventProducer, EventConsumer).
- **Frontend**: UI, FileStorage, CDN, Cache.
- Other types as needed.

---

## As-Built

As-Built is a **required** artifact for verification and drift detection.

- **What it is**: A description of the current system state as it is built right now.
- **Placement**: A **system-level** as-built (e.g. root or `docs/as-built.md`) summarizing current system state. **Optional** per-domain as-built docs where useful.
- **Update cadence**: After each deploy or milestone (or both).
- **Use**:
  - Compare as-built to epics and features to evaluate system completeness.
  - Compare as-built to system design documents to evaluate correctness.
  - When drift is found, prompt the developer to determine whether the system or the system design documents need to be updated.

---

## Example folder structure

Abbreviated tree showing where key artifacts live (derived from `app-spec-template-jle-1`):

```
specs/
├── product-vision.spec.md
├── product-requirements.md
├── user-personas.spec.md
├── application-events.spec.md
├── application-entities.spec.md
├── as-built.md
├── network/
│   ├── network.md
│   └── network-topology.drawio
├── services-map/
│   ├── services.md
│   ├── service-dependency-graph.drawio
│   └── services-integration-use-case-A.data-flow.drawio
├── security/
│   ├── security-controls.spec.md
│   ├── authentication/
│   │   ├── authentication.spec.md
│   │   └── technology-selection.spec.md
│   └── authorization/
│       └── authorization.spec.md
├── observability/
│   ├── technology-selection.spec.md
│   ├── logging.spec.md
│   ├── alerts.spec.md
│   └── metrics/
├── epics/
│   └── <epic-name>/
│       └── <story-name>/
│           ├── research.md      (optional)
│           ├── spec.md
│           ├── plan.md
│           └── tasks.md
└── application-stack/           (or backend/, frontend/)
    ├── constitution.md
    ├── frontend/
    │   ├── technology-selection.spec.md
    │   ├── testing-strategy.spec.md
    │   ├── deployment-strategy.spec.md
    │   └── observability.spec.md
    └── backend/
        └── <component-name>/   (e.g. service-A, data-store-A)
            ├── overview.md
            ├── configuration.md
            ├── deployment-strategy.spec.md
            ├── observability.spec.md
            ├── security.md
            ├── testing-strategy.spec.md
            └── (optional: caching.md, technology-research.md, technology-selection.spec.md)
```

---

## Spec-complete checklist

Use this minimal checklist per scope before treating that scope as spec-complete.

| Scope | Checklist |
|-------|-----------|
| **Epic** | Intent stated; acceptance criteria present; definition of done stated; feature stories linked. |
| **Feature** | `spec.md` with definition of done; `plan.md` and `tasks.md` present; acceptance criteria stated. |
| **Domain** | Domain doc present; components listed; links to system design (or root) where relevant. |
| **Component** | `overview.md` and required docs present; linked to parent domain and architecture diagram. |

---

## Alignment with git-spec and bmad

### git-spec

- **Linked specs and traceability**: Required references between files (e.g. feature → plan → tasks; component → parent domain). Document how changes propagate upstream and downstream; keep a clear source of truth (e.g. product requirements → domain → component → tasks).

### bmad

- **Intent and acceptance criteria**: Require intent and acceptance criteria at each scope (epic, feature, domain, component as applicable).
- **Definition of done**: Explicit definition of done at epic and feature scope.
- **Verification**: Encourage verification artifacts (tests, demos, QA notes) and tie them to definition of done.
