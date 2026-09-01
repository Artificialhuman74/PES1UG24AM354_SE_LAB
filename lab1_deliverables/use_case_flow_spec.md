# Use-Case Flow Specification

**Use Case:** Cast Vote
**Primary Actor:** Public Voter
**Related Use Cases:** *includes* Verify Voter Identity; *extended by* Flag Suspicious Voting Pattern
**Scope:** Student Project Portfolio & Showcase System

---

### Preconditions
1. The showcase catalog has been published and the public voting window is currently open.
2. The voter holds a verified account (e.g., verified email or student ID) recognized by the system.
3. The voter has not already cast a vote for this specific project during the current voting window.

### Postconditions (on success)
1. Exactly one vote is recorded against the selected project.
2. The project's vote count is incremented and the public leaderboard is recalculated in real time.
3. The voter's account is marked as having voted for that project, preventing a repeat vote.

---

### Main Success Scenario
1. The voter opens the showcase catalog and browses the published project profiles.
2. The voter selects a project and selects **Vote**.
3. The system verifies the voter's identity and device/account fingerprint as part of the anti-sybil check *(include: Verify Voter Identity)*.
4. The system confirms no prior vote exists from this voter for this project.
5. The system records the vote and increments the project's vote count.
6. The system recalculates the leaderboard ranking in real time, within the response-latency target defined in NFR-001.
7. The system displays an on-screen confirmation that the vote was recorded.

### Alternate Flow A1: Duplicate or Suspicious Vote Detected
*Triggered from step 3, extension point "on identity check"; corresponds to the extending use case Flag Suspicious Voting Pattern.*

- A1.1 — During the identity check, the system flags the attempt as a suspicious or duplicate pattern (for example, the same device fingerprint voting under multiple accounts, or an existing vote from this identity for the same project).
- A1.2 — The system rejects the vote attempt and does not increment the project's vote count.
- A1.3 — The system displays a message to the voter: *"This vote could not be counted — a vote already exists for this project from your account."*
- A1.4 — The system logs the flagged attempt for the event organizer's review.
- A1.5 — The use case ends without a recorded vote; the voter returns to the showcase catalog.

---

*Prepared for Lab 1: Requirements Engineering & UML Use-Case Modelling — Problem Statement #4, Student Project Portfolio & Showcase App.*
