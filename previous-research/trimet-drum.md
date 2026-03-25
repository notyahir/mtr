# TriMET-Drum — The Drum Toy Example
## Scoped Research Direction

**Status:** Archived (Phase 2 complete, Phase 3 not started)
**Period:** Early 2026
**Dataset:** Groove MIDI Dataset (Google Magenta)

---

## The Problem

Given:
1. A drum MIDI file with **one instrument removed** (e.g., the hi-hat track)
2. The **reference audio** of the complete performance (which includes the missing instrument)

→ Detect which instrument is missing and recover the missing MIDI track.

This is a clean, verifiable instance of the general audio-conditioned MIDI editing problem. Ground truth is known (we removed the instrument), the dataset provides real paired performances, and results are auditorially evaluable.

---

## The Dataset

**Groove MIDI Dataset** (Google Magenta)
- Roland TD-11 electronic drum kit recordings
- Paired MIDI + WAV from the same performance, perfectly aligned
- 1,150 MIDI files, 13.6 hours total audio
- Multiple drummers, multiple styles (rock, jazz, funk, latin)
- Heavy imbalance: small number of drummers dominate the recording count
- CC#4 (hi-hat pedal) is the only CC data — Where axis is audio-only

**GM drum map (most common pitches):**
- Kick: 36 | Snare: 38/40 | Hi-hat closed: 42 | Hi-hat open: 46
- Crash: 49 | Ride: 51 | Tom high: 50 | Tom mid: 48 | Tom low: 45

---

## Phase History

### Phase 1: Data Exploration ✅ COMPLETE
Key findings:
- Heavy drummer imbalance across the dataset
- Short median clip durations — segmentation required
- CC#4 is the only CC data (Where axis audio-only)
- Paired MIDI/audio structure is clean and reliable

### Phase 2: Signal Processing Baseline ✅ COMPLETE
Pipeline built:
1. FluidSynth rendering (MIDI → audio via GM soundfont)
2. Instrument removal (mute one drum channel before rendering)
3. Spectrogram residual comparison
4. Onset envelope comparison
5. Per-band energy comparison
6. Cosine similarity metrics

**Core finding:**
> The pipeline works for frequency-isolated instruments in dense grooves but fails for slow tempos and sparse patterns where the How-axis timbre gap dominates. The difference between a FluidSynth GM soundfont and a real Roland TD-11 is large enough to swamp the What-axis signal in sparse/slow contexts.

### Phase 3: Neural Renderer 🔴 NOT STARTED (project archived before this phase)
**Planned:** Train a neural net to map FluidSynth audio → TD-11-style audio, closing the How-axis timbre gap so the Phase 2 comparison becomes reliable for all groove types.

**Two candidate approaches identified:**
- Approach A: U-Net spectrogram mapper (FluidSynth mel-spec → TD-11 mel-spec)
- Approach B: Learned embedding space where FluidSynth and TD-11 are close

---

## Key Technical Decisions Made

- Train/test split by drummer identity, not by clip (prevents data leakage)
- FluidSynth soundfont: FluidR3_GM.sf2 (141MB, at `~/projects/trimet/soundfonts/`)
- Conda environment: `trimet` (Python 3.10)
- ASUS ROG (RTX 4060, 8GB VRAM) as training machine

---

## What Was Learned

The How-axis gap (timbre mismatch between rendered MIDI and real recordings) is a fundamental obstacle in any system that tries to compare MIDI-rendered audio to real audio. This is not specific to drums — it will appear in any audio-conditioned symbolic music editing system. The neural renderer approach (Phase 3) is the right solution, and the design work done is directly reusable if this direction is ever resumed.
