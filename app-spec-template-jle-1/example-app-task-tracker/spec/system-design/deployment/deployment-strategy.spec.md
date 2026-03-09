# Overview
Each application component will have its own deployment strategy.  This page includes general approach, technology selection, which parts of the system will be covered by which kinds of tests in which environments.

This spec will also include preferences for test setup and tear down, and the degree to which end-to-end tests will create/update state in the varioua environments.

# Deployment Strategy (Spec) – Root

<!-- Default deployment approach; overridable per area. -->

## Environments

- <!-- e.g. dev, staging, prod; how they differ -->

## Release process

- <!-- Branch → build → deploy; approvals, rollback -->

## Per-area overrides

- Frontend: see `frontend/deployment-strategy.spec.md`
- Backend: see each service/data-store/cron folder
