# Lab 1 — Requirements Table

**Project:** Student Project Portfolio & Showcase App (Problem Statement #4)
**Actors:** Student Team, Panel Judge, Public Voter

## Functional Requirements

| ID | Priority | Description | Acceptance Criteria | Rationale |
|----|----------|--------------|----------------------|-----------|
| FR-001 | High | The system shall enable student teams to create showcase profiles containing abstract summaries, demo video links, and verified GitHub repository URLs. | **Pass:** Profile is published to the showcase catalog upon validation of the repository link. **Fail:** Invalid URL format is accepted. | Establishes the core content pipeline that populates the entire showcase catalog — every other feature (judging, voting, leaderboard) depends on a project profile existing first. |
| FR-002 | High | The system shall allow panel judges to score each submitted project against a weighted digital rubric (Innovation, Technical Execution, Presentation) and automatically compute an aggregate score. | **Pass:** The aggregate score recalculates immediately when any rubric criterion is updated. **Fail:** The score requires manual recalculation. | Automated, structured scoring keeps judging consistent and comparable across a large number of projects and multiple judges. |
| FR-003 | Medium | The system shall allow one verified public vote per project per user account, blocking duplicate votes and flagging suspicious multi-account (sybil) voting patterns. | **Pass:** A second vote attempt from the same verified identity is rejected. **Fail:** A duplicate vote is counted. | Directly addresses the "strict anti-sybil protections" requirement that is central to the problem statement. |
| FR-004 | Medium | The system shall display a public leaderboard that ranks projects by combined judge score and public vote count, updating in real time. | **Pass:** Leaderboard position updates within the NFR-001 latency target after a new vote or score is recorded. **Fail:** A stale ranking persists after new input. | Gives the expo audience visible, live feedback, which drives engagement during the event. |
| FR-005 | Low | The system shall allow student teams to edit or withdraw their showcase submission any time before the judging deadline, logging every change with a timestamp. | **Pass:** Edit history shows timestamped changes. **Fail:** Edits made after the deadline are accepted silently. | Supports late-breaking fixes (broken links, updated demos) without compromising judging fairness once scoring has started. |

## Non-Functional Requirements

| ID | Type | Description | Priority | Acceptance Criteria | Rationale |
|----|------|--------------|----------|----------------------|-----------|
| NFR-001 | Performance & Security | The public voting and leaderboard calculations shall update in real-time with an API response latency under 300 ms. | High | **Pass:** Benchmarking tests confirm target latency and security standards under simulated peak load. | A slow or insecure vote pipeline undermines trust in the leaderboard exactly when the audience is watching it live. |
| NFR-002 | Reliability & Scalability | The voting and leaderboard services shall maintain 99.5% uptime and support at least 5,000 concurrent users during the 48-hour expo voting window, without breaching the NFR-001 latency target. | High | **Pass:** A load test at 5,000 concurrent users sustains sub-300 ms p95 latency with zero downtime. **Fail:** The service degrades or drops below 99.5% uptime. | Expo voting is a short, high-traffic burst window — the system must not fail exactly when engagement peaks. |
