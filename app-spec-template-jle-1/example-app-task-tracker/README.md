# Task Tracker – Example App Spec (First Draft)

This folder is a **first draft** of an application spec **Task Tracker**, generated from `app-spec.template.md`. Placeholder content remains where you will fill in details later.

## Decisions recorded

| Topic | Decision |
|-------|----------|
| App name | Task Tracker |
| Epic/story names | task-management, user-management; stories e.g. task-list, download-data, new-user-account-provisioning |
| Pages/components | page-1, component-1 as placeholders |
| Backend | 1 service (service-A), 1 data store (data-store-A), cron-driven-processes/process-A |
| Backend/frontend drawios | Optional: services-map; frontend-A (styleguide, ui-layout, ui-general-layout); frontend-level (ui-layout, ui-container) |
| Drawio | application-events, application-entities at root; network under security; per-component as needed |
| Figma | Fill in details later |
| Authentication | OIDC from Cognito |
| OpenAPI | Keep minimal for now |
| Constitution | Root + per-area (already in place) |
| Observability | One metric, one dashboard for now |

## Structure

- **Spec root** (`spec/`): constitution, user-personas, application-events, application-entities (and optional .drawio at root), as-built
- **product-design/** (`spec/product-design/`): product-vision, product-requirements, user-flows (README, application.figma, style-guide), epics with stories (research → spec → plan → tasks)
- **system-design/** (`spec/system-design/`):
  - **application**: application-events, application-entities; backend (technology-selection at backend level; service-A, data-store-A, cron-driven-processes/process-A); frontend/frontend-A (pages, components, deployment, observability, testing, technology-selection, ui-application-events; optional styleguide, ui-layout drawios)
  - **security**: security-controls, authentication, authorization, network (network.drawio, network.md)
  - **observability**: technology-selection, logging, alerts, metrics, dashboards
  - **deployment**: deployment-strategy
  - **testing**: e2e-testing-strategy (testing-strategy optional)
