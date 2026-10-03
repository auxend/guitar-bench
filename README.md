# Volt Guitar Bench Lab

An interactive workbench app and luthier knowledge base for documenting, preserving, comparing, and reverse-engineering electric guitar setups—specializing in Fender Offsets (Jazzmaster, Jaguar) and Stratocasters.

---

## 🚀 Quick Start

Open **`index.html`** in any web browser (Chrome, Safari, Firefox). 
- **100% Offline-First:** Zero dependencies, no npm install, no node server required.
- **Auto-Persisting:** Saves all your guitar profiles directly to browser `localStorage`.
- **JSON Backup:** One-click Export and Import to preserve your collection's DNA.

---

## 🗂️ Project Structure

```
guitar-bench/
├── index.html                           # The unified Guitar Bench Lab Web App
├── guitar-bench-app.html                # App alias
├── fender-offset-setup-guide.html       # Visual guide: Offset Break Angles & T-R-A-I-N Protocol
├── guitar-baseline-capture-guide.html   # Visual guide: 7 Measurements for Holy Grail Guitars
├── openspec.md                          # OpenSpec Architecture, vector formulas & data schema
├── agent.md                             # AGY Luthier Agent operating instructions
└── .agents/
    ├── rules/
    │   └── guitar-tech-protocol.md      # Auto-trigger rule enforcing physical axioms & T-R-A-I-N
    └── skills/
        ├── guitar-setup-and-diagnostics/# Bench procedures, tolerances, and blank setup sheets
        └── html-guide-boilerplate/      # Reusable guide design system & templates
```

---

## 🎸 Key Capabilities

1. **Fleet Manager:** Record scale length, relief, 1st fret nut clearances, 12th/17th fret action, neck pocket shims, and hardware quirks.
2. **Compare & Clone Engine:** Pick a "Benchmark Guitar" (e.g. your slammed Jazzmaster) and a "Target Guitar" (e.g. your buzzing Jaguar). The app superimposes their neck planes on an interactive SVG and generates a custom luthier prescription.
3. **Break Angle & Force Vector Calculator:** Calculates string break angle ($\alpha$) and downward seating force ($F_{\text{down}}$) in lbs over the saddles, with automatic buzz hazard warnings for offsets.
4. **Embedded Knowledge Base:** Both the *Offset Setup Guide* and *Baseline Capture Guide* are embedded right inside the app tabs.
