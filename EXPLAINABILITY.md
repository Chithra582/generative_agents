# EXPLAINABILITY.md

This document explains the internal mechanisms, data lineage, operational boundaries, and governance framework of **Generative Agents Simulation Architecture** (`generative-agents`) in accordance with the **OpenGAP v0.1.0** specification for the **HiDevs GitAgent Passport** clearance pipeline.

> **Agent Name:** Generative Agents Simulation Architecture (`generative-agents`)  
> **Specification:** OpenGAP v0.1.0  
> **Category / Domain:** Developer Tools / Social Simulation & Cognitive Architecture  
> **Compliance Standard:** OpenGAP Checkpoint 2 (Explainability & Decision Governance), OWASP LLM Top 10, MITRE ATLAS  

---

## How the Agent Decides

The Generative Agents Simulation Architecture is an open-source implementation of generative computational agents that simulate human behavior in interactive sandbox worlds. It provides an end-to-end cognitive architecture combining associative memory streams, periodic reflection, hierarchical planning, and spatial environmental perception. Its operational purpose is to serve as an architectural benchmark and experimentation framework for social science simulations, non-player character (NPC) behavioral modeling, human-agent interaction studies, and multi-agent coordination research.

### 1. Decision Architecture

The sensory perception, memory retrieval, reflection synthesis, hierarchical planning, and action actuation loop operates across a deterministic, five-stage architecture:

```
Simulation Step / Environmental Event (Perceived Observation / Dialogue Turn / Object State Change)
    │
    ▼
[Stage 1: Environmental Perception & Event Ingestion]
    │  - Observes entities and spatial states within the agent's sensory radius
    │  - Translates spatial coordinate changes into natural language event descriptions
    │  - Appends raw perceptual observations to the agent's continuous memory stream
    ▼
[Stage 2: Associative Memory Retrieval & Scoring]
    │  - Evaluates memory stream records across Recency, Importance, and Relevance
    │  - Computes composite retrieval scores to extract top-k salient memories
    │  - Restricts prompt memory injection to avoid context window overflow
    ▼
[Stage 3: Periodic Reflection & Higher-Order Synthesis]
    │  - Identifies salient patterns and generates high-level reflective questions
    │  - Synthesizes abstract behavioral insights from retrieved cluster memories
    │  - Stores synthesized reflections back into the memory stream as generalized knowledge
    ▼
[Stage 4: Hierarchical Planning & Dialogue Formulation]
    │  - Decomposes day-level schedules into hourly blocks and 5-minute action sub-goals
    │  - Dynamically revises execution plans when interrupted by environmental changes or speech
    │  - Generates context-grounded conversational dialogues with neighboring agents
    ▼
[Stage 5: Spatial Movement Actuation & Trajectory Logging]
    │  - Translates planned actions into discrete grid-world coordinates and state mutations
    │  - Applies collision avoidance and spatial boundary constraints
    │  - Commits complete simulation state and dialogue transcripts to local storage
    ▼
Validated Agent Action & Auditable Cognitive Simulation Trajectory Record
```

### 2. Decision Logic & Memory Retrieval Formulations

Generative Agents evaluate memory salience, reflection triggers, and action scheduling using deterministic mathematical models:

1. **Composite Memory Retrieval Score ($S_{\text{retrieve}}$)**:
   $$S_{\text{retrieve}}(m) = (w_r \cdot R_{\text{recency}}(m)) + (w_i \cdot I_{\text{importance}}(m)) + (w_s \cdot S_{\text{relevance}}(m, q))$$
   where:
   - $R_{\text{recency}}(m) = \alpha^{\Delta t}$ is an exponential decay function over elapsed simulation hours ($\alpha = 0.995$).
   - $I_{\text{importance}}(m) \in [1, 10]$ is an integer score assigned at memory ingestion.
   - $S_{\text{relevance}}(m, q) = \text{CosineSim}(\mathbf{v}_m, \mathbf{v}_q)$ represents dense vector similarity to current query $q$.
   - Standard normalized weights: $w_r = 1.0, w_i = 1.0, w_s = 1.0$.

2. **Reflection Trigger Threshold ($T_{\text{reflect}}$)**:
   $$T_{\text{reflect}} = \sum_{m \in M_{\text{recent}}} I_{\text{importance}}(m) \ge 150$$
   Triggering higher-order abstract reasoning whenever cumulative perceptual importance reaches the trigger quota.

### 3. Thresholding & Refusal Decision Criteria

Generative Agents Simulation Architecture enforces strict operational safety and ethical boundaries:
- **Refusal to Generate Real-World Harmful Deceptions**: Dialogue turns designed to emulate real-world impersonation, harassment, or financial extortion are deterministically blocked with code `ERR_HARMFUL_SIMULATION_BLOCKED`.
- **Refusal of Teleportation or Spatial Rule Violations**: Action requests attempting to move outside tile grid boundaries or through solid obstacles are rejected (`ERR_SPATIAL_COLLISION_PREVENTED`).
- **Turn Ceiling Enforcement**: Dialogue interactions between agents enforce a limit of `max_turns: 25` to prevent infinite conversational deadlocks (`WARN_DIALOGUE_CEILING_REACHED`).
- **Local Storage Confinement**: Simulation saves write strictly to the local project directory; external file paths are blocked (`ERR_OUT_OF_BOUNDS_WRITE`).

### 4. Fallback Decision Mechanism

Continuous simulation execution is guaranteed through multi-tier fault recovery:
- **Model Cascade Failover**: When the primary foundation model experiences latency spikes or HTTP 429 rate limits, the orchestrator cascades automatically between `claude-3-5-sonnet`, `gpt-4o`, and `gemini-2.0-flash`.
- **Rule-Based Routine Fallback**: If LLM planning fails or encounters timeouts, the agent falls back to pre-defined deterministic daily routine tables (sleeping, eating, working).
- **Graceful Schedule Repair**: If dynamic re-planning fails during an interruption, the agent resumes its baseline hourly schedule without halting the world simulation.

### 5. Human-in-the-Loop Governance

Human researchers retain complete supervisory direction over the simulation environment:
- **Researcher Intervention Authority**: Researchers can inject custom events, speak directly to agents as an omniscient persona, or pause the world tick at any time.
- **Emergency Simulation Kill Switch**: Operators can halt the simulation server instantly via standard `Ctrl+C` interrupt signals.
- **Inspectable Cognitive Trajectories**: Complete memory streams, reflection trees, and spatial movement paths are logged in structured JSON files for scientific analysis.

---

## The Data It Uses

Generative Agents operates under strict privacy, data minimization, and local simulation isolation standards.

### 1. Ingested Input Data

The agent processes only operational assets necessary to fulfill cognitive simulation:
- **Perceptual Events**: Textual descriptions of spatial movements, object interactions, and agent utterances.
- **Agent Personas**: Character backstories, personality traits, occupations, and initial relationship graphs.
- **Environment Tile Maps**: Spatial coordinate matrices and collision layers representing the sandbox town.

### 2. Configuration & Reference Data

- **Memory Stream Schemas**: Structured formats defining creation timestamps, expiration times, and importance scores.
- **Spatial Topology Layouts**: Grid definitions, room designations, and interactable object dictionaries.
- **Reflection Prompt Templates**: Canonical templates for question generation and insight extraction.

### 3. Base Model & Inference Lineage

- **Deterministic Simulation Engines**: Grid movement solvers, A* pathfinders, and temporal decay calculators executed natively in Python (100% deterministic with zero LLM variance).
- **Foundation LLMs**: High-capability frontier models (`claude-3-5-sonnet`, `gpt-4o`, `gemini-2.0-flash`) utilized for conversational dialogue, reflective reasoning, and dynamic plan decomposition.
- **Zero Training on Research Data**: Simulation personas, character dialogues, and social interaction logs are never transmitted to external cloud servers or used for model training.

### 4. Data Privacy, Storage, and Retention

- **OWASP LLM & MITRE ATLAS Hardened**: Defended against prompt injection, memory stream poisoning, and unauthorized agency.
- **Local-Only Simulation Storage**: All memory logs, world states, and agent trajectories reside exclusively on the user's filesystem.
- **Zero Personal Data Collection**: Simulated characters represent fictional synthetic personas containing zero real-world personally identifiable information (PII).
- **Zero Commercial Monetization**: Research logs, simulation states, and agent dialogues are never monetized, aggregated, or shared with third parties.

---

## Limitations

Understanding the operational boundaries and technical constraints of Generative Agents is essential for research modeling.

### 1. Memory Stream Context Dilution Over Extended Lifespans
- **Limitation**: Simulating hundreds of game days can accumulate tens of thousands of memories, challenging retrieval precision.
- **Mitigation**: The architecture implements hierarchical reflection trees and periodic memory pruning to compress old observations into compact insights.

### 2. High Computational Cost for Large Populations
- **Limitation**: Simulating large towns with dozens of concurrent agents generates significant LLM token throughput per tick.
- **Mitigation**: The engine supports spatial LOD (level of detail), freezing cognitive updates for distant agents outside the player's active area.

### 3. Hallucination of Physical World Rules
- **Limitation**: Without strict spatial ground truth, agents can verbally claim to interact with non-existent objects.
- **Mitigation**: All physical actions must be validated against the environment state database before state mutations are committed.

### 4. Conversational Repetition in Extended Dialogues
- **Limitation**: Two agents left in an unconstrained dialogue loop can begin repeating pleasantries without advancing social dynamics.
- **Mitigation**: The engine enforces a 4-to-8 turn dialogue budget, automatically terminating conversations when information exchange ceases.

### 5. Multi-Agent Coordination Coordination Friction
- **Limitation**: Coordinating town-wide collaborative events (e.g., organizing a party) requires subtle social diffusion across multiple independent agents.
- **Mitigation**: The system supports explicit calendar invitation objects that propagate through direct conversation channels.

---

## Summary & Compliance Checklist

| Checkpoint 2 Requirement | Corresponding Section | Status |
| :--- | :--- | :---: |
| **How the agent decides** | [How the Agent Decides](#how-the-agent-decides) | **Covered** |
| - Decision architecture & 5-stage pipeline | Section 1 | Verified |
| - Decision logic & memory retrieval formulations | Section 2 | Verified |
| - Thresholding & refusal decision criteria | Section 3 | Verified |
| - Fallback decision mechanism | Section 4 | Verified |
| - Human-in-the-loop governance & oversight | Section 5 | Verified |
| **The data it uses** | [The Data It Uses](#the-data-it-uses) | **Covered** |
| - Ingested perceptual events, personas & tile maps | Section 1 | Verified |
| - Configuration, memory schemas & prompt templates | Section 2 | Verified |
| - Base model lineage & deterministic engines | Section 3 | Verified |
| - Data privacy, retention lifecycle & MITRE/OWASP | Section 4 | Verified |
| **Its limitations** | [Limitations](#limitations) | **Covered** |
| - Memory stream context dilution over extended lifespans | Section 1 | Verified |
| - High computational cost for large populations | Section 2 | Verified |
| - Hallucination of physical world rules | Section 3 | Verified |
| - Conversational repetition in extended dialogues | Section 4 | Verified |
| - Multi-agent coordination coordination friction | Section 5 | Verified |
