# TriMET — Project Overview
## Tri-Modal Music Editing Transformer

**Status:** Archived
**Period:** Late 2025 – March 2026
**Advisor:** Paris Smaragdis (AERA Lab, MIT) | **Co-Advisor:** Anna Huang (Google DeepMind)

---

## The Original Vision

TriMET was a multi-modal transformer system for symbolic music editing. The core idea: given three inputs — a text instruction, a MIDI file, and an optional audio reference — generate an edited version of the MIDI that satisfies the instruction while using the audio as a style or groove guide.

**Three input modalities:**
- **Text** — natural language description of the desired edit ("change the cadence from V-I to V-vi")
- **MIDI** — the existing symbolic music content
- **Audio** — optional reference recording for style, groove, or timbre

**Output:** Edited MIDI satisfying the specified constraints

**Eight edit types planned:**
1. Cadence Rewrite (V-I → V-vi, etc.)
2. Reharmonization
3. Groove Matching
4. Form Expansion
5. Rhythmic Variation
6. Texture Control
7. Style Transfer
8. Melodic Variation

**Novel contribution claimed:** First system combining text + symbolic + audio inputs for editable symbolic output, with audio treated as time-varying constraints rather than global style descriptors.

---

## What Was Actually Built (Pre-Scoping)

Before advisor scoping narrowed the project:

- **Multi-track REMI tokenizer** — 632-token vocabulary, 100% encode/decode accuracy on test files
- **MIDI quality filter** — applied to Lakh MIDI (116K files → ~50K high quality) and POP909
- **Five music editors** — cadence rewrite, rhythmic variation, reharmonization, form expansion, texture control
- **Training pair generation pipeline** — 35 pairs generated before scope change
- **PyTorch Dataset class** — complete and tested

**Dataset used:** POP909 (909 pop songs), Lakh MIDI (116K files)

---

## The Four-Axis Framework

The most durable intellectual contribution of the TriMET work. All musical information organized along four axes:

| Axis | What It Captures | MIDI Representation |
|------|-----------------|---------------------|
| **When** | Onset timing, tempo, rhythm | Note-on timestamps, BPM |
| **What** | Instrumentation, which notes | Pitch, Channel, Program |
| **How** | Timbre, dynamics, articulation | Velocity (partial); mostly audio |
| **Where** | Spatial position, reverb | CC#10, CC#91, CC#93 |

"Who" (performer identity) is emergent — a signature across the four axes — not a fifth axis.

This framework is transferable to any new research direction involving both MIDI and audio.

---

## Why It Was Scoped Down

The full 8-edit-type system was a 12–16 month project. On advisor guidance (Paris Smaragdis), the scope was narrowed to a **drum toy example** using the Groove MIDI Dataset. See `trimet-drum.md` for the scoped version.
