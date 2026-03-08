---
name: Apply feedback to README v2
overview: "Apply all editorial suggestions from README-v1.codex-feedback.md to README-v1.md and write the result as README-v2.md: add purpose, lifecycle, glossary, concrete rules, Quick Start, example folder structure, checklists, and git-spec/bmad alignment; fix typos and rephrase questions as guidance. As-Built: system-level summary plus optional per-domain as-built."
todos: []
isProject: false
---

# Apply Codex feedback to README → README-v2.md

## Sources

- **Feedback**: README-v1.codex-feedback.md
- **Source doc**: README-v1.md
- **Output**: `README-v2.md`
- **As-Built placement** (per your choice): system-level summary + optional per-domain as-built

## Document shape for README-v2

1. **Purpose statement** (new, near top)
  - What this repo is: spec-driven development templates for human + AI collaboration.
  - Who uses it: product, design, architecture, security, data, engineers + AI agents.
  - How to use it: author and maintain linked specs; apply templates on new efforts.
2. **Quick Start** (new)
  - 3–5 steps: e.g. (1) Copy template from `app-spec-template-jle-1` or create from this README, (2) Create root design docs (vision, requirements, personas), (3) Create first epic and feature story with spec → plan → tasks, (4) Link specs and keep as-built updated, (5) Use checklist before considering a scope "spec complete."
3. **Spec lifecycle** (new section)
  - Discovery → Spec → Plan → Tasks → Build → Verify → As-Built → Drift Review.
  - Tie to artifacts: Discovery (research, decisions), Spec (spec.md, definition of done), Plan (plan.md), Tasks (tasks.md), Build (implementation), Verify (tests, demos, QA), As-Built (as-built.md), Drift Review (compare as-built to specs and design docs; update code or docs).
4. **Glossary** (new)
  - **System**: entire product/system.
  - **Domain**: major sub-system (e.g. Security, Observability, Application stack).
  - **Component**: concrete instance (e.g. a service, datastore, UI).
  - **Epic**: large unit of work (what/why); contains feature stories and design/research.
  - **Feature story**: deliverable unit (how/who); has spec.md, plan.md, tasks.md.
  - **Task**: single actionable step in tasks.md.
  - Align terms so "epic," "feature story," "domain," "component" are used consistently.
5. **Specification conventions** (rewrite of current §1)
  - Fix: "heirarchy" → "hierarchy."
  - Replace vague bullets with **concrete rules**:
    - Where specs live: by scope (system/domain/component/feature) as in Example folder structure.
    - When to read: at start of work for that scope; when tracing impact.
    - How to link: explicit references (file paths, section refs); traceability from product → domains → components → tasks.
    - When to update: when scope changes; when design decisions change; after verification; when drift is found.
  - Add brief git-spec alignment: linked specs, required references between files, how changes propagate, source-of-truth rules.
6. **Product management** (split and tighten per feedback)
  - **Requirements artifacts**: epics (what/why), stories (user + tech), research, design decisions. Acceptance criteria required at epic and feature scope (bmad). Definition of done at epic and feature.
  - **Delivery artifacts**: plan.md (which components to change), tasks.md (actionable steps), test cases / E2E as definition of done.
  - Fix: "referenece" → "reference."
  - Rephrase as declarative rules, not questions.
7. **System design documents** (replace questions with list)
  - What exists: global system docs, domain docs, component docs (overview + optional docs).
  - Where they live: see Example folder structure; by domain and component.
  - When to read: before changing a domain/component; when doing impact analysis.
  - When to update: new feature touching that area, major refactor, or drift found in drift review.
8. **Application domains** (clarify)
  - Generalized domains: reusable capabilities (e.g. document-templating-service).
  - Application domains: product-specific (e.g. bespoke-document-generation-service).
  - Add one short example of dependency link: application domain depends on generalized domain; document where and how (e.g. in domain overview or architecture diagram).
9. **System components** (separate instance vs template; mandatory vs optional)
  - **Component instance**: each instance has required vs optional docs.
    - Required (or "mandatory"): overview.md, configuration.md, deployment-strategy.md, observability.md, security.md, testing-strategy.md (or equivalent list from current README).
    - Optional: caching.md, technology-research.md, technology-selection.md (or per current list).
  - **Component type template**: each type has a template (scaffold) so non-optional files exist even if minimal.
  - Rules: overview.md references architecture diagram and parent domain; link to parent domain spec.
  - Keep current component-type list (Backend: Auth, Datastore, Service, etc.; Frontend: UI, FileStorage, etc.) as reference.
10. **As-Built** (elevate to required artifact)
  - **Required**: As-Built is required for verification and drift detection.
    - **Placement**: system-level as-built (e.g. root or `docs/` as-built.md) summarizing current system state; optional per-domain as-built where useful.
    - **Update cadence**: after each deploy or milestone (or both).
    - **Use**: compare to epics/features for completeness; compare to system design for correctness; when drift is found, prompt to update either system or design docs.
11. **Alignment with git-spec** (short subsection or bullets)
  - Linked specs and traceability; required references between files; how changes propagate upstream/downstream; source of truth (e.g. product requirements → domain → component → tasks).
12. **Alignment with bmad** (short subsection or bullets)
  - Intent + acceptance criteria at each scope; explicit definition of done at epic and feature; verification artifacts (tests, demos, QA notes).
13. **Example folder structure** (new)
  - Short tree derived from app-spec-template-jle-1/app-spec.template.md and the example app, showing:
    - Root: product-vision, product-requirements, user-personas, application-events/entities, as-built.md.
    - Domains: e.g. security/, observability/, application-stack/.
    - Features: epics/<epic>/<story>/ with research.md, spec.md, plan.md, tasks.md.
    - Components: under domains with overview, configuration, deployment-strategy, etc.
    - Keep it one concise tree (abbreviated) so readers see where each artifact lives.
14. **Spec-complete checklist** (new)
  - Minimal checklist per scope, e.g.
    - Epic: intent, acceptance criteria, definition of done, stories linked.
    - Feature: spec.md with DoD, plan.md, tasks.md, acceptance criteria.
    - Domain: domain doc present, components listed, links to system design.
    - Component: overview, required docs present, linked to parent domain and diagram.

## Order of sections in README-v2 (suggested)

- Title + purpose statement
- Quick Start
- Spec lifecycle
- Glossary
- Specification conventions
- Product management (Requirements artifacts / Delivery artifacts)
- System design documents
- Application domains
- System components
- As-Built
- Example folder structure
- Spec-complete checklist
- Alignment (git-spec, bmad) — can be short end matter

## Typos to fix (from README-v1)

- "heirarchy" → "hierarchy"
- "referenece" → "reference"

## What to avoid

- Leaving rhetorical questions; use declarative rules or "When X, do Y."
- Using epic/feature/domain/component interchangeably without glossary.
- Omitting As-Built from the example tree (show at least system-level as-built.md).

No code or repo layout changes—only producing the single new file **README-v2.md** with the above content applied.
