# 🎸 Auxend's Guitar Bench Lab

Welcome to the **Guitar Bench Lab**—your digital luthier assistant! 

If you're tired of guessing why your Jaguar bridge is buzzing, why your Strat's F-barre chords feel stiff, or you finally got that one "Golden" guitar playing *perfectly* and you desperately want to capture its exact setup DNA so you can replicate it on your other guitars... you're in the right place.

This app is designed for guitar enthusiasts, tone chasers, and offset lovers to document, compare, and dial in their setups using pure physics instead of superstition.

---

## 🛠️ How It Works (The Bench Workflow)

The app works by letting you record the exact measurements of your guitars and automatically compares them against your "Benchmark" (the best-playing guitar you own) to tell you exactly what you need to adjust.

```mermaid
flowchart TD
    subgraph 1. Measure & Record
        A[Add Guitar Profile] -->|Measure with Feeler Gauges| B(Input Relief, Nut Height, Action)
    end
    
    subgraph 2. Compare
        B --> C{Delta Comparison Engine}
        C -->|Compare against...| D[(Your Golden 'Benchmark' Guitar)]
    end
    
    subgraph 3. Adjust (T-R-A-I-N)
        C -->|App detects high nut| E[Lower Nut Slots]
        C -->|App detects offset rattle| F[Add Neck Shim & Raise Bridge]
        C -->|App detects stiff middle| G[Flatten Truss Rod]
    end
    
    E & F & G --> H[🎸 Perfectly Dialed In]
```

---

## 🚀 Getting Started

You don't need any fancy servers or backend installations to run this. It's built entirely on standalone web technologies.

1. **Clone or Download this repository.**
2. **Open `index.html`** directly in your web browser (Chrome, Edge, or Safari).
3. **Link your Data:** The app uses the modern File System API. You can point it directly to the included `fleet.json` file on your hard drive, and any changes you make in the browser will automatically save back to the file!

---

## 🎸 Features Built for Tone Chasers

### 1. The Fleet Manager
Keep a digital logbook of every guitar you own. Record the scale length, string gauge, neck relief, 12th fret action, and nut slot heights. Never forget what gauge strings you put on that Telecaster 6 months ago.

### 2. The Delta Comparison Engine
Have one guitar that plays like butter, and another that fights you? Set your favorite guitar as the **Benchmark**, and the app will generate a "Delta" (difference) report. It will tell you exactly how many thousandths of an inch you need to lower your nut or flatten your truss rod to make the bad guitar feel exactly like the good one.

### 3. The Offset Break-Angle Calculator
Fender Jazzmasters and Jaguars have unique physics. If the angle of the strings behind the bridge is too shallow, the bridge will violently rattle and strings will pop out. The app automatically flags offset guitars with dangerous break angles and prescribes the exact neck shim (e.g., 0.5° StewMac) you need to fix it.

### 4. Built-In Visual Luthier Guides
Not sure how to measure your relief or file a nut? The app includes beautifully formatted, interactive visual guides embedded right in the tabs:
- **Baseline Capture Guide:** How to measure the "Holy Grail" guitar you just bought before you change the strings.
- **Fender Offset Setup Guide:** The definitive manual for making Jazzmasters and Jaguars play flawlessly without buzzing.

---

## 📂 Project Files Explained

- **`index.html`** - The main app. Open this to start!
- **`fleet.json`** - Your guitar database. Back this file up! It holds all your measurements.
- **`openspec.md`** - The raw math and geometry rules the app uses to calculate setups.
- **`.agents/`** - For the AI nerds: This folder contains the skills and rules that allow AI assistants to act as your personal Master Luthier based on the OpenSpec data.

---

*Grab your feeler gauges, fire up the bench, and let's get those guitars playing like butter!*
