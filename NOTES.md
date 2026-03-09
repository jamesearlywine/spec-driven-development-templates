# spec-driven-development-templates
## Things the AI Agent needs to know:
This is a list of things the AI Agent needs to know, but also needs to know how to author, in collaboration with various project collaborators (product, design, architecture, security, data, engineers).

1. Specification conventions
    - Structure
      - The heirarchy of the specification files
      - The purpose of each specification file
    - Content
      - When to read/load specification files(s)
      - When to update specification file(s) of various scopes
        - How to ensure specification files are properly linked/associated to align to expected spec structure

2. Product Management
    - Epics (what and why)
      - Contains stories
        - User-oriented stories
        - Tech-oriented stories
      - Design documents, research and decisions
      - E2E Test Cases as Definition of Done

    - Feature stories (how and who)
      - research.md - optional, may referenece research in the Epic scope
      - spec.md - high-level definition-of-done
      - plan.md - to determine which system components require update
      - tasks.md - granular set of actionable steps to update, test, and deploy each component

3. System Design Documents
    - What documents exist at the global system level?
    - What domains exist?
      - Application Domain
      - Generalized Domains
    - What system design documents exist for each type of system component?
      - Component types
        - Document description and possible template for each
    - Where do they live?
    - When should they be read?
    - When should they be updated?

4. Application Domains
    - Sub-systems that contain system components
      - Generalized Domains
        - example: document-templating-service
      - Application Domains
        - example: bespoke-document-generation-service,
          - depends upon general document-templating-service

5. System Components
    - Templates
      - Each component instance should have:
        - caching.md (optional)
        - configuration.md
        - deployment-strategy.md
        - observability.md
        - security.md
        - technology-research.md
        - technology-selection.md
        - testing-strategy.md

        - overview.md
          - reference an architectural diagram that explains where it lives within the broader system
          - describes the component behavior
          - public and private state
          - state management
          - data lifecycle
          - component lifecycle
      - Each component type should have a template with defaults
        - even if it's just a scaffold of empty markdown, for the non-optional files

    - Component Types
      - Backend
        - Authentication
        - Authorization
        - Datastore
        - Filestore
        - Service
        - Cache
        - SearchIndex
        - DataPipeline
        - Orchestration
        - CronJob
        - Messaging
          - EventBus
            - EventProducer
            - EventConsumer
          - Topic
          - Queue
          - StreamingAppendOnlyLog
            - Dynamodb

      - Frontend
        - UI
        - FileStorage
        - CDN
        - Cache

      - ..whatever else..

6. As Built
    - A description of the current system state, as it is built right now
      - This should be compared against epics/features to evaluate system completeness
      - This should be compared against system design documents to evaluate system correctness
        - when there is drift, prompt developer to determine if the system or the system design documents need to be updated

7. Change Management
    - Phase 1 - Changelog (Immutable)
      - Epics
        - Stories

    - Phase 2 - Design Specifications (Mutable)
      - Product Design
      - System Design

    - Phase 3 - Build/Test/Deploy
      - Implementation

    - Notes
      - For each phase, the AI should have formal guidance on how to collaborate with the human-in-the-loop.
      - For AI-generated change, a change plan/diff should be created for human-in-the-loop to review and approve, when
        - Pairing to create epics and stories
        - Pairing to create design documents
        - Pairing to implement stories in accordance with relevant design documents