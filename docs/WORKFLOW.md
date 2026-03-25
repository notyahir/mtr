# Workflow System
## How Claude + ChatGPT Collaborate

**Last updated:** March 24, 2026

---

## The Philosophy

Two AI tools, distinct non-overlapping jobs, one shared GitHub repo as ground truth.

**The cardinal rule: Do not ask both tools to do the same job.**

---

## Division of Labor

| Responsibility | Claude | ChatGPT |
|---|---|---|
| Planning & decomposing tasks | ✅ Primary | ❌ |
| Research design & methodology | ✅ Primary | ❌ |
| Web research & finding papers | ❌ | ✅ Primary |
| Literature synthesis & summaries | ❌ | ✅ Primary |
| Current events / recent developments | ❌ | ✅ Primary |
| Document drafting (thesis, reports) | ✅ Primary | ❌ |
| Critiquing and red-teaming | ✅ Primary | Secondary |
| Code planning & architecture | ✅ Primary | ❌ |
| Code implementation & debugging | ❌ | ✅ Primary |
| Interpreting experiment results | ✅ Primary | Secondary |
| Brainstorming & ideation | ✅ Primary | Secondary |
| Writing handoff prompts | ✅ Primary | ❌ |

**Claude knows the project deeply.** All research context, design decisions, phase history, and theoretical frameworks live in the Claude Project. Claude is the research brain.

**ChatGPT executes and researches live.** It browses the web, finds papers, writes and debugs code. ChatGPT is the hands and eyes.

---

## Workflow 1: Researching

**Use when:** Finding papers, surveying a field, understanding what exists, finding datasets.

**Who leads:** ChatGPT (web research) → Claude (synthesize into project context)

### Step 1 — Frame with Claude
Tell Claude what you want to research and why. Claude will frame the question precisely and write a tight research brief for ChatGPT.

### Step 2 — Research with ChatGPT
```
RESEARCH BRIEF:
[paste Claude's brief]

Your job:
1. Search for papers, tools, datasets, or implementations relevant to this
2. For each: title, authors, year, one-sentence summary, why it's relevant
3. Flag anything that directly overlaps or contradicts the approach
4. Identify gaps — what has NOT been done
5. End with a 1-paragraph synthesis

Prioritize: 2020–2025, peer-reviewed venues (ISMIR, ICASSP, NeurIPS, ICML, ICLR),
publicly available code/datasets.
```

### Step 3 — Synthesize with Claude
Bring ChatGPT's findings back. Claude situates them in the project context, identifies what actually matters, updates `research/papers.md`.

### Step 4 — Update repo
Say "summary" → Claude writes session summary → paste into `docs/SESSION_LOG.md` → push.

---

## Workflow 2: Programming and Implementing

**Use when:** Writing code, building a pipeline, debugging, running experiments.

**Who leads:** Claude (plan) → ChatGPT (implement) → Claude (critique) → ChatGPT (finalize)

### Step 1 — Plan with Claude
Describe the task. Claude breaks it into steps, identifies approaches, flags risks, writes a precise implementation spec.

### Step 2 — Implement with ChatGPT
```
IMPLEMENTATION SPEC:
[paste Claude's spec]

WORKING CONTEXT:
[paste relevant section of docs/WORKING_CONTEXT.md]

Your job:
1. Implement the spec — do not redesign unless you hit a genuine blocker
2. Flag any significant design choice not in the spec
3. Write clean, commented code
4. Note assumptions made
5. End with: what you built, what you tested, what's left, open questions

Environment: Python 3.10, PyTorch 2.0, conda env 'trimet'
```

### Step 3 — Critique with Claude
Paste ChatGPT's implementation. Claude checks against the spec, flags issues, writes a critique brief.

### Step 4 — Finalize with ChatGPT
Apply only the good feedback. Produce final version.

### Step 5 — Update repo
Claude writes summary → `docs/SESSION_LOG.md`. ChatGPT pushes code.

---

## Workflow 3: Writing Papers and Thesis

**Use when:** Writing any research document — thesis sections, paper drafts, abstracts, related work.

**Who leads:** Claude throughout. ChatGPT assists with sourcing only.

### Step 1 — Structure with Claude
Tell Claude what needs to be written and its purpose. Claude proposes structure and identifies what needs sourcing vs. what can be drafted now.

### Step 2 — Source with ChatGPT (if needed)
```
SOURCING REQUEST:
I am writing [section] of a paper on [topic].
I need: [specific things — stats, citations, prior work]
For each: give me the source, the specific claim, and a paraphrase I can use.
Do not fabricate citations. Flag uncertainty.
```

### Step 3 — Draft with Claude
Claude integrates sourced material, drafts the section, maintains argument flow and voice.

### Step 4 — Iterate
Claude red-teams the draft — argument logic, clarity, whether it says what it needs to say.

### Step 5 — Update repo
Final draft into the relevant file. Session summary into `docs/SESSION_LOG.md`.

---

## Workflow 4: Brainstorming New Ideas

**Use when:** Exploring new project directions, generating options, thinking laterally.

**Who leads:** Claude (generate, grounded in context) → ChatGPT (validate against what exists)

### Step 1 — Generate with Claude
Describe the space. Claude generates 5–8 concrete ideas, each with: core concept, research angle, feasibility, dataset requirements, scope/risk assessment.

### Step 2 — Validate with ChatGPT
```
IDEA VALIDATION:
Here are [N] ideas I'm considering:
[paste ideas]

For each:
1. Search for existing work that does the same or similar thing
2. Has this been done, partially done, or genuinely not done?
3. Most relevant existing paper or tool
4. Novelty assessment (1–5 scale)
```

### Step 3 — Decide with Claude
Claude situates results against the research context, recommends which idea to pursue, writes rationale, updates `docs/DECISIONS.md`.

---

## Workflow 5: Evaluation and Interpreting Results

**Use when:** You have experiment results and need to understand what they mean.

**Who leads:** Claude throughout.

### Step 1 — Dump results to Claude
Paste raw results + experiment setup. Claude identifies what the numbers say, flags surprises, connects results to theoretical framework, recommends next step.

### Step 2 — Research context with ChatGPT (if needed)
```
RESULTS CONTEXT:
I ran [experiment] and got [result].
Unexpected because [reason].

Search for:
1. Papers reporting similar results and how they explain it
2. Known failure modes for [method] that could explain this
3. Evaluation best practices in [field] for this experiment type
```

### Step 3 — Synthesize with Claude
Claude integrates context with result analysis, produces clean interpretation, updates `research/experiments.md`, writes next step into `docs/TODO_NEXT.md`.

---

## The Update Ritual

At the end of any meaningful session:
1. Say **"summary"** to Claude
2. Claude writes a full session summary formatted for the log
3. You paste it into `docs/SESSION_LOG.md`
4. Push to GitHub

That's it. Keep it consistent and the repo stays alive.

---

## Handoff File Templates

### WORKING_CONTEXT.md
```markdown
# Working Context
Last updated: YYYY-MM-DD

## Current Phase
[Phase name and active task]

## What Was Just Completed
[Brief description]

## What Is Next
[Specific next task]

## Open Questions
- [question 1]

## Active Constraints
[Timeline, compute, data availability, etc.]
```

### TODO_NEXT.md
```markdown
# Next Task

## Task
[One sentence]

## Context
[Why this task, what it depends on]

## Spec
[Detailed enough for ChatGPT to implement without guessing]

## Done When
[Clear completion criteria]
```

### SESSION_LOG.md entry
```markdown
## YYYY-MM-DD — [Session Title]

**What we worked on:**
[Paragraph summary]

**Key decisions made:**
- [decision]

**Key findings:**
- [finding]

**What changed:**
- [file/doc/plan that changed]

**Next step:**
[What happens next]
```
