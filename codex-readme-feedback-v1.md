# README.md Editorial Feedback (Spec-Driven Development, git-spec, bmad)

Below is a fresh, structured set of editorial notes and recommendations for improving the root README to better reflect spec-driven development methodologies, including git-spec and bmad.

## Executive Summary
- The README reads more like a brainstorming list than a practical guide. Convert it into a clear, action-oriented document.
- Make the workflow explicit. Artifacts without process lead to drift.
- Define scope boundaries and relationships between epics, features, domains, and components.
- Add a short purpose statement so readers understand why these templates exist and how to use them.

## High-Impact Recommendations
1. **Add a clear purpose statement.**  
   Explain what this repo is for, who uses it, and what “spec-driven development” means in this context (human + AI collaboration).

2. **Describe the spec lifecycle.**  
   Add a short “Lifecycle” section:
   - Discovery → Spec → Plan → Tasks → Build → Verify → As-Built → Drift Review  
   Tie each step to its file(s).

3. **Define scopes and boundaries.**  
   Clearly distinguish:
   - System / Domain / Component / Feature / Task  
   Include how artifacts link across scopes.

4. **Create a glossary.**  
   Terms like “epic,” “feature story,” “system component,” and “domain” are used interchangeably. A short glossary will prevent ambiguity and align with git-spec/bmad intent.

5. **Replace questions with guidance.**  
   Several sections read as prompts rather than instructions. Rephrase as declarative rules or conventions.

## Section-by-Section Notes
### 1. Specification Conventions
- Fix spelling: “heirarchy” → “hierarchy.”
- Replace vague bullets with concrete rules:
  - Where specs live
  - When to read them
  - How to link them
  - When to update them

### 2. Product Management
- Split into two headings:
  - Requirements artifacts (epics, stories, research, design decisions)
  - Delivery artifacts (plan.md, tasks.md, test cases)
- Explicitly require acceptance criteria at epic and feature scope (bmad emphasis).

### 3. System Design Documents
- Replace questions with a short list:
  - What exists (global system docs, domain docs, component docs)
  - Where they live
  - Update triggers (new feature, major refactor, drift)

### 4. Application Domains
- Clarify how generalized domains relate to application domains.
- Add an example of dependency links between domains.

### 5. System Components
- Separate “component instance files” from “component type templates.”
- Clarify which docs are mandatory vs optional.
- Encourage linking component overview to architecture diagrams and parent domain specs.

### 6. As-Built
- Make “As-Built” a required artifact for verification and drift detection.
- Specify update cadence (e.g., after each deploy or milestone).

## Alignment With git-spec
- Strongly emphasize linked specs and traceability.
- Add guidance on:
  - Required references between files
  - How changes propagate upstream/downstream
  - Source of truth rules

## Alignment With bmad
- Require intent + acceptance criteria at each scope.
- Include explicit definition of done at epic and feature scope.
- Encourage verification artifacts (tests, demos, QA notes).

## Suggested Additions
- **Quick Start**: 3–5 steps to apply the templates on a new effort.
- **Example Folder Structure**: a short tree showing where each artifact lives.
- **Checklist**: a minimal “spec complete” checklist for each scope.

