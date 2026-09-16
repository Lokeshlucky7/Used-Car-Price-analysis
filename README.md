# Used Cars Price Analysis

An end-to-end data analytics project examining used car pricing trends across 8 major Indian cities, using listings scraped from CarWale.

---

## Problem Statement

The Indian pre-owned car market is fragmented, and buyers face real friction when trying to compare options:

- No clarity on how prices differ across brands and models
- Hard to identify reliable vehicles within a given budget
- Inconsistent EMI and financing options for comparable cars
- No easy way to compare listings side by side

This project applies a structured analytics approach to real listing data to make those comparisons possible.

---

## Objectives

- Extract used car listings from CarWale across multiple cities
- Analyze pricing trends by brand, fuel type, EMI structure, model year, and location
- Identify cars offering the best balance of cost and value
- Present findings through clear, interactive dashboards

---

## Data

**Source:** CarWale (used cars section), scraped with Python

**Cities covered (8):** Ahmedabad, Bangalore, Chennai, Delhi, Gurgaon, Hyderabad, Mumbai, Pune

**Fields captured:**

| Field | Description |
|---|---|
| Car Name | Make and model |
| Company Name | Manufacturer (derived during cleaning) |
| CarModelYear | Year of manufacture |
| Kilometers Travelled | Odometer reading |
| Fuel Type | Petrol / Diesel / CNG etc. |
| Transmission | Manual / Automatic |
| Ownership | First owner, second owner, etc. |
| EMI | Estimated monthly EMI |
| Price | Listed sale price |

---

## Methodology

**1. Data Acquisition**
Scraped listings city by city using `requests` and `BeautifulSoup`, storing raw output per city in `data/raw/`.

**2. Data Cleaning & Preprocessing**
- Converted currency-formatted strings (₹, commas, "Lakh") into numeric values
- Handled missing and null entries
- Standardized naming for fuel types and car brands
- Derived `Company Name` from the full car name
- Removed duplicates and enforced consistent data types

**3. Analysis & Visualization**
- Brand vs. price comparison
- Fuel type distribution and its relationship to price
- EMI vs. price scatter analysis
- Listing counts per manufacturer

Built as interactive dashboards in Tableau.

---

## Repo Structure

```
UsedCarsPriceAnalysis/
├── notebooks/
│   ├── WebScraping.ipynb       # Scraping listings from CarWale
│   └── DataCleaning.ipynb      # Cleaning, merging, standardizing
├── data/
│   ├── raw/                    # Raw scraped listings, one file per city
│   └── processed/
│       ├── FullData.xlsx       # Merged raw listings
│       ├── CleanedData.xlsx    # Cleaned, analysis-ready dataset
│       └── MasterDataset.xlsx  # Consolidated master file
├── tableau/
│   └── Project2.twb            # Tableau workbook with dashboards
├── reports/
│   ├── Used_Cars_Price_Analysis_Report.docx
│   └── Used_Cars_Price_Analysis_Clean_Presentation.pptx
└── README.md
```

---

## Tools & Technologies

| Purpose | Tools / Libraries |
|---|---|
| Data Extraction | BeautifulSoup, requests |
| Data Processing | Pandas, NumPy |
| Visualization | Tableau, Matplotlib |
| Environment | Jupyter Notebook |
| Reporting | Word, PowerPoint |

---

## How to Reproduce

1. **Scrape (optional):** Run `notebooks/WebScraping.ipynb` to pull fresh listings — or skip this and use the pre-scraped files already in `data/raw/`.
2. **Clean:** Run `notebooks/DataCleaning.ipynb` to merge city files and produce `data/processed/CleanedData.xlsx`.
3. **Visualize:** Open `tableau/Project2.twb` in Tableau Desktop or Tableau Public to explore the dashboards.

**Requirements:** Python 3.x with `pandas`, `numpy`, `beautifulsoup4`, `requests`, `openpyxl`

```bash
pip install pandas numpy beautifulsoup4 requests openpyxl
```

---

## Challenges Encountered

- **Dynamic HTML:** CarWale's markup made scraping slow and error-prone, requiring careful selector handling
- **Request blocking:** Frequent rate limiting during scraping runs
- **Inconsistent formatting:** Price and EMI values came in mixed formats needing normalization
- **Noisy listings:** Promotional content mixed into genuine listings

---

## Scope & Limitations

This is a snapshot analysis of a sample of listings (under 200 records after cleaning), not an exhaustive market study. It demonstrates the full pipeline — scrape, clean, analyze, visualize — rather than aiming for statistical representativeness. Extending the scrape volume would be the natural next step.

---

## Possible Extensions

- Predict future price trends and estimate depreciation curves
- Rank vehicles by value-for-money score
- Expand to more cities and a larger listing volume

---

## Author

**Lokeswararao Adada**
