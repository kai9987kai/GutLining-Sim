# GutLining-Sim

**GutLining-Sim** is a **single-file, browser-based educational simulation** that models a few *mechanistic drivers* that can contribute to **GI mucosal irritation**, then converts them into a single illustrative **“risk” score** and a **curve** over time.

> **Education only — NOT medical advice.** :contentReference[oaicite:0]{index=0}

---

## What it simulates (high level)

The model combines several rough drivers into one composite output:

- **Acid/base causticity** (very rough; based on type/strength + concentration) :contentReference[oaicite:1]{index=1}  
- **Oxidizer / reactivity flags** (only if present in the project’s reference list) :contentReference[oaicite:2]{index=2}  
- **Osmotic load** (roughly, for salts) :contentReference[oaicite:3]{index=3}  
- **Exposure time scaling** :contentReference[oaicite:4]{index=4}  

It then “converts that into a single ‘risk’ number and an illustrative curve.” :contentReference[oaicite:5]{index=5}

---

## Repo contents

This repository is intentionally minimal:

- `index.html` — the entire interactive simulation (HTML/CSS/JS) :contentReference[oaicite:6]{index=6}  
- `README.md` :contentReference[oaicite:7]{index=7}  

GitHub shows **HTML 100%** and **2 commits**. :contentReference[oaicite:8]{index=8}

---

## Run locally

### Option A — open directly
Download/clone the repo and open:

- `index.html` :contentReference[oaicite:9]{index=9}  

### Option B — local server (recommended)
Running via `http://localhost` avoids `file://` quirks.

```bash
python -m http.server 8000
