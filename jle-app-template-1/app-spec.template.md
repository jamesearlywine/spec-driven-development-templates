# App Spec Template


## Design
These sections are exclusively design sections

### Application
specs/
(root - high-level)
- spec-overview.md
- product-vision.spec.md // why?
- product-requirements.md // what to build?
- user-personas.spec.md // who?
- application-events.spec.md // what actions happen? .. sequence diagrams, flow charts
- application-entities.spec.md // to what entities? .. entity relationship diagrams

### Security
- /security
  - security-controls.research.md
  - security-controls.spec.md
  - /authentication
    - technology-selection.research.md
    - technology-selection.spec.md
    - authentication.spec.md
  - /authorization
    - technology-selection.research.md
    - technology-selection.spec.md
    - authorization.model.drawio
    - authorization.spec.md
  - /networking
    - network-topology.drawio

### Observability
/observability
  - technology-selection.research.md
  - technology-selection.spec.md
  - logging.spec.md // logging technologies
  - alerts.spec.md // alerting technologies
  - /metrics
    metric-A.spec.md // includes alert thresholds
  - /dashboards // composed of metrics
    - technology-selection.research.md
		- technology-selection.spec.md
    - /dashboard-A
      - dashboard-A.spec.md
      - dashboard-A.wireframe.drawio

## Features
This section is where we plan to build the various parts of our application.
- epics/
	- some-epic/
		- some-story/
			- research.md
			- spec.md
			- plan.md
			- tasks.md
		- some-other-story/
			- research.md
			- spec.md
			- plan.md
			- tasks.md

## Technology
This section is a mix of planning and execution.  This planning is non-functional and localized in its technical scope.

Each technology sub-section should have these specs in the root folder:
- constitution.md
- technology-selections.research.md
- technology-selections.spec.md
- testing-strategy.spec.md
- deployment-strategy.spec.md

	- /frontend
	  - technology-selection.research.md
		- technology-selection.spec.md
		- testing-strategy.spec.md
		- deployment-strategy.spec.md
		- observability/.spec.md

    - style.spec.md
    - pages/
      - page-1.requirements.spec.md
      - page-1.research.md
      - page-1.wireframe.drawio
      - page-1.figma.md
    - components/
      - component-1.requirements.spec.md
      - component-1.research.md
      - component-1.wireframe.drawio
      - component-1.figma.md
		- application-events.spec.md

	- /backend
		- /service-A
			- constitution.md
			- technology-selections.research.md
			- technology-selections.spec.md
			- observability.spec.md
			- testing-strategy.spec.md
			- deployment-strategy.spec.md

			- application-events.sequence-diagram.drawio
			- application-events.spec.md
			- service-A.openapi.yaml
      - coding-style.spec.md
			- system-events.dfd.drawio
			- service-configuration.md

		- /data-store-A
			- constitution.md
			- technology-selections.research.md
			- technology-selections.spec.md
			- testing-strategy.spec.md
      - deployment-strategy.spec.md
			- observability.spec.md

			- entity-relationship-diagram.drawio

		- /cron-driven-processes
			- constitution.md
			- technology-selections.research.md
			- technology-selections.spec.md
			- testing-strategy.spec.md
			- deployment-strategy.spec.md
      - observability.spec.md

      - /process-A
        - research.md
        - spec
        - plan.md
        - tasks.md

