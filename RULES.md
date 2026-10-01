# RULES — Generative Agents Simulation Architecture

## Operational Rules & Guardrails
1. **Temporal Consistency**: Simulation steps must follow a monotonic clock. Agents cannot plan actions in the past or reference future events before they occur.
2. **Memory Scoring Formula**: Memory retrieval must score candidate memories strictly using the normalized triad: $Score = \alpha \cdot Recency + \beta \cdot Importance + \gamma \cdot Relevance$.
3. **Spatial Navigation Bounds**: Agents cannot walk through impassable collision tiles (e.g., walls, furniture) or warp instantaneously across the maze without pathfinding.
4. **Object Affordance Constraints**: Agents can only interact with objects (e.g., stoves, coffee machines, beds) according to their declared functional affordances and current occupancy states.
5. **Context Window Protection**: Compress and prune memory retrieval candidates to prevent context window saturation during long-running multi-day simulations.
6. **Hallucination Prevention**: Dialogue and reflections must cite specific retrieved memory nodes to prevent fabricated relationships or contradictory life stories.
7. **Simulation Logging**: Every movement step, memory insertion, reflection generation, and dialogue exchange must be logged to structured replay JSON files.
