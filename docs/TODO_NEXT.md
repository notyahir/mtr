# Next Task

## Task
Review ChatGPT's field survey results and identify 2–3 candidate research directions to explore further.

## Context
We are in the exploratory phase — no research direction has been selected. ChatGPT was sent a broad survey prompt covering active areas in music AI / MIR, open problems, underserved areas, and gaps in non-Western music representation. Results are pending.

## Spec
When ChatGPT's survey comes back:
1. Bring the full results to Claude
2. Claude will synthesize and identify the most promising directions given Yahir's background and interests
3. Claude will produce a shortlist of 2–3 directions with honest assessment of each
4. Each direction gets: research angle, novelty, feasibility for an MS thesis, cultural relevance, and required skills/data
5. From the shortlist, run Workflow 4 (Brainstorming) to generate concrete project ideas within each direction
6. Take the concrete ideas to ChatGPT for novelty validation

## Done When
- A research direction is chosen and written into `docs/DECISIONS.md`
- A first concrete research question is written into `docs/WORKING_CONTEXT.md`
- `docs/TODO_NEXT.md` is updated with the first real task in that direction
