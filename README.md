# ⚔️ Warhammer 40K Tournament Analysis: Does Army Cost Impact Competitive Performance?

This repository contains a group project developed for the **Data Management** course as part of the MSc in Data Science at the **University of Milan-Bicocca (UNIMIB)**.

The project covers the **Warhammer 40,000 World Championship 2025** (Atlanta, GA) through a complete data management pipeline: tournament results for **402 players** are collected via REST API, integrated with retail miniature prices, stored in a relational **SQLite** database and analysed to find out whether money buys victory.

---

## 🎯 Project Objectives & Research Questions

The analysis is structured around four research questions, each addressing a different dimension of competitive play:

* **Economic impact:** Does army cost influence results? Is a high budget needed to reach the top tier?
* **Meta analysis:** Do popular factions perform better? Does detachment choice matter?
* **Unit analysis:** Do indispensable units exist? Do elite armies beat horde armies?
* **Faction dynamics:** Is there a "rock-paper-scissors" dynamic between factions?

---

## 🛠️ Tech Stack & Workflow

* **REST API (ListEngine):** Extraction of raw tournament data in JSON format.
* **Python scripts:** Parsing, re-parsing, merging, validation and cleaning of the army lists.
* **SQLite:** Final relational database, created and loaded through a dedicated Python script.
* **Jupyter Notebooks:** Data quality assessment (before/after integration), exploratory analysis, statistical tests and visualisations.

---

## 📈 Key Insights

* **Weak but significant link between cost and performance:** army cost vs. wins shows a positive correlation of **r = 0.131** (p = 0.0086).
* **Elite level does not require a bigger budget:** top 25 and bottom 25 players spent statistically the same amount (**p = 0.3082**).
* **Popularity is not a winning factor:** faction popularity is unrelated to win rate (**r = 0.0007**), while detachment choice is a key strategic factor within a faction.
* **No global advantage for elite or horde lists:** only **3 out of 40** faction matchups are significant hard counters.
* **Warhammer 40,000 is not pay-to-win:** money gives a marginal advantage, but success is driven mainly by player skill, strategy and preparation.

---

## 📡 Data Sources

| Dataset | Source | Availability |
|---|---|---|
| Tournament data | [ListEngine](https://listengine-v3-be.onrender.com) REST API (JSON) | Processed files included |
| Pricing data | Official price list provided by **ArsManufactorea** (XLSX, November 2025) | Private, not included |

---

## 📂 Repository Structure

**`1_Data Aquisition/`** — Extraction and parsing of the raw tournament data

- `API_acquisition.py` — Extracts raw tournament data from the ListEngine API
- `parser.py` — First parsing of the raw JSON
- `reparser.py` — Second parsing pass for failed lists
- `merger.py` — Merges parsed lists with manually compiled ones
- `validator.py` — Validation helpers used across the pipeline
- `warhammer_manual_lists.json` — 19 manually compiled army lists

**`2_Data Integration/`** — Cleaning, standardisation and database creation

- `Input/` — Cleaned and validated JSON files (`warhammer_final_cleaned.json`, `warhammer_final_valid.json`)
- `cleaner.py` — Final cleaning and standardisation
- `Warhammer_SQL.py` — Creates and loads the SQLite database
- `warhammer_tournaments.db` — Final relational database

**`3_Data Quality/`** — Quality metrics before and after integration

- `data_quality_assessment.ipynb`

**`4_Data Analysis/`** — Statistical analysis and visualisations

- `warhammer_analysis.ipynb` — EDA, statistical tests and visualisations

**Report & Slides**

- `Warhammer 40k report.pdf` — Full project report with methodology and results
- `Warhammer 40K presentation.pptx` — Presentation slides

---

## ⚠️ Limitations

* **Single tournament:** results reflect the November 2025 meta and may not generalise.
* **Estimated costs:** army costs come from a rule-based price-scaling function, not from actual player spending.
* **Small samples:** matchup and detachment analyses have limited statistical significance.

---

## 👥 Contributors

- [@mezza04](https://github.com/mezza04) — Data acquisition and parsing pipeline
- [@ilaria-cesa](https://github.com/ilaria-cesa) — Data cleaning, integration and database
- **Andrea Porro** — Statistical analysis and interpretation

---
*Developed by Andrea Porro, Ilaria Cesaratto, and Chiara Mezzanzanica.*

*Warhammer 40,000 is a trademark of Games Workshop. This is an independent academic project, not affiliated with or endorsed by Games Workshop.*
