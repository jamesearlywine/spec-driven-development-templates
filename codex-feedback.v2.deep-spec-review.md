# Codex Feedback v2 Deep Spec Review

This review starts from `codex-feedback.v2.md` and extends it with a full audit of all example Markdown spec documents under:

- `app-spec-template-jle-1/example-app-task-tracker/spec/**/*.md`

## Scope

- Total Markdown spec documents reviewed: **78**
- Files containing unresolved template comments (`<!-- ... -->`): **65 / 78**
- Empty files: **3 / 78**
- Product design docs: **21**
- System design docs: **52**
- Root-level docs: **5**

## Findings (Ordered by Severity)

1. Critical: The example corpus is mostly unresolved template scaffolding, not a realistic filled example.
- Evidence:
  - Placeholder-heavy docs across almost every area, e.g. [application-events.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/application-events.spec.md:13), [service-A/application-events.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/system-design/application/backend/service-A/application-events.spec.md:11), [frontend-A/technology-selection.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/system-design/application/frontend/frontend-A/technology-selection.spec.md:7)
  - 65/78 files contain unresolved `<!-- ... -->` prompts.
- Impact:
  - New users may treat this as complete guidance, but most documents do not yet demonstrate the expected “done” quality.

2. Critical: Story-level spec/plan/tasks/research docs are duplicated boilerplate and not story-specific.
- Evidence:
  - 16 files under `product-design/epics/*/*/` still use `# Some Other Story – ...`, e.g. [task-list/spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/product-design/epics/task-management/task-list/spec.md:1), [new-user-account-provisioning/plan.md](app-spec-template-jle-1/example-app-task-tracker/spec/product-design/epics/user-management/new-user-account-provisioning/plan.md:1)
  - All four story `spec.md` files are byte-identical; same for all four `plan.md`, `research.md`, and `tasks.md` files.
- Impact:
  - This breaks traceable examples of how one story differs from another and weakens the template’s teaching value.

3. High: Several cross-references are stale or incorrect.
- Evidence:
  - [application-entities.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/application-entities.spec.md:23) points to `application-stack/...` (path does not exist in this example).
  - [application-events.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/application-events.spec.md:24) points to `application-stack/...`.
  - [deployment-strategy.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/system-design/deployment/deployment-strategy.spec.md:20) references `frontend/deployment-strategy.spec.md` (actual file is under `application/frontend/frontend-A/`).
  - [e2e-testing-strategy.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/system-design/testing/e2e-testing-strategy.spec.md:17) and :18 use incorrect relative paths.
  - [dashboards/technology-selection.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/system-design/observability/dashboards/technology-selection.spec.md:13) references `/dashboards/dashboard-A/` with an absolute-like path that is ambiguous in-repo.
  - [service-A/deployment-strategy.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/system-design/application/backend/service-A/deployment-strategy.spec.md:16) references `service-configuration.md`, but the file is `configuration.md`.
- Impact:
  - Navigation is unreliable, and traceability claims are undermined.

4. High: Key docs are empty, leaving major domains undocumented.
- Evidence:
  - [as-built.md](app-spec-template-jle-1/example-app-task-tracker/spec/as-built.md)
  - [frontend-A/styleguide.md](app-spec-template-jle-1/example-app-task-tracker/spec/system-design/application/frontend/frontend-A/styleguide.md)
  - [security/network/network.md](app-spec-template-jle-1/example-app-task-tracker/spec/system-design/security/network/network.md)
- Impact:
  - Critical lifecycle and security architecture artifacts are missing, creating blind spots for implementers.

5. High: Requirement traceability is declared but not actually carried through downstream specs.
- Evidence:
  - Root requirements define `REQ-1..REQ-3` in [product-requirements.md](app-spec-template-jle-1/example-app-task-tracker/spec/product-design/product-requirements.md:11).
  - Story specs still reference placeholder IDs like `REQ-x`, e.g. [task-list/spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/product-design/epics/task-management/task-list/spec.md:16).
  - UI specs also keep placeholder requirement links, e.g. [page-1.requirements.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/system-design/application/frontend/frontend-A/pages/page-1.requirements.spec.md:16), [component-1.requirements.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/system-design/application/frontend/frontend-A/components/component-1.requirements.spec.md:21).
- Impact:
  - The spec system advertises traceability but does not demonstrate an end-to-end traceable chain.

6. Medium: Persona commitments are not translated into architecture-level decisions.
- Evidence:
  - Persona says local-first/offline is a constraint in [user-personas.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/user-personas.spec.md:8).
  - Frontend/data-store specs remain placeholders and do not define local cache/sync/conflict behavior, e.g. [frontend-A/technology-selection.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/system-design/application/frontend/frontend-A/technology-selection.spec.md:7), [data-store-A/technology-selection.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/system-design/application/backend/data-store-A/technology-selection.spec.md:7).
- Impact:
  - Core product constraints are not design-driving in the example.

7. Medium: Security coverage is uneven (authentication is concrete; authorization and controls are mostly placeholders).
- Evidence:
  - Authentication has concrete Cognito/OIDC details in [authentication.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/system-design/security/authentication/authentication.spec.md:3).
  - Authorization model and security controls remain unresolved templates in [authorization.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/system-design/security/authorization/authorization.spec.md:3) and [security-controls.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/system-design/security/security-controls.spec.md:3).
- Impact:
  - Example implies partial security design maturity while authz/control layers are not specified.

8. Medium: Terminology and naming conventions are inconsistent, reducing polish and discoverability.
- Evidence:
  - `style-guide.md` vs `styleguide.md` split between product and system domains.
  - “MockUps”, “pallete”, and “varioua” appear in user-facing docs: [application.figma.md](app-spec-template-jle-1/example-app-task-tracker/spec/product-design/user-flows/application.figma.md:1), [style-guide.md](app-spec-template-jle-1/example-app-task-tracker/spec/product-design/user-flows/style-guide.md:2), [deployment-strategy.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/system-design/deployment/deployment-strategy.spec.md:4).
- Impact:
  - Lowers confidence and increases friction when searching or standardizing docs.

## What Is Strong Already

- Directory breadth is good and maps to a comprehensive product/system/security/observability lifecycle.
- Root product docs provide meaningful seed content:
  - [product-vision.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/product-design/product-vision.spec.md)
  - [product-requirements.md](app-spec-template-jle-1/example-app-task-tracker/spec/product-design/product-requirements.md)
  - [user-personas.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/user-personas.spec.md)
- Authentication technology decision is concrete and reasonably specific:
  - [authentication/technology-selection.spec.md](app-spec-template-jle-1/example-app-task-tracker/spec/system-design/security/authentication/technology-selection.spec.md)

## Recommended Remediation Plan

1. Convert this from “mostly-template” to “true example” by fully completing one vertical slice.
- Suggested slice: `task-management/task-list` + `frontend-A/page-1` + `service-A` + `data-store-A` + core observability/security links.
- Goal: demonstrate complete traceability (`vision -> requirements -> story spec -> plan -> tasks -> system specs`).

2. Fix all stale path references and enforce a link check in CI.
- Add a markdown link/reference checker (including backtick path validation for local docs).
- Ensure all examples resolve from repository root.

3. Remove duplicated generic story docs.
- Replace `Some Other Story` files with unique, story-specific examples for each included story.
- Keep one intentionally skeletal sample only if clearly labeled as such.

4. Fill currently empty critical docs.
- `as-built.md`: document known divergence policy and update cadence.
- `security/network/network.md`: summarize trust boundaries and ingress/egress rules.
- `frontend-A/styleguide.md`: define concrete tokens/accessibility conventions used by example pages.

5. Standardize naming and editorial quality.
- Choose one naming convention (`style-guide` or `styleguide`) and apply it consistently.
- Fix spelling/grammar issues and normalize title casing across docs.

6. Add completion metadata to reduce ambiguity.
- Add front matter fields per spec: `status`, `owner`, `last-reviewed`, `traceability-ids`.
- Mark intentionally incomplete docs explicitly as `status: draft-template`.

## Delta vs `codex-feedback.v2.md`

The original v2 feedback correctly identified strategic alignment gaps with Spec Kit/BMAD and explicitly noted limited scope. This deep review confirms those strategic points and adds concrete document-level findings:

- Most example docs are still unresolved template scaffolds.
- Story artifacts are duplicated and not differentiated.
- Several cross-references are broken.
- Traceability claims are not operationalized end-to-end.

