# SomnoLens

**A lens on your nights: no-code tools to inspect, harmonize and preprocess sleep EEG from polysomnography (PSG).**

> **Status:** under active development. The code is currently developed within our [team repository](https://github.com/Dream-Team-ICM/Dream-Toolkit/tree/main/python/Inspect_EDF)  and will be published here.

## Why SomnoLens?

Sleep clinics record polysomnography every night. These routine recordings build large databases and make it possible to set up new research cohorts quickly, e.g. on a specific pathology. Reusing them, however, raises several challenges:

- **Heterogeneity:** within and across centers, acquisition and export parameters differ (sampling frequency, filters, units, polarity, dynamic range, channel configuration).
- **Signal Quality:** EDF export settings can silently clip or coarsen the 16-bit signal, and overnight recordings carry specific artifacts.
- **Flexibility vs. ease of use:** code-based tools adapt to each project but require programming skills, while graphical interfaces are accessible but rigid.

SomnoLens is a modular pipeline, tailored to PSG, that takes a database from export checks to sleep EEG features, **without requiring programming expertise**.

## What it does

| Step | Tools |
|---|---|
| **1. Inspection** | Audit of EDF export parameters for a whole dataset, from the headers only (no signal loading) · header anonymization (signal bytes untouched) · interactive explorer for a single recording |
| **2. Harmonization** | Channel selection, renaming and re-referencing per participant · hypnogram label remapping across scoring conventions (custom stages kept) · harmonization of scored events across exports and languages |
| **3. Preprocessing** | Signal quality overview (per channel, per file and per dataset) · filtering, resampling, re-referencing, epoching · flagging of every epoch × channel (amplitude, gradient, flat signal, 1/f fit, scored events) · decision by guided visual review or by an automatic channel-then-epoch rule · participant selection on macrostructure criteria |
| **4. Feature extraction** | Sleep macrostructure (TST, SE, latencies, WASO, stage %, AHI, PLM, ODI, T90) · automatic sleep scoring (GSSC) compared with the expert, with hypnodensity · spectral features (band power, periodic and aperiodic components) per stage and night third |

## Design principles

- **No code required:** every tool is an interactive web app (Voila); the code stays hidden.
- **Nothing is deleted:** rejected epochs, channels and participants are computed, flagged and traced in tables, then only left out of group statistics and figures.
- **Data vs reports:** machine-readable tables (TSV) feed the next tool, and HTML reports are for humans.
- **Resumable:** one file per participant, and database tables are rebuilt from disk, so participants can be added, or an interrupted run resumed, at any time.
- **Originals are never modified.**

**Formats:** EDF/EDF+. Experimental: Curry 9 (`.cdt`) and high-density montages (32–64 channels).

## Coming next

- Sleep microstructure: spindles and slow waves
- Infraslow rhythm, complexity and connectivity
- Group statistics and BIDS export

## Built on

[Python](https://www.python.org/) · [MNE-Python](https://mne.tools/) · [YASA](https://github.com/raphaelvallat/yasa) · [specparam](https://github.com/fooof-tools/fooof) · [GSSC](https://github.com/jshanna100/gssc) · [Voila](https://github.com/voila-dashboards/voila)

## Contact

Yvan Nédélec, Paris Brain Institute (ICM), Paris, France · yvan.nedelec@gmail.com

License: BDS-3.
