# TMDb Movie Dataset — Exploratory Data Analysis

**Data Analytics Project**  
**Gautami Thakur | University of Galway, 2025**

Exploratory data analysis of 10,000 movies from The Movie Database (TMDb), investigating what drives movie popularity, profitability, and genre trends across decades.

---

## Overview

This project analyses a real-world TMDb dataset to answer five data-driven questions about the film industry. It covers the full EDA workflow — data wrangling, feature engineering, and visual exploration — using Python, Pandas, Matplotlib, and Seaborn.

---

## Repository Structure

```
├── DA_MD.ipynb         # Full analysis notebook
├── tmdb-movies.csv     # TMDb dataset (10,000 movies)
└── README.md
```

---

## Research Questions

| # | Question |
|---|---|
| 1 | Does a higher budget lead to higher popularity? Is there a measurable relationship? |
| 2 | How does runtime affect popularity? What length performs best? |
| 3 | Does higher popularity translate to higher profits? |
| 4 | What features characterise the top 10 highest-revenue movies? |
| 5 | Which genres are most popular, and how has this changed over time? |

---

## Dataset

Source: [The Movie Database (TMDb)](https://www.themoviedb.org/)  
10,000 movies with the following key fields:

| Column | Description |
|---|---|
| `budget` | Production budget (USD) |
| `revenue` | Box office revenue (USD) |
| `popularity` | TMDb popularity score |
| `runtime` | Film duration in minutes |
| `vote_count` | Number of user votes |
| `vote_average` | Average user rating |
| `genres` | Pipe-separated genre list |
| `release_year` | Year of release |
| `cast`, `director` | Key talent |
| `production_companies` | Studio(s) |

---

## Data Wrangling

- Dropped irrelevant columns: `id`, `imdb_id`, `homepage`, `overview`
- Filled missing string fields (`cast`, `director`, `tagline`, `keywords`, `genres`, `production_companies`) with `"missing"`
- Replaced zero-value budgets with `NaN` (unreported, not zero)
- Removed duplicate rows
- Engineered `profit` column: `revenue − budget`
- Extracted primary genre per film for per-genre trend analysis

---

## Analysis & Findings

### Q1 — Budget vs Popularity
Scatter plot showed no obvious linear correlation. After splitting films into low/high budget groups at the median, high-budget films averaged **over 50% higher popularity** than low-budget films.

> Higher budget → significantly higher average popularity.

### Q2 — Runtime vs Popularity
Bar chart and scatter plot across short (<100 min), medium, and long (>200 min) runtime groups. Films under 200 minutes cluster at higher popularity scores; very long films rarely achieve high popularity.

> Films perform best between 100–200 minutes. Beyond 200 minutes, popularity drops sharply.

### Q3 — Popularity vs Profit
Split on median popularity. High-popularity films generated substantially higher average net profit than low-popularity films.

> Popularity is a strong signal of profitability.

### Q4 — Top 10 Revenue Movies
Histogram analysis of the top 10 highest-grossing films revealed shared characteristics:
- Runtime: 100–200 minutes
- Release years: concentrated between 1995–2015
- High budgets with correspondingly high revenues

### Q5 — Genre Trends Over Time
Parsed pipe-separated genre fields to count per-genre occurrences across all films. Top 5 genres: **Drama, Comedy, Action, Horror, Adventure**. Per-year release counts show a steady increase in film output from 1984 to 2014, with rising budgets and revenues over time.

> Genre diversity and production scale have grown consistently across decades.

---

## Limitations

- Many budget and revenue values are missing or recorded as zero, which may skew profit calculations
- Popularity and vote count methodologies are not fully disclosed by TMDb
- No currency normalisation — international films are compared without exchange rate or inflation adjustments
- Analysis covers up to 2015; trends may differ in more recent years

---

## Tech Stack

- **Python** — Pandas, NumPy
- **Matplotlib / Seaborn** — Visualisation
- **Jupyter Notebook** — Analysis environment

---

## How to Run

```bash
git clone https://github.com/gautami9t/DA_MD.git
cd DA_MD
pip install pandas matplotlib seaborn numpy jupyter
jupyter notebook DA_MD.ipynb
```
