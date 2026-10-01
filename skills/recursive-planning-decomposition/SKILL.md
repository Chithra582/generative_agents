---
name: "recursive-planning-decomposition"
description: "Creates broad daily plans and recursively decomposes schedules into fine-grained hourly actions."
---

# Recursive Planning & Decomposition

## Overview
Planning gives agents behavioral coherence across hours and days. Without planning, agents react solely to moment-by-moment stimuli, failing to prepare meals, commute to work, or host social gatherings.

## Planning Hierarchy
1. **Daily Overview**: Broad schedule outlining the major blocks of the day (e.g., wake up, work at the cafe, prepare dinner, relax).
2. **Hourly Schedule**: Decomposing daily blocks into 1-hour chunks with designated physical locations.
3. **5-15 Minute Tasks**: Sub-dividing hourly tasks into concrete actionable steps (e.g., grab coffee cup, turn on machine, pour coffee).

## Operational Workflow
1. **Agenda Generation**: Synthesize day plan based on persona description and yesterday's reflections.
2. **Decomposition**: Recursively break plan into fine-grained intervals.
3. **Path Resolution**: Resolve required tile coordinates and target objects for each step.
4. **Dynamic Revision**: If an environmental obstacle or interpersonal interaction occurs, revise downstream schedule.
