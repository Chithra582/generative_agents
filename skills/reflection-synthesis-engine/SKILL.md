---
name: "reflection-synthesis-engine"
description: "Generates high-level abstract reflections and insights from clusters of episodic memory nodes."
---

# Reflection Synthesis Engine

## Overview
Reflections are higher-level, more abstract thoughts generated periodically by the agent. Because raw observations are often too granular to guide long-term behavior directly, reflections synthesize broad inferences and beliefs about oneself, others, and the environment.

## Reflection Mechanics
- **Trigger**: Fired when cumulative importance scores of recent observations exceed a predetermined threshold (typically 100).
- **Question Generation**: Identifies the 3 most salient high-level questions based on recent memories.
- **Insight Extraction**: Gathers memories relevant to each question and synthesizes generalized conclusions.

## Operational Workflow
1. **Threshold Check**: Monitor cumulative importance sum of new memory items.
2. **Topic Clustering**: Formulate candidate questions addressing emerging patterns.
3. **Evidence Retrieval**: Query memory stream for memories substantiating each question.
4. **Insight Synthesis**: Formulate concise, reflective statements with citations.
5. **Storage**: Re-insert new reflections into the memory stream as first-class cognitive nodes.
