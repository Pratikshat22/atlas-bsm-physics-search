# Looking for New Particles in ATLAS Data

I spent some time looking through ATLAS Monte Carlo datasets from CERN. The goal was simple — see if I can find signs of something beyond the Standard Model. Z′ and W′ particles. Heavy. Would show up as bumps in the mass spectrum if they exist.

## Data Source

The metadata comes from the **ATLAS Open Data portal** at CERN.

- **Source:** https://opendata.atlas.cern
- **Energy:** 13 TeV proton-proton collisions
- **Samples:** 102 datasets covering Z′ → ee/μμ, W′ → eν/μν, Higgs (ggF, VBF, WH, ZH, ttH), SUSY (gluino, stop, stau), and SM processes (ttbar, diboson, diphoton)
- **Generators:** Pythia8, MadGraph, Powheg, Sherpa

The metadata includes DSID, cross sections, filter efficiency, number of events, and process descriptions as provided by the ATLAS collaboration.

## What I Actually Did

I downloaded metadata from 102 ATLAS datasets. Each one is a simulation of proton-proton collisions at 13 TeV. Different physics processes. Z′ decaying to electrons, muons, taus. W′ to electrons, muons. Higgs production. SUSY. Standard Model backgrounds.

The metadata tells you what cross section to expect, what generator was used, how many events were simulated.

## What I Found

| | |
|---|---|
| Total datasets | 102 |
| Z′ and W′ datasets | 8 |
| Higgs datasets | 73 |
| SUSY datasets | 16 |

The Z′ cross section at 3 TeV is about 0.0018 pb. W′ is about 0.011 pb. Both follow the 1/M⁴ scaling that theorists predict. If you want to see a 3 TeV resonance, you need a lot of data.

## Higgs Numbers

ggF dominates. 28.3 pb. VBF is 3.75 pb. WH and ZH are around 0.8 pb. ttH is 0.46 pb. The decays — mostly to bb (58%). WW (21%). ττ (6%). ZZ (2.6%). γγ (0.23%). Zγ (0.15%). μμ (0.02%). That last one is tiny but that's what makes it interesting.

## SUSY and Other Things

Gluino cross section at 2 TeV is 0.001 pb. Stop at 1.2 TeV is 0.0017 pb. Stau at 200 GeV is 0.03 pb. Small numbers. Need high luminosity to see anything.

The diphoton spectrum drops fast. From 85 pb at 55 GeV to 1.2×10⁻⁶ pb at 5 TeV. That's a factor of 10⁸. Makes sense why high-mass resonances are hard to find.

## Why I Did This

Honestly, I just wanted to work with real particle physics data. The format is different from Kaggle. DSIDs. Cross sections. Generator names. JobOptions files. Pythia8 commands. I had to figure out what each column meant.

I ended up making an interactive dashboard with Plotly. Eight figures. Resonance shapes, cross section scaling, Higgs production and decay, diphoton spectrum, SUSY cross sections, and the Pythia8 JobOptions that tells you how the events were generated.

## What I Learned

The 1/M⁴ scaling is real. You can see it in the data. The Higgs decays mostly to bb. That's why Higgs searches focus on b-jets. The diphoton channel is rare but clean. That's why it's the discovery channel.

SUSY cross sections are tiny. If it exists, it's faint. Need a lot of luminosity.

The JobOptions file is basically a script that tells Pythia8 what to simulate. Mass, decay channels, PDF sets. It's the same format ATLAS uses for production.

## Interactive Dashboard

The dashboard has eight figures you can explore:

| Figure | What It Shows |
|--------|---------------|
| 1.1 | BSM resonance search — Z′ and W′ at 3 TeV |
| 1.2 | Cross section vs mass — 1/M⁴ scaling |
| 1.3 | Higgs production modes |
| 1.4 | Higgs decay branching ratios |
| 1.5 | Diphoton mass spectrum (55 GeV to 5 TeV) |
| 1.6 | SUSY and exotic particle cross sections |
| 1.7 | ttbar + X processes (rare top) |
| 1.8 | Pythia8 JobOptions for Z′→ee |

**Live Dashboard:**  
https://Pratikshat22.github.io/atlas-bsm-physics-search/ATLAS_OpenData_Analysis.html

## Files

- `ATLAS_OpenData_Analysis.html` — interactive dashboard (open in browser)
- `analysis_script.py` — Python code that made the plots
- `README.md` — this file
- `requirements.txt` — Python packages needed

## Running the Code Yourself

If you want to run the analysis:

```bash
pip install -r requirements.txt
python analysis_script.py
