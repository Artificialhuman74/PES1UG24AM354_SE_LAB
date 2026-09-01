# Lab 1 — Student Project Portfolio & Showcase App

Requirements Engineering & UML Use-Case Modelling deliverables for Problem Statement #4.

## Contents

| File | What it is |
|------|------------|
| `requirements_table.md` | FR-001–FR-005 and NFR-001–NFR-002 with ID, Type/Priority, Description, Acceptance Criteria, Rationale. |
| `use_case_diagram.puml` | PlantUML source for the UML use-case diagram. |
| `use_case_diagram.svg` / `.png` | Rendered diagram — actors Student Team, Panel Judge, Public Voter; includes both an `<<include>>` and an `<<extend>>` relationship. |
| `use_case_flow_spec.md` / `.pdf` | 1-page flow specification for the **Cast Vote** use case: preconditions, postconditions, main success scenario, and one alternate flow. |

## How to use this

1. Copy these files into your Lab 1 GitHub repo (a `docs/` or `lab1/` folder works well).
2. Open `requirements_table.md` — if your actual Lab 1 draft already has different FRs/NFRs, keep those; this table is a best-effort draft since no prior Lab 1 table was available.
3. Double-check the use-case diagram: it currently models 3 actors (Student Team, Panel Judge, Public Voter). The brief only names the first two — "Public Voter" was added because voting is one of the 5 functional requirements. If your instructor wants exactly 2 actors, fold the voting use cases under Student Team/Panel Judge instead, or ask before submitting.
4. Push everything and confirm the repo link is what you'll submit.

## Use-case relationships modeled

- **`<<include>>`**: Create Showcase Profile → Validate Repository URL · Score Project via Rubric → Calculate Aggregate Score · Cast Vote → Verify Voter Identity
- **`<<extend>>`**: Edit or Withdraw Submission → (extends) Create Showcase Profile · Flag Suspicious Voting Pattern → (extends) Cast Vote
