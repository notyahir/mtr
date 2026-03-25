# MTR — Music Technology Research

**Yahir | MIT Music Technology & Computation MS**
**Advisor:** Paris Smaragdis (AERA Lab) | **Co-Advisor:** Anna Huang (Google DeepMind)

---

## What This Repo Is

This is the central hub for all research, planning, and documentation across the MS. It is the single source of truth shared between Claude, ChatGPT, and any other tools in the workflow.

**Everything important lives here. If it isn't in this repo, it doesn't exist.**

---

## Repo Structure

```
mtr/
├── README.md                        ← you are here
├── docs/                            ← operational documents (read these first)
│   ├── WORKFLOW.md                  ← how Claude + ChatGPT collaborate
│   ├── WORKING_CONTEXT.md           ← current project state
│   ├── DECISIONS.md                 ← locked decisions + rationale
│   ├── TODO_NEXT.md                 ← the specific next task
│   └── SESSION_LOG.md               ← running log of meaningful sessions
├── previous-research/               ← TriMET and TriMET-drum (archived)
│   ├── README.md                    ← what this folder is and why
│   ├── trimet-overview.md           ← what TriMET was
│   ├── trimet-drum.md               ← the drum toy example specifically
│   └── why-we-shifted.md            ← honest transition document
└── research/                        ← active research (new direction TBD)
    ├── README.md                    ← how to use this folder
    ├── survey.md                    ← field survey, open problems
    ├── papers.md                    ← reading notes and citations
    └── experiments.md               ← what was run, what it showed
```

---

## For Claude

You hold the deep project context. All research history, design decisions, and phase findings live in your Project memory. Your jobs: planning, research design, document drafting, critique, writing handoff prompts for ChatGPT.

At the end of any meaningful session, write a full session summary when Yahir says "summary." Format it for `docs/SESSION_LOG.md`.

Full workflow instructions: `docs/WORKFLOW.md`

---

## For ChatGPT

Your jobs: web research, finding papers, surveying the field, code implementation, debugging.

Before starting any task:
1. Read `docs/WORKING_CONTEXT.md` — current project state
2. Read `docs/TODO_NEXT.md` — the specific task spec
3. Do not make research or architectural decisions independently — flag them

Full workflow instructions: `docs/WORKFLOW.md`

---

## Current Status

**Phase:** Exploratory — new research direction being identified
**Active task:** Field survey of music AI / MIR research landscape
**Previous work:** TriMET and TriMET-drum (see `previous-research/`)
