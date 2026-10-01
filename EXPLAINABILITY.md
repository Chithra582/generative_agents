# EXPLAINABILITY — Generative Agents Simulation Architecture

> **Admissibility & Transparency Report for OpenGAP / Agent Passport**  
> *Agent Name:* Generative Agents Simulation Architecture (`generative-agents`)  
> *Specification:* OpenGAP v0.1.0  
> *Domain:* Developer Tools / Social Simulation & Cognitive Architecture  

---

## 1. Overview & Operational Purpose
The **Generative Agents Simulation Architecture** is an open-source implementation of generative computational agents that simulate human behavior in interactive sandbox worlds. It provides an end-to-end cognitive architecture combining associative memory streams, periodic reflection, hierarchical planning, and spatial environmental perception.

Its operational purpose is to serve as an architectural benchmark and experimentation framework for social science simulations, non-player character (NPC) behavioral modeling, human-agent interaction studies, and multi-agent coordination research.

---

## 2. How the Agent Decides (Decision-Making Logic)
Generative Agents Simulation Architecture operates across a deterministic, multi-stage decision pipeline:

```
[Stage 1: Perceptual Intake] ──> [Stage 2: Memory Retrieval] ──> [Stage 3: Reflection & Belief]
                                                                                │
                                                                                ▼
[Stage 6: World State Commit] <── [Stage 5: Action Execution] <── [Stage 4: Plan Decomposition]
```

### 2.1 Perceptual Intake & Importance Rating
- **Decision:** Scan the immediate 2D grid vicinity for spatial objects, ambient statuses, and other characters; compute an importance score for new observations.
- **Rules:** Filter redundant static observations; rate importance on a scale of 1-10; insert novel events into the chronological memory stream.

### 2.2 Memory Retrieval & Context Formulation
- **Decision:** Query associative memory for relevant past experiences, emotional bonds, and procedural knowledge applicable to the current situation.
- **Rules:** Score memories using a balanced combination of recency decay, importance weight, and cosine relevance; retrieve the top-$k$ memory nodes.

### 2.3 Reflection & Belief Updating
- **Decision:** When cumulative importance points exceed the reflection threshold, synthesize higher-level abstract questions and insights.
- **Rules:** Generate 2-3 generalized insights linking multiple memory nodes; re-insert insights as first-class memory nodes that influence future planning.

### 2.4 Plan Decomposition & Action Execution
- **Decision:** Decompose active schedule milestones into immediate minute-by-minute actions, destination coordinates, and dialogue turns.
- **Rules:** Verify object availability and path navigability; if another agent is present and speaks, pause execution and generate responsive dialogue.

---

## 3. Data & Privacy
| Data Category | Retention Policy | Third-Party Sharing | Storage Mechanism |
|---|---|---|---|
| Experiential Memory Nodes | Simulation Lifetime | None | Local JSON / SQLite Store |
| Agent Persona Profiles | Permanent Config | None | Local Python / JSON Manifests |
| Dialogue & Interaction Transcripts | Simulation Run (Replay Archive) | None | Local Output Replay Directory |
| Spatial Environment Grid Data | Static / Simulation Duration | None | Local Tilemaps & Matrix Arrays |

Generative Agents Simulation Architecture complies with operational security and privacy standards:
- **No Cloud Data Exfiltration:** All agent reflections, memory streams, and town movement matrices are stored and executed locally without telemetry leaks.
- **Epistemic Isolation:** Each agent's memory stream is strictly private; an agent has zero access to another agent's internal thoughts, plans, or reflections unless communicated via dialogue.
- **Sanitized Model Payloads:** Prompts dispatched to model inference contain only synthetic persona backstories and simulation observations, devoid of user credentials or host machine secrets.
- **Data Minimization:** Memory retrieval algorithms dynamically filter and extract only the minimal top-$k$ memory items required for a specific decision step.

---

## 4. Known Limitations & Failure Modes
Reviewers, auditors, and users should note the following operational constraints:
1. Hallucinated Relationship History
   - *Limitation:* Over extensive simulation runs, agents may occasionally hallucinate shared past events that never actually occurred in the simulation.
   - *Mitigation:* The architecture enforces memory grounding, requiring dialogue generation prompts to explicitly cite past memory node IDs.
2. Temporal Drift and Schedule Desynchronization
   - *Limitation:* If LLM latency spikes, agent time loops can drift relative to other agents in the simulation clock.
   - *Mitigation:* The simulation operates on a discrete turn-based simulation clock (`simulation-step-clock`) where all agents must complete step $T$ before $T+1$ advances.
3. Pathfinding Deadlocks in Narrow Corridors
   - *Limitation:* Multiple agents attempting to cross single-tile doorways simultaneously can result in oscillation or deadlock.
   - *Mitigation:* The pathfinding system incorporates collision-avoidance yield rules and temporary detour routing.
4. Repetitive Conversational Loops
   - *Limitation:* Long conversations between two agents without new external stimuli can degrade into polite but repetitive conversational loops.
   - *Mitigation:* The architecture implements dialogue termination heuristics, ending conversations after 4-8 turns or when conversational topics exhaust.

---

## 5. Verification, Safety & Human Oversight
Generative Agents Simulation Architecture integrates multi-layer safety rails to ensure full human accountability and system integrity:
- **Real-Time Human Approval Gate:** Authoring new agent personas, modifying world parameters, or injecting synthetic events requires explicit human operator action.
- **Emergency Session Interrupt:** Simulations can be paused, frozen, or terminated cleanly at any discrete step tick without data loss.
- **Step Quota Guardrails:** Strict step boundaries limit maximum autonomous simulation ticks per run, preventing unbounded API consumption.
- **Structured Audit Logging:** Every agent thought, perception, reflection, and spoken utterance is serialized to immutable replay files for post-hoc analysis.
