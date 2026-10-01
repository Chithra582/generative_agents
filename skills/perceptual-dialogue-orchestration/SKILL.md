---
name: "perceptual-dialogue-orchestration"
description: "Coordinates spatial awareness, object affordance interaction, and inter-agent conversational dialogues."
---

# Perceptual Dialogue Orchestration

## Overview
This skill governs how agents perceive their environment, interact with surrounding objects, and engage in natural, emergent conversations with other agents they encounter.

## Key Capabilities
- **Spatial Awareness**: Detects agents and objects within the agent's perceptual field (vision radius).
- **Affordance Interactions**: Modifies object states (e.g., changes 'bed' state to 'occupied' or 'stove' to 'cooking').
- **Contextual Dialogue**: Initiates and conducts believable conversational exchanges informed by shared relationship histories.

## Operational Workflow
1. **Perception Scan**: Detect nearby entities at each simulation tick.
2. **Reaction Assessment**: Decide whether to continue active task or initiate social engagement.
3. **Utterance Generation**: Produce dialogue turns reflecting character persona and retrieved relationship memories.
4. **Information Diffusion**: Propagate shared news and town gossip into each participant's memory stream.
