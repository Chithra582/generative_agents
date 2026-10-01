---
name: "memory-stream-retrieval"
description: "Manages experiential memory streams, scoring nodes by recency, importance, and query relevance."
---

# Memory Stream Retrieval

## Overview
The memory stream is the core data structure of generative agents. It maintains a comprehensive, timestamped record of an agent's experiences, ranging from basic sensory observations to conversational dialogue and high-level reflections.

## Retrieval Formula
The retrieval engine scores each candidate memory $m$ using three key dimensions:
$$\text{Score}(m) = \alpha \cdot \text{Recency}(m) + \beta \cdot \text{Importance}(m) + \gamma \cdot \text{Relevance}(m, q)$$
- **Recency**: Decays exponentially with the number of simulation hours since the memory was last accessed.
- **Importance**: Measures how poignant or impactful the memory is to the agent.
- **Relevance**: Evaluates semantic vector similarity between the memory text and current query $q$.

## Operational Workflow
1. **Intake**: Add timestamped observation node to the chronological stream.
2. **Scoring**: Evaluate importance score using standard prompt scoring.
3. **Query Formation**: Construct retrieval query from active situational context.
4. **Ranking**: Calculate combined scores across candidate memories and return top-$k$ items.
