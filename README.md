# Datasheet: Keppetipola Wholesale Vegetable Prices (2024 - 2026)

Prepared in compliance with the **Gebru et al. (Datasheets for Datasets)** framework to guarantee maximum transparency, reproducibility, and utility for time-series forecasting.

---

## 1. Motivation
- **Why was the dataset created?** Created to document wholesale vegetable price fluctuations in Sri Lanka's Keppetipola Dedicated Economic Centre, helping local farmers, policy analysts, and machine-learning researchers predict food inflation cycles.
- **Who funded/created the dataset?** Self-funded; collected by AGN Chathuranga and the infamous other Chathuranga. Compiled and cleaned by Anton Jayakody (NSBM Green University). Contact: anton.j@nsbm.ac.lk.

## 2. Composition
- **What do the instances represent?** Daily wholesale price observations per crop.
- **Schema Definition:**
  - `Date`: Observation date in standardized ISO 8601 format (`YYYY-MM-DD`).
  - `Vegetable`: Standardized local vegetable name.
  - `Price_Raw_LKR`: Original price recorded before data cleaning.
  - `Price_Clean_LKR`: Corrected and validated price (LKR/kg).
  - `Correction_Notes`: Log explaining any programmatic or manual typo repairs.
  - `Botanical_Name`: Scientific taxonomic classification.
  - `English_Name`: Standard English names for global discoverability.
  - `Unit`: Fixed measurement unit (`LKR/kg`).
  - `Market_Type`: Fixed transaction class (`Wholesale`).
  - `Data_Quality_Flag`: Set to `Observed` or `Carried_Forward` (preventing target leakage during rolling train/test splits).

- **Summary Statistics:**
  - **Total Records:** 6815 observations
  - **Unique Varieties:** 16
  - **Observed Instances:** 6112
  - **Carried Forward Instances:** 703 (10.32% of dataset)

### Price Summary Statistics Matrix
| Vegetable    | English_Name           | Botanical_Name                       |   count |   min |   max |   mean |   median |
|:-------------|:-----------------------|:-------------------------------------|--------:|------:|------:|-------:|---------:|
| Beans        | Green Beans            | Phaseolus vulgaris                   |     427 |   100 |  1000 | 367.76 |      350 |
| Beetroot     | Beetroot               | Beta vulgaris                        |     427 |    60 |   900 | 244.05 |      250 |
| Brinjal      | Eggplant / Brinjal     | Solanum melongena                    |     427 |    50 |   800 | 226.31 |      200 |
| Cabbage      | Cabbage                | Brassica oleracea var. capitata      |     427 |    30 |   650 | 159.16 |      100 |
| Cabbage Leaf | Cabbage Leaf           | Brassica oleracea (Foliage)          |     425 |    60 |   400 | 149.13 |      150 |
| Capsicum     | Bell Pepper / Capsicum | Capsicum annuum (Capsicum Group)     |     427 |   100 |  1500 | 558.75 |      550 |
| Carrot       | Carrot                 | Daucus carota                        |     426 |    70 |  1300 | 278.26 |      210 |
| Cucumber     | Cucumber               | Cucumis sativus                      |     424 |    25 |   200 | 103.99 |      100 |
| Green Chilli | Green Chilli           | Capsicum annuum (Chili pepper group) |     426 |   100 |  1500 | 447.95 |      300 |
| Knolkhol     | Kohlrabi / Knol-khol   | Brassica oleracea var. gongylodes    |     426 |    60 |   500 | 184.73 |      180 |
| Leeks        | Leeks                  | Allium ampeloprasum                  |     425 |    60 |   500 | 180.22 |      160 |
| Potato       | Potato                 | Solanum tuberosum                    |     425 |   150 |   350 | 236.26 |      230 |
| Pumpkin      | Pumpkin                | Cucurbita maxima                     |     424 |    30 |   280 | 109.74 |      105 |
| Radish       | Radish                 | Raphanus sativus                     |     427 |    20 |   150 |  62.63 |       60 |
| Salada       | Lettuce / Salada       | Lactuca sativa                       |     425 |    50 |  1800 | 242.94 |      150 |
| Tomato       | Tomato                 | Solanum lycopersicum                 |     427 |    30 |   700 | 226.78 |      170 |

## 3. Collection Process
- **How was the data acquired?** Compiled from daily price bulletins of Keppetipola Dedicated Economic Centre.
- **Temporal Coverage:** 2024-01-01 to 2026-05-29.
- **Critical Temporal Gaps & Missingness Disclosure:**
  - Of the 880 total calendar days in this overall span, 427 dates are populated and 453 days are missing.
  - **2024 Gap:** Covers Jan 1 to Mar 12 (with a gap from Feb 15 to Feb 28). April through December 2024 are completely missing.
  - **2025 Gap:** Covers Jan 1 to May 31, then June, July, and August 2025 are completely missing, resuming Sep 1 to Dec 29.
  - **2026 Gap:** Covers Jan 1 to May 29.

## 4. Preprocessing / Cleaning / Labeling
- **Data Cleaning Log:**
  - Standardized all string columns and resolved local Sinhala transliterations.
  - Corrected blatant 10x typos and dropped-zero entries (e.g., Green Chilli, Tomato, Beetroot, Capsicum, Pumpkin, Potato).
  - Set consecutive dates with identical prices across all active categories to `Carried_Forward` (Day 1 of the dataset defaults to `Observed`).

## 5. Uses
- **What can the dataset be used for?** Time series forecasting, spatial economic modelling, market integration analysis.
- **What should be avoided?** Standard random splits on validation/testing sets because of high temporal autocorrelation and carried-forward days. Use rolling-window splits instead.

## 6. Distribution
- **Licensing:** Distributed under the Apache 2.0 Licsence
- **Formats:** Standard comma-separated values (CSV).

## 7. Maintenance
- **Who maintains the dataset?** Maintained by Anton Jayakody. Please submit bug reports and queries to <anton.j@nsbm.ac.lk> or use the github repo at `https://github.com/tobijay666/Sri-Lankan-Agri-Food-Economic-Open-Data`
- **Updates:** Periodically appended as newer monthly bulletins are processed.

---

## How to Cite
If you use this dataset, please cite it as follows:

```bibtex
@misc{keppetipola_vegetable_prices_2024_2026,
  author = {Anton Jayakody},
  title = {Keppetipola Wholesale Vegetable Prices Dataset (2024-2026)},
  year = {2026},
  publisher = {Zenodo},
  doi = {https://doi.org/10.5281/zenodo.24214018},
  url = {https://github.com/tobijay666/Sri-Lankan-Agri-Food-Economic-Open-Data OR https://zenodo.org/records/24214018}
}
```
