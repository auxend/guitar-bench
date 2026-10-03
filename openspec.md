# OpenSpec: Guitar Bench & Setup Architecture

This OpenSpec defines the physical tolerances, fleet measurement schema, and diagnostic workflows for setting up and maintaining electric guitars—with specific domain architecture for Fender Offsets (Jazzmaster, Jaguar) and Stratocasters.

---

## 1. System Architecture & Setup Geometry

Guitar setup is a closed multi-variable mechanical system:
$$\text{Action} = f(\text{Neck Angle}, \text{Relief}, \text{Nut Depth}, \text{Bridge Height}, \text{Fret Plane})$$

### 1.1 The Independent Variables
1. **Neck Pitch Angle ($\theta_{\text{neck}}$):** Dictated by the neck pocket floor and neck shims. Controls overall bridge elevation relative to the body.
2. **Neck Relief ($\Delta_{\text{truss}}$):** Controlled via truss rod. Dictates the longitudinal concave bow between frets 1 and 17.
3. **Nut Slot Depth ($h_{\text{nut}}$):** Dictates boundary condition clearance for open strings and frets 1–3. Zero impact on fretted notes past fret 3.
4. **Bridge Saddle Height & Arc ($h_{\text{bridge}}, r_{\text{saddle}}$):** Dictates action across frets 7–21 and sets string radius matching.

### 1.2 The Offset Break Angle Vector
On vintage floating offset vibratos (Jazzmaster/Jaguar):
- Break angle ($\alpha$) over the bridge saddle:
$$\alpha = \arctan\left(\frac{h_{\text{bridge}} - h_{\text{tailpiece}}}{D_{\text{bridge-tailpiece}}}\right)$$
- Downward seating force ($F_{\text{down}}$):
$$F_{\text{down}} = 2 \cdot T_{\text{string}} \cdot \sin\left(\frac{\alpha}{2}\right)$$
- **Constraint:** If $\alpha < 10^\circ$, vibration causes saddle buzzing, screw loosening, and string displacement.
- **Remediation:** To increase $F_{\text{down}}$, tilt neck back using a **0.5° or 1.0° full-pocket hardwood shim**, which elevates $h_{\text{bridge}}$ while keeping action low.

---

## 2. Standard Instrument Measurement Schema

Every instrument logged on this bench must track the following parameters:

```yaml
instrument:
  id: "fender-jaguar-1965-reissue"
  model: "Fender Jaguar"
  scale_length_in: 24.0
  fretboard_radius_in: 9.5 # (or 7.25 / 12)
  string_gauge: "11-48"
  tuning: "E Standard (A=440Hz)"

geometry:
  neck_pocket_shim_deg: 0.5 # 0.0 (flat), 0.25, 0.5, 1.0
  relief_8th_fret_in: 0.005 # Feeler gauge with 1st capo'd & 17th held
  nut_clearance_1st_fret:
    low_e_in: 0.013
    high_e_in: 0.009
  action_12th_fret:
    low_e_in: 0.046 # 3/64" (1.19mm)
    high_e_in: 0.039 # 2.5/64" (0.99mm)
  action_17th_fret:
    low_e_in: 0.048
    high_e_in: 0.041
  bridge_type: "Offset Rocking Bridge w/ Mustang Saddles"
  break_angle_deg: 13.5

diagnostics:
  open_string_buzz: false
  frets_1_to_5_buzz: false
  frets_7_to_12_buzz: false
  upper_register_choke_on_bends: false
  bridge_rattle: false
  hardware_treatments:
    - "Blue Loctite 242 applied to saddle height screws"
```

---

## 3. Fleet Registry & Status

### Guitar 01: The Benchmark Jazzmaster (The "Slammed" Standard)
- **Status:** Dialed In (Custom Shop Standard)
- **Scale:** 25.5"
- **Characteristics:** Bridge slammed near body; nut slots cut to minimum zero-fret threshold (`.012"` / `.008"`); dead-flat neck (`.004"` relief); level frets with upper fall-away.
- **Role:** Golden reference for fretting hand-feel.

### Guitar 02: The Jaguar (Project "Buzz-Killer")
- **Status:** Remediation Needed (Excessive Bridge Rattle)
- **Scale:** 24.0" (Low natural string tension)
- **Target Plan:**
  1. Add 0.5° StewMac full-contact neck pocket shim.
  2. Elevate bridge assembly to increase string break angle to $\ge 12^\circ$.
  3. Step up strings from 9s to 10.5 or 11–48.
  4. Apply Blue Loctite 242 to bridge saddle threads.
  5. File nut slots to match Jazzmaster low-action profile.

### Guitar 03: The Vintage-Saddle Stratocasters
- **Status:** Nominal
- **Scale:** 25.5"
- **Target Plan:**
  1. Perform 1st-fret capo diagnostic test to verify factory nut slot excess.
  2. If saddles bottom out before achieving 3/64" action, verify neck pocket pitch / micro-tilt.
  3. File nut slots to zero-fret spec to eliminate cowboy chord fatigue.

---

## 4. Bench Tooling Checklist

When executing bench setups, have the following precision tools ready:
- Feeler gauge set (`.002"` through `.025"`)
- Precision 6" steel string action gauge (in 64ths of an inch and mm)
- Understring radius gauges (7.25", 9.5", 10", 12")
- Gauged nut slotting files (`.010"`, `.013"`, `.017"`, `.026"`, `.036"`, `.046"`)
- StewMac angled neck pocket shims (0.25°, 0.5°, 1.0°)
- Blue Loctite 242 (removable threadlocker)
- Accurate strobe tuner (Peterson Strobe or Polytune in strobe mode)

---

## 5. Guitar Setup Lab App Specification

### 5.1 Architecture
- **Format:** Single-file standalone HTML/CSS/JS application (`guitar-bench-app.html`).
- **Persistence:** Browser `localStorage` (key: `volt_guitar_bench_fleet_v1`) with full JSON Export and Import capabilities.
- **Dependency Policy:** 100% self-contained (zero CDNs, zero NPM packages).

### 5.2 Core Capabilities
1. **Fleet Manager:** Add, edit, clone, and remove guitar setup cards with rich metadata.
2. **Interactive Neck Plane Visualizer:** SVG diagram dynamically rendering string trajectory, nut boundary, relief sagitta, and bridge action based on input numbers.
3. **Delta Comparison Engine:** Compare any target guitar against a "Golden Reference" (e.g. The Slammed Jazzmaster) calculating parameter deltas ($\Delta \text{Relief}$, $\Delta \text{Nut}$, $\Delta \text{Action}$, $\Delta \text{Break Angle}$).
4. **Automated Luthier Prescription Engine:**
   - Detects back-bow risks if relief $< 0.003"$.
   - Detects F-barre fatigue if nut gap $> 0.018"$.
   - Detects offset buzz zone if scale $= 24"$ and break angle $< 10^\circ$.
   - Generates exact mechanical prescription (e.g. "Add 0.5° shim, raise bridge 1.2mm, file nut down 0.006\"").

