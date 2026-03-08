# Task Tracker – Example App Spec (First Draft)

This folder is a **first draft** of a spec-driven app structure for **Task Tracker**, generated from `app-spec.template.md`. Placeholder content remains where you will fill in details later.

## Decisions recorded

| Topic | Decision |
|-------|----------|
| App name | Task Tracker |
| Epic/story names | Keep generic for now (some-epic, some-story) |
| Pages/components | Fill in later (page-1, component-1 as placeholders) |
| Backend | 1 service (service-A), 1 data store (data-store-A) |
| Drawio | Minimal placeholders for now |
| Figma | Fill in details later |
| Authentication | OIDC from Cognito |
| OpenAPI | Keep minimal for now |
| Constitution | Root + per-area (already in place) |
| Observability | One metric, one dashboard for now |

## Structure

- **Design**
  - **Application** (root): vision, requirements, personas, application events, application entities
  - **Security**: controls, authentication (OIDC/Cognito), authorization, networking
  - **Observability**: technology selection, logging, alerts, metrics, dashboards
- **Features**: `epics/some-epic/` with stories (research → spec → plan → tasks)
- **Application stack**: `application-stack/` — root defaults, then `frontend/` and `backend/` (service-A, data-store-A, cron-driven-processes/process-A)
