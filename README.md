# Gut Lining Interaction Simulator

**Advanced educational prototype for exploring how chemical identity, concentration, exposure time, gut region, mucus reserve, buffering, flow, tight junctions, and uncertainty can change a rough gut-lining irritation-risk estimate.**

> **Educational only. Not medical advice. Not a toxicology decision tool.**  
> This project is a mechanistic teaching toy. It must not be used to decide whether an ingestion, exposure, chemical, dose, or product is safe. If a real exposure has happened, contact poison control, NHS 111, or emergency services for serious symptoms.

---

## Why this exists

The simulator started as a single-file gut-lining interaction demo that accepted a chemical formula or common name, estimated a rough irritation score, showed a barrier-thickness curve, and let users compare scenarios. This upgraded version keeps that fast offline workflow but adds a more research-inspired explanation layer:

- chemical identity parsing and molecular-weight estimation
- concentration conversion across common units
- region-specific gut assumptions
- mucus, epithelium, tight-junction, and immune-alarm proxies
- uncertainty/sensitivity modelling
- adverse-outcome-pathway style explanation
- optional online PubChem lookup
- local export, comparison, presets, and scenario sharing

The goal is to make chemical-risk reasoning more transparent, visual, and experimental while clearly showing the limits of the model.

---

## Features

### Preserved core features

- **Single-file HTML app** — no build tools or server required.
- **Chemical input** by formula or common name, such as `HCl`, `NaOH`, `C2H6O`, `Ca(OH)2`, ethanol, aspirin, salt, and hydrogen peroxide.
- **Formula parser** with support for elements, parentheses, and simple hydrates.
- **Concentration inputs** for `mM`, `M`, and approximate percent units.
- **Exposure-time control** in minutes.
- **Gut-region selector** for comparing different mucosal environments.
- **Risk KPIs** for score, band, pH direction, and confidence.
- **Model breakdown** showing major drivers such as pH/caustic shift, osmotic load, oxidative/reactive stress, and membrane/solvent stress.
- **Barrier chart** showing a toy damage-versus-recovery curve.
- **Compare table** for side-by-side scenario testing.
- **JSON export** for saving individual results.

### New advanced features

- **Advanced context controls**
  - mucus layer reserve
  - food/buffering context
  - peristalsis/flow
  - pre-existing irritation
  - microbiome stress proxy

- **Multi-layer gut barrier model**
  - mucus reserve
  - epithelial/barrier thickness
  - tight-junction integrity
  - immune/inflammatory alarm proxy

- **Extra KPIs**
  - TEER-style barrier integrity proxy
  - final mucus reserve
  - tight-junction stress
  - inflammatory alarm proxy

- **Uncertainty modelling**
  - Monte Carlo-style runs
  - uncertainty interval
  - uncertainty histogram
  - confidence/data-quality messaging

- **Research Lab tab**
  - scenario presets
  - reference-panel runner
  - safe in-silico experiment idea generator
  - organ-on-chip inspired interpretation mode

- **Data + export tools**
  - export latest result as JSON
  - export compare table as CSV
  - copy share-state JSON
  - save/load locally with `localStorage`

- **Optional PubChem lookup**
  - can fetch formula, molecular weight, IUPAC name, and CID data
  - off by default
  - only assists chemical identity, not clinical risk

- **Accessibility and UX improvements**
  - responsive grid layout
  - light/dark theme toggle
  - clearer warnings
  - tabbed workflow
  - readable model-card assumptions

---

## Research-informed design

This project borrows ideas from several modern modelling directions while remaining a simplified educational simulation.

| Idea | How it appears in the app |
| --- | --- |
| **Adverse Outcome Pathways (AOPs)** | Results are explained as a chain from stressor → molecular initiating event → cellular response → barrier change → uncertainty/warning. |
| **Gut-on-chip models** | The advanced context controls include flow/peristalsis-like effects, mucus reserve, epithelial barrier proxies, and microbiome stress. |
| **Barrier integrity metrics** | TEER-style output is included as a toy proxy for epithelial barrier integrity. |
| **Open chemical identity data** | Optional PubChem lookup can fill in formula and molecular-weight information when online access is available. |
| **Uncertainty-aware modelling** | The simulator avoids single-score overconfidence by adding confidence, interval, histogram, and model-card explanations. |

### Useful references

- OECD: Adverse Outcome Pathways — https://www.oecd.org/en/topics/sub-issues/testing-of-chemicals/adverse-outcome-pathways.html
- OECD: Series on Adverse Outcome Pathways — https://www.oecd.org/en/publications/oecd-series-on-adverse-outcome-pathways_2415170x.html
- NIH PubChem PUG-REST documentation — https://pubchem.ncbi.nlm.nih.gov/docs/pug-rest
- Nature Biomedical Engineering: gut-on-chip with microbiome and peristaltic-like movements — https://www.nature.com/articles/s41551-024-01318-z
- Microfluidic gut barrier platform review — https://www.sciencedirect.com/science/article/pii/S2590006424001388

---

## Quick start

### Option 1: Open directly

1. Download or clone the repository.
2. Open `index.html` in a modern browser.
3. Enter a chemical formula or supported common name.
4. Choose concentration, unit, exposure time, and gut region.
5. Click **Simulate**.

### Option 2: Run with a local static server

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

A static server is useful when testing browser permissions, optional online lookup, or future module loading.

---

## Example scenarios

Try these to explore how the model behaves:

| Scenario | Input | What to watch |
| --- | --- | --- |
| Strong acid | `HCl`, 50 mM, stomach | pH/caustic component and mucus reserve |
| Strong base | `NaOH`, 20 mM, oesophagus | high caustic risk and low buffering |
| Weak organic acid | citric acid, 25 mM, duodenum | weaker pH stress but context-sensitive output |
| Solvent stress | ethanol, 10% v/v, stomach | membrane/solvent component |
| Oxidizer demo | `H2O2`, 3% w/v, mouth | oxidative/reactive driver |
| Osmotic load | `NaCl`, 500 mM, colon | osmotic contribution and region differences |

---

## How the model works

The app uses a deliberately transparent rule-based pipeline:

```text
chemical input
  ↓
formula/name normalisation
  ↓
formula parser + molecular weight estimate
  ↓
rough molarity conversion
  ↓
chemical class / reactive flag estimate
  ↓
component scoring
  ↓
region + context modifiers
  ↓
layer dynamics simulation
  ↓
uncertainty sampling
  ↓
visual result + model-card explanation
```

### Main score drivers

- **Caustic / pH shift** — strong acids and bases increase this component.
- **Osmotic load** — salts and high-solute scenarios can increase irritation potential.
- **Oxidative / reactive stress** — oxidizers and dehydrating chemicals add stress.
- **Membrane / solvent stress** — solvents and organic compounds can affect membrane integrity in the toy model.
- **Exposure time** — longer contact increases simulated injury potential.
- **Region modifiers** — stomach, oesophagus, mouth, small intestine, and colon have different baseline assumptions.
- **Context modifiers** — mucus, buffering, flow, inflammation, and microbiome stress alter the final simulation.

---

## Important limitations

This simulator does **not** know or model:

- actual swallowed dose or volume
- real product formulation
- dilution after ingestion
- vomiting, aspiration, airway risk, burns, or perforation
- patient age, pregnancy, medications, disease, allergies, or medical history
- clinical examination findings
- regulatory exposure limits
- validated toxicology thresholds
- product-specific additives
- mixtures, surfactants, or complex reactions
- metabolism, absorption, distribution, or excretion
- real tissue healing dynamics

A low score does **not** prove safety. A high score does **not** diagnose injury. The output is only a learning aid.

---

## Safety message

For real-world exposures:

- Do **not** rely on this app.
- Follow the product label and local poison guidance.
- In the UK, contact **NHS 111** for urgent advice when appropriate.
- Call emergency services for severe pain, breathing difficulty, drooling, repeated vomiting, blood, collapse, confusion, burns, or suspected caustic ingestion.

---

## Project structure

Suggested repository layout:

```text
.
├── index.html        # single-file simulator
├── README.md         # project documentation
├── LICENSE           # project license
└── screenshots/      # optional UI screenshots or demos
```

The current app can stay as one HTML file. If the project grows, consider splitting into:

```text
src/
├── parser.js         # formula parsing and molecular-weight utilities
├── model.js          # scoring and layer simulation
├── uncertainty.js    # Monte Carlo/sensitivity logic
├── charts.js         # canvas chart renderers
├── data.js           # reference chemicals and presets
└── ui.js             # DOM events and rendering
```

---

## Development notes

### No build step

The simulator is designed to run directly in the browser. Keep dependencies minimal unless a feature clearly benefits from a package.

### Browser APIs used

- Canvas API for charts
- `Blob` and object URLs for export
- `localStorage` for local save/load
- optional `fetch` for PubChem lookup

### Recommended QA checks

Before committing changes:

- Test formula parsing: `HCl`, `H2SO4`, `Ca(OH)2`, `CuSO4·5H2O`.
- Test common names: ethanol, aspirin, salt, citric acid, baking soda.
- Test units: `mM`, `M`, `% w/v`, `% v/v`, `mg/mL`.
- Test every region and model mode.
- Test reset, compare, clear compare, JSON export, CSV export, local save/load, and theme toggle.
- Test offline behaviour with PubChem unavailable.
- Confirm warnings remain visible and unambiguous.

---

## Roadmap

### Near-term improvements

- Add unit tests for formula parsing and concentration conversion.
- Add a screenshot or GIF demo to the README.
- Add more chemicals with clear educational-only metadata.
- Add import support for exported JSON states.
- Add better error messages for invalid formulas.
- Add keyboard shortcuts for simulation and reset.

### Research/innovation ideas

- Confidence-weighted scoring based on identity certainty and unit-conversion certainty.
- Separate acid neutralisation and buffer-capacity toy module.
- Chemical mixture sandbox with strong warning labels.
- Sensitivity tornado chart showing which input changed the output most.
- Calibration mode using safe synthetic benchmark cases.
- AOP graph view with editable event nodes.
- Versioned model cards for reproducible educational experiments.
- Web Worker option for large Monte Carlo runs.
- Exportable lab notebook report in Markdown or PDF.

---

## Contributing

Contributions are welcome if they preserve the project’s educational framing and safety boundaries.

Good contribution areas:

- accessibility improvements
- clearer warnings and model-card text
- parser correctness
- chart readability
- test cases
- documentation
- safe preset scenarios
- better uncertainty visualisation

Please avoid contributions that make the simulator look clinically validated, diagnostic, or suitable for real exposure decisions.

---

## License

MIT License is recommended for this style of educational single-file prototype, unless your repository already uses a different license.

---

## Disclaimer

This repository is for education, visualisation, and experimentation only. It is not medical advice, toxicology advice, poison-control advice, a laboratory protocol, or a safety certification tool. Always use qualified medical, toxicology, regulatory, or emergency services for real-world exposure questions.
