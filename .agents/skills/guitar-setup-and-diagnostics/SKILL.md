---
name: guitar-setup-and-diagnostics
description: >-
  Use this skill when diagnosing, setting up, or troubleshooting electric guitars—especially Fender offsets (Jazzmaster, Jaguar), Strats, and Teles. Covers neck relief, nut slot depths, bridge break angles, neck pocket shimming, and buzz elimination.
---

# Guitar Setup & Offset Geometry Skill

This skill documents the exact mechanical rules, tolerances, and diagnostics for high-performance electric guitar setups, specifically addressing the unique physics of Fender offset vibrato bridges and vintage Stratocaster tremolos.

---

## 1. The Core Geometry Principles

### The "Zero-Fret" Nut Rule
- The nut **only** dictates action on open strings and the first 3 frets.
- Once any fret is depressed (frets 1–21/22), the nut is physically bypassed and has **zero influence** on string height across the rest of the fingerboard.
- **Factory Nut Flaw:** Factory nuts are cut high (`.020"–.024"`) to prevent open string buzz in retail stores. This makes first-position F-barre chords stiff and pulls open chords sharp.
- **Master Bench Spec:** Cut nut slots down to `0.012"–0.014"` (bass) and `0.008"–0.010"` (treble) above the 1st fret crown.
- **Diagnostic:** Clamp a capo on fret 1. If playability suddenly feels effortless, the nut is cut too high.

### The Offset Break Angle Paradox (Jazzmaster vs. Jaguar)
- **Jazzmaster (25.5" Scale):** Higher string tension naturally seats strings into the saddles. With a flat neck pocket, the bridge can be slammed low to the body without losing adequate downward pressure.
- **Jaguar (24.0" Short Scale):** Tension is significantly lower. Strings have a wide vibration arc.
  - **Slamming the Jaguar bridge flattens the break angle**, removing downward string pressure.
  - Result: Saddles rattle, height grub screws back out, and strings pop out of grooves.
  - **The Fix:** Install a **0.5°–1.0° neck pocket shim** (StewMac full-contact). This tilts the neck back and forces the bridge to be **raised**, increasing the break angle over the saddles to 12°–15° while maintaining ultra-low action at the 12th fret.
  - **Strings:** Never use 9s on a vintage Jaguar. Run `10.5` or `11s`.
  - **Hardware:** Apply Blue Loctite 242 to bridge saddle height screws to prevent vibration drift.

---

## 2. The T-R-A-I-N Protocol (Order of Operations)

Always execute adjustments in this strict sequence:

1. **Tune to Pitch:** Tension dictates geometry. Never set up a guitar slack.
2. **T: Truss Rod (Relief):**
   - Capo 1st fret, fret at the body joint (17th fret).
   - Measure gap at 8th fret crown.
   - Standard: `0.010" (0.25mm)`.
   - Ultra-Low / "Slammed": `0.004"–0.006" (0.10–0.15mm)` (near-flat neck).
3. **R: Radius & Bridge Height (Action):**
   - Lower bridge until slight buzz occurs on frets 7–12, then raise 1/4 turn.
   - Use understring radius gauges to match bridge saddles to fretboard radius (7.25", 9.5", 12").
4. **A: Action at Nut (Slot Depth):**
   - Fret between 2nd & 3rd fret. Check clearance over 1st fret.
   - Target: `0.003"–0.005"` (whisper of light).
   - File slots using gauged files angled back toward tuners.
5. **I: Intonation:**
   - Adjust saddle position forward/back until the 12th fret harmonic matches the fretted 12th note.

---

## 3. Reference Tolerances

| Parameter | Fender Factory | Master Low Action | Measurement Point |
|---|---|---|---|
| **Relief** | 0.010" (0.25mm) | `0.004"–0.006"` | Fret 8 (capo 1, hold 17) |
| **Low E Nut** | 0.022" (0.55mm) | `0.012"–0.014"` | 1st fret open string gap |
| **High E Nut** | 0.018" (0.45mm) | `0.008"–0.010"` | 1st fret open string gap |
| **12th Fret Bass** | 4/64" (1.6mm) | `3/64" (1.19mm)` | Top of 12th fret to string bottom |
| **12th Fret Treble** | 3.5/64" (1.4mm) | `2.5/64" (0.99mm)` | Top of 12th fret to string bottom |
| **Break Angle** | 6°–8° | `12°–15°` | Bridge saddle to tailpiece |
