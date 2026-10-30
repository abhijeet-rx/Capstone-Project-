# MetroPT-3 Early Anomaly Forecasting Showcase

> A premium, single-page scrollytelling showcase for the research paper:  
> **"Early Forecasting of Progressive Sensor Anomalies in Air Compressor Systems Using Explainable Machine Learning"**

---

## 🔬 Research Overview & Dataset
- **Domain**: Railway Air Production Units (APUs) supplying braking, doors, and suspension.
- **Dataset**: **MetroPT-3** (*Veloso et al., Scientific Data, 2022, doi: 10.1038/s41597-022-01877-3*).
- **Telemetry Scale**: **1,516,948 samples**, **15 features**, **~10 s sampling interval**, **4 documented failure events**.
- **Evaluated Events**:
  - **Event 3** (Validation): Onset `2020-06-05 10:00`.
  - **Event 4** (Held-Out Prospective Test): Onset `2020-07-15 14:30`.
- **Chronological Split**:
  - Training window: Prior to `2020-05-30 06:00` (healthy baseline calibration only).
  - Validation window: `2020-05-30 06:00` to `2020-06-07 14:30` (Event 3 tuning).
  - Held-out prospective test: From `2020-06-07 14:30` onwards (Event 4 test).

---

## 🎨 Design System & Creative Direction
- **Palette**: Refined **Light Instrumentation Palette** (clean porcelain `#f8fafc`, pure white surface `#ffffff`, precision slate lines `#e2e8f0`, deep ink `#0f172a`, instrument phosphor teal `#0d9488` for healthy telemetry, and warm vermilion `#c2410c` strictly reserved for threshold alarms).
- **Typography**:
  - Headlines: *Space Grotesk* (structural, confident engineering grotesque).
  - Narrative: *Newsreader* (humanist, warm editorial cadence for readability under 68ch).
  - Telemetry & Metrics: *JetBrains Mono* and tabular numerals (`font-variant-numeric: tabular-nums`).
- **Motion Spec**:
  - Hero oscilloscope vector trace that draws across time, rises in variance, and breaches $Q_{99} = 0.644372$.
  - Smooth inertia scrolling via Lenis with thin progress bar.
  - Interactive persistence scrubber ($P = 1, 2, 3, 5, 10$) with real-time numeric animation.
  - Interactive benchmark model ranking toggle morphing test prevalence ratio into validation AP.
  - Paired bilateral TreeSHAP attribution bars highlighting `Caudal_impulses` (+36.87 shift).
  - Reconstructed native SVG charts for all 10 research figures from the paper with coordinate tooltips.
  - Visible, non-negotiable **"What this does not show"** limitations section.

---

## 📁 Repository Structure

```text
├── index.html                   # High-performance zero-dependency scrollytelling frontend
├── README.md                    # Project documentation & deployment guide
└── data/                        # Exact structured JSON data files
    ├── benchmark.json           # All 12 benchmark model test AP ratios, AUCs, and val APs
    ├── events.json              # Exact timestamps, lead times, FWR, and episodes for Events 3 & 4
    ├── persistence.json         # P = 1, 2, 3, 5, 10 sensitivity and sensor ablation data
    ├── shap.json                # TreeSHAP values for all 8 features and net shifts
    ├── splits.json              # Dataset metrics and chronological split boundaries
    ├── figures.json             # Data series for research figures 01–10
    └── comparators.json         # Alarm burden comparison (Health Index vs Extra Trees, XGBoost, PCA)
```

---

## 🚀 Quick Start & Deployment

### 1. Direct Local Preview
Double-click `index.html` to open it in any web browser (Chrome, Edge, Safari, Firefox). No build steps or package installation required.

### 2. Local HTTP Server
Using Python:
```bash
python -m http.server 8000
```
Then visit `http://localhost:8000` in your browser.

### 3. Deploy to Vercel or GitHub Pages
- **GitHub Pages**: Push this repository to GitHub, go to **Settings > Pages**, and choose `main` branch root.
- **Vercel / Netlify**: Connect the repository or drag-and-drop the directory into the dashboard.

---

## ⚖️ Scientific Integrity & Honesty Rules
1. **Zero Data Fabrication**: Every single number, timestamp, and metric matches the research paper and `/data/*.json`.
2. **Prominent Boundaries**: Event 4 is a single held-out failure; downtime reduction was not measured; SHAP attribution is not physical causation; and the Health Index is not Remaining Useful Life (RUL).
3. **Illustrative Tagging**: All decorative oscilloscope signals are explicitly labeled `illustrative signal trace`.
