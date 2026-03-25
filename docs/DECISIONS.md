# Decisions Log

Locked decisions — what was chosen, alternatives considered, and why. Do not relitigate without strong new reason.

---

## 2026-03-24 — Deprecated TriMET and TriMET-drum
**Decision:** Step away from TriMET (tri-modal music editing transformer) and the drum toy example as the active research direction.
**Alternatives considered:** Continuing Phase 3 (neural renderer), pivoting the approach within the same problem.
**Rationale:** Yahir wants to pursue a genuinely different research direction rather than continuing to invest in a problem that no longer feels right. All prior work is preserved in `previous-research/` — nothing is lost, it can be revisited.

---

## 2026-03-24 — Claude = planner/drafter, ChatGPT = researcher/implementer
**Decision:** Claude handles planning, research design, drafting, and critique. ChatGPT handles web research, finding papers, code implementation, and debugging.
**Rationale:** Claude holds deep project context in its Project memory. ChatGPT has better live web access and is stronger at iterative debugging and implementation. Playing to each tool's actual strengths.

---

## 2026-03-24 — GitHub (mtr) as single source of truth
**Decision:** All project documentation, logs, decisions, and handoffs live in the mtr GitHub repo.
**Rationale:** Both Claude and ChatGPT can access it. Version controlled. Survives any individual chat session. One ground truth shared across all tools.

---

## 2026-03-24 — Build on signal processing + ML skills, open to new problem
**Decision:** Carry technical skills from TriMET work (audio analysis, signal processing, ML model design) but do not constrain the new research direction to the same problem space.
**Rationale:** Yahir enjoyed the signal processing and ML design thinking in TriMET, not the symbolic MIDI plumbing. New direction should play to those strengths while exploring a fresh problem.
