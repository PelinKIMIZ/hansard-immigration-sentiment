# Emotional Analysis of UK Parliamentary Immigration Debates (2023–2025)

Sentiment and emotion analysis of 2,468 speeches from the UK House of Commons, comparing Conservative and Labour parties on immigration-related language before and after the July 2024 general election.

## Overview

This project collects, processes, and analyses parliamentary debate data to answer the question: **Do Conservative and Labour MPs differ in emotional tone and intensity when discussing immigration, and how did the July 2024 institutional shift affect this?**

The analysis pipeline spans two notebooks — data collection and analysis — and combines NLP sentiment tools with statistical hypothesis testing.

## Notebooks

| Notebook | Description |
|---|---|
| [`hansard_immigration_data_collection.ipynb`](hansard_immigration_data_collection.ipynb) | Collects speeches from 839 XML debate files, filters by immigration keywords, maps speakers to parties via the UK Parliament Members API |
| [`hansard_immigration_analysis.ipynb`](hansard_immigration_analysis.ipynb) | VADER sentiment analysis, NRC-VAD arousal & dominance scoring, pre/post election comparison, visualisation |

## Research Question

> Do Conservative and Labour parties differ in emotional tone (valence) and emotional intensity (arousal) when discussing immigration in UK parliamentary debates, and how does the July 2024 institutional shift influence this?

## Key Findings

- **Conservatives speak more positively** about immigration overall (VADER compound: 0.301 vs Labour's 0.175)
- The word **"asylum"** shows the largest partisan gap — Conservatives score 0.343 vs Labour's 0.107
- Interestingly, **"migrant"** reverses this pattern — Labour scores higher (0.236) than Conservatives (0.147)
- **After the July 2024 election**, Labour's arousal increased significantly (p < 0.001, Mann-Whitney U), while the Conservative shift was not statistically significant (p = 0.64) — consistent with Labour transitioning from opposition to government
- Both parties show similar dominance levels, suggesting comparable assertiveness in parliamentary language

## Methods & Tools

**Language:** Python  
**Key packages:** `requests`, `beautifulsoup4`, `lxml`, `pandas`, `numpy`, `vaderSentiment`, `nltk`, `scipy`, `matplotlib`  
**NLP tools:** VADER (valence/sentiment) · NRC-VAD v2.1 (arousal, dominance)  
**Statistical test:** Mann-Whitney U test (pre vs post election comparison)

## Data Sources

- [mySociety ParlParse XML](http://www.theyworkforyou.com/pwdata/scrapedxml/debates/) — UK House of Commons debate transcripts (Hansard), 839 files (2023–2025)
- [UK Parliament Members API](https://members-api.parliament.uk) — MP name → party mapping (current and former MPs)

## Corpus

- **839** XML debate files scanned (2023–2025)
- **2,468** immigration-related speeches extracted
- **Keywords:** `immigration`, `migrant`, `asylum`
- Conservative speeches: 1,084 | Labour speeches: 1,384

## Repository Structure

```
├── hansard_immigration_data_collection.ipynb   # Data collection pipeline
├── hansard_immigration_analysis.ipynb          # Sentiment & emotion analysis
└── hansard_immigration_analysis_final.csv      # Final dataset (optional)
```

## How to Reproduce

```bash
pip install requests pandas beautifulsoup4 lxml vaderSentiment nltk scipy matplotlib
```

```python
# Step 1: Run data collection notebook
# hansard_immigration_data_collection.ipynb
# → Outputs: hansard_immigration_raw.csv

# Step 2: Run analysis notebook
# hansard_immigration_analysis.ipynb
# → Outputs: hansard_immigration_analysis_final.csv + figures
```

> Data is collected live from public APIs; no local data files needed to reproduce.
