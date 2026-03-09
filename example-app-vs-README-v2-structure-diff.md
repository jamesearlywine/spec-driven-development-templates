# Structure diff: example-app-task-tracker-spec vs README-v2.md

This document compares the **actual** folder/file structure of `app-spec-template-jle-1/example-app-task-tracker-spec` with the **Example folder structure** described in README-v2.md, so you can align the spec template with the spec template spec.

---

## 1. Root layout

| Aspect | README-v2.md | example-app-task-tracker-spec |
|--------|--------------|-------------------------------|
| **Root** | Single `specs/` prefix; all artifacts under one tree | **Three top-level folders**: `product-design/`, `system-design/`, `implementation/` (no `specs/` wrapper) |

README-v2 assumes one root (`specs/`). The example splits into product-design, system-design, and implementation.

---

## 2. Product / application-level docs

| README-v2 (specs/) | example-app | Match / note |
|--------------------|-------------|--------------|
| product-vision.spec.md | product-design/product-vision.spec.md | Path: under product-design, not at root |
| product-requirements.md | product-design/product-requirements.md | Path: under product-design |
| user-personas.spec.md | user-personas.spec.md at **repo root** | Path: README has under specs root; example has at repo root |
| application-events.spec.md | system-design/application/application-events.spec.md | Path: under system-design/application, not at root |
| application-entities.spec.md | system-design/application/application-entities.spec.md | Path: under system-design/application |
| as-built.md | **Missing** | Example has no as-built.md |

---

## 3. network/

| README-v2 | example-app | Match / note |
|-----------|-------------|--------------|
| specs/network/network.md | system-design/security/network/network.md | Same files; **path**: under security, not under specs root |
| specs/network/network-topology.drawio | system-design/security/network/network-topology.drawio | Same files; path differs |

---

## 4. services-map/ vs application (service topology)

| README-v2 | example-app | Match / note |
|-----------|-------------|--------------|
| specs/services-map/services.md | **Missing** | No services.md in example |
| specs/services-map/service-dependency-graph.drawio | system-design/application/services-dependency-graph.drawio | **Name**: example uses `services-dependency-graph` (plural "services"); README uses `service-dependency-graph` (singular) |
| specs/services-map/services-integration-use-case-A.data-flow.drawio | system-design/application/systems.data-flow.drawio | **Different file**: example has `systems.data-flow.drawio`; README expects `services-integration-use-case-A.data-flow.drawio`. No per–use-case data flow in example. |
| — | system-design/application/technology-selection.research.md | In example only (application-level tech selection) |
| — | system-design/application/technology-selection.spec.md | In example only |

README-v2 uses a **services-map/** area; the example uses **system-design/application/** for service/dependency diagrams and has no dedicated services-map folder.

---

## 5. security/

| README-v2 | example-app | Match / note |
|-----------|-------------|--------------|
| specs/security/security-controls.spec.md | system-design/security/security-controls.spec.md | Path: system-design/security |
| specs/security/authentication/authentication.spec.md | system-design/security/authentication/authentication.spec.md | Path differs |
| specs/security/authentication/technology-selection.spec.md | system-design/security/authentication/technology-selection.spec.md | Path differs |
| specs/security/authorization/authorization.spec.md | system-design/security/authorization/authorization.spec.md | Path differs |
| specs/security/authorization/technology-selection.spec.md | system-design/security/authorization/technology-selection.spec.md | Path differs |
| — | system-design/security/security-controls.research.md | In example only |
| — | system-design/security/encryption/ (dir) | In example only (empty or not enumerated in README) |
| — | system-design/security/network/ (see §3) | In example, network is under security; README has network at root |

---

## 6. observability/

| README-v2 | example-app | Match / note |
|-----------|-------------|--------------|
| specs/observability/technology-selection.spec.md | system-design/observability/technology-selection.spec.md | Path: system-design/observability |
| specs/observability/logging.spec.md | system-design/observability/logging.spec.md | Path differs |
| specs/observability/alerts.spec.md | system-design/observability/alerts.spec.md | Path differs |
| specs/observability/metrics/ | system-design/observability/metrics/ (metric-A.spec.md) | Path differs; example has concrete metric |
| — | system-design/observability/dashboards/ (dashboard-A, technology-selection) | In example only; README tree omits dashboards |
| — | system-design/observability/technology-selection.research.md | In example only |

---

## 7. epics / feature stories

| README-v2 | example-app | Match / note |
|-----------|-------------|--------------|
| specs/epics/<epic-name>/<story-name>/ | product-design/epics/<epic>/<story>/ | Path: product-design/epics, not specs/epics |
| research.md, spec.md, plan.md, tasks.md | Same set (e.g. task-list has all four) | Convention matches |
| — | task-management/task-list, task-management/download-data (no plan/spec/tasks in list), user-management/… | Example has multiple epics/stories; some story dirs may not yet have all four files |

---

## 8. application-stack / implementation (backend & frontend)

| README-v2 | example-app | Match / note |
|-----------|-------------|--------------|
| specs/application-stack/ (or backend/, frontend/) | **implementation/** | README uses "application-stack"; example uses "implementation" |
| constitution.md at stack root | constitution.md in implementation/backend/cron-driven-processes and in service-A, data-store-A | Example has no single implementation-level constitution; constitutions are per-area/component |
| frontend/: technology-selection, testing-strategy, deployment-strategy, observability | implementation/frontend/: same plus style.spec.md, ui-application-events.spec.md, pages/, components/ | Largely aligned; example has more (pages, components, style, ui-application-events) |
| backend/<component>/: overview.md, configuration.md, deployment-strategy.spec.md, observability.spec.md, security.md, testing-strategy.spec.md | implementation/backend/: service-A has service-configuration.md (not overview.md); deployment-strategy, observability, testing-strategy, technology-selection, constitution, application-events, openapi, drawio | **overview.md**: README requires it; example uses **service-configuration.md** and no overview.md. **security.md**: README lists it; not present in example backend components. **configuration.md**: README; example has service-configuration.md |
| Optional: caching.md, technology-research.md, technology-selection.spec.md | technology-selection.research.md, technology-selection.spec.md present | Naming: example uses .research.md and .spec.md |

---

## 9. Items only in README-v2 (not in example)

- `specs/` as top-level container
- `as-built.md` at root
- `specs/network/` at root (example has network under system-design/security/)
- `specs/services-map/` and `services.md`; `service-dependency-graph.drawio` (naming); `services-integration-use-case-A.data-flow.drawio`
- `application-stack/` (example uses `implementation/`)
- Backend component: `overview.md`, `configuration.md`, `security.md` (example has service-configuration.md, no overview or security.md)
- Observability: no dashboards in README tree

---

## 10. Items only in example (not in README-v2 tree)

- **Root**: `constitution.md`, `spec-rules.md`, `README.md` at repo root
- **Top-level**: `product-design/`, `system-design/`, `implementation/`
- **system-design**: `spec-rules.md`; `deployment/` (deployment-strategy.spec.md); `testing/` (testing-strategy.spec.md)
- **system-design/application**: application-events.spec.md, application-entities.spec.md, technology-selection.*
- **security**: security-controls.research.md, encryption/, network/ (under security)
- **observability**: dashboards/ (dashboard-A, technology-selection), technology-selection.research.md
- **implementation**: per-component constitution; service-configuration.md; application-events, openapi, drawio under service-A
- **product-design/epics**: concrete epic/story names (task-management, user-management, task-list, etc.)

---

## 11. Naming differences

| Concept | README-v2 | example-app |
|---------|-----------|-------------|
| Service dependency diagram | service-dependency-graph.drawio | services-dependency-graph.drawio |
| Use-case data flow | services-integration-use-case-A.data-flow.drawio | systems.data-flow.drawio (single system-wide?) |
| Backend component overview | overview.md | (missing; service-configuration.md used) |
| Backend component config | configuration.md | service-configuration.md |
| Stack root folder | application-stack/ (or backend/, frontend/) | implementation/ |

---

## 12. Suggested alignment directions

1. **Root**: Decide whether to adopt a single `specs/` root (README-v2) or keep `product-design/`, `system-design/`, `implementation/` (example). If keeping the three-fold split, update README-v2’s example tree to show that layout.
2. **network**: Decide if network stays under security (example) or is a top-level sibling of security (README-v2). Update the other side accordingly.
3. **services-map vs application**: Either rename system-design/application to services-map and add services.md + per–use-case data flow files, or change README-v2 to describe system-design/application with services-dependency-graph and systems.data-flow.drawio.
4. **as-built**: Add as-built.md to the example (and template) if it should be required.
5. **Backend component docs**: Add overview.md and security.md to backend components in the example, or relax README-v2 to allow service-configuration.md and no overview/security when not applicable.
6. **Constitution**: Either add an implementation-level constitution.md in the example or document in README-v2 that constitution can be per-area/component only.
7. **Observability dashboards**: Add dashboards/ to the README-v2 example tree to match the example.
8. **File names**: Align service-dependency-graph vs services-dependency-graph and the data-flow diagram naming (systems vs services-integration-use-case-A).

Use this diff to refine either the example-app structure or README-v2 (or both) until they match the intended spec template spec.
