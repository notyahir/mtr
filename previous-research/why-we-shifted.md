# Why We Shifted
## An Honest Account of the Transition

**Written:** March 24, 2026

---

## What Was Built

Over roughly three months of work, the TriMET project produced:

- A clear and intellectually coherent research framing (audio-conditioned symbolic music editing)
- The four-axis framework for organizing musical information (When / What / How / Where)
- A complete signal processing baseline pipeline for the drum toy problem
- A dataset exploration of the Groove MIDI Dataset
- A REMI tokenizer, MIDI quality filter, and five music editors (from the pre-scoping phase)
- Two complete research phases with honest findings

None of this is wasted. The four-axis framework is a genuinely useful conceptual tool. The Phase 2 finding about the How-axis timbre gap is a real result that would appear in any system of this type.

---

## What Was Learned Technically

1. **The How-axis gap is a fundamental obstacle** in audio-conditioned symbolic music editing. Any system comparing MIDI-rendered audio to real recordings will encounter this — FluidSynth and a real instrument sound different, and that difference can swamp the signal you're trying to detect.

2. **Signal processing baselines are fragile** in sparse/slow musical contexts. Dense grooves are forgiving; sparse ones are not.

3. **The drum toy is a good problem** — well-defined, verifiable ground truth, real paired data. The problem itself is not the reason for the shift.

---

## Why the Direction Changed

The honest reason is not technical. The research was sound and had a clear next step (Phase 3 neural renderer). The shift happened because:

- The problem stopped feeling like *Yahir's* problem — it felt inherited from the project framing rather than something personally compelling
- The symbolic MIDI editing components (the plumbing that dominated early work) were not what Yahir found engaging — the signal processing and ML design thinking were
- Starting fresh allows the research direction to be chosen from scratch, grounded in what is actually interesting rather than what was already in motion

This is a legitimate reason to shift at the MS level. A thesis you are not curious about is harder to finish and harder to defend well.

---

## What Carries Forward

- **Technical skills:** audio signal processing, spectrogram analysis, onset detection, ML model design, PyTorch pipelines, dataset construction
- **Conceptual tools:** the four-axis framework, the distinction between MIDI-observable and audio-observable information, the How-axis gap concept
- **Dataset knowledge:** Groove MIDI Dataset, Lakh MIDI, POP909, GM drum map
- **Research habits:** phase-based progression, honest empirical findings, clean documentation

---

## If This Work Is Ever Resumed

Phase 3 is well-specified in `trimet-drum.md`. The two neural renderer approaches are documented. The paired data construction task (Step 3.1) is fully specced. Resuming would mean picking up exactly where Phase 2 left off, with the Phase 3 spec as the starting point.
