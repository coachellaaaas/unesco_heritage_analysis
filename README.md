# UNESCO Heritage Atlas

I built this as a personal data project to explore the full UNESCO World Heritage dataset — 1,248 sites across 171 countries, spanning nearly five decades of inscriptions from 1978 to 2025.

The goal was simple: clean the data properly, find what's interesting, and present it in a way that's actually enjoyable to explore.

🌍 **[View Live Dashboard](https://coachellaaaas.github.io/personal-portfolio/projects/unesco-heritage/)**

---

## What it does

The dashboard lets you filter by continent and category, and everything updates at once — the charts, the map, and the site browser. It's built as a pure static site with no backend, so it runs entirely in the browser.

- **Inscriptions Over Time** — how many sites got inscribed each year, going back to 1978
- **By Category** — the split between Cultural, Natural, and Mixed sites
- **Top 15 Countries** — hover over a bar and it lights up green
- **Category by Continent** — which continents lean cultural vs natural
- **World Map** — every site plotted on a dark Leaflet map, colour-coded by category, with hover popups showing the site name, country, and year
- **Site Browser** — a searchable, paginated table to look up any site by name or country

---

## How the data was cleaned

The raw dataset had a lot to untangle — multilingual columns for five languages, coordinates bundled into a single string, and transboundary sites where one site belongs to multiple countries listed in the same cell.

```
Raw CSV
    ↓ Drop multilingual columns (FR, ES, RU, AR, ZH variants)
    ↓ Rename columns for readability
    ↓ Split "lat,long" string → Latitude and Longitude columns
    ↓ Split + explode Countries and ISO Codes into individual rows
    ↓ Map countries → Continents using country_converter
    ↓ Separate North America from South America
    ↓ Clean up long official country names (e.g. "United Kingdom of Great Britain...")
    ↓ Export to heritage.json
```

The explode step was the trickiest part — a transboundary site like the Ancient Beech Forests spans 18 countries, so it needed to be split into 18 separate rows while keeping everything else intact. That's why the dataset goes from 1,248 unique sites to 1,354 rows after exploding.

---

## What I found

A few things surprised me when I actually looked at the data:

- **Italy and China are almost tied** at 61 and 60 sites respectively — I expected a bigger gap
- **2000 was by far the biggest year**, with 61 new inscriptions — nearly double most other years
- **Europe's cultural dominance is striking** — 432 Cultural sites, more than Asia, Africa, and the Americas combined
- **Oceania bucks the trend** — it has more Natural sites than Cultural ones, which makes sense given how much of it is wilderness
- **106 sites span multiple countries**, which caused a fun data wrangling problem

---

## Stack

**Analysis:** Python, Pandas, NumPy, Matplotlib, Seaborn, country_converter

**Dashboard:** HTML/CSS/JS, Plotly.js (charts), Leaflet.js + CartoDB dark tiles (map), GitHub Pages (hosting)

---

## Project structure

```
unesco-heritage/
├── index.html          ← the dashboard
├── heritage.json       ← cleaned dataset
├── analysis.ipynb      ← full EDA notebook
├── data/               ← raw source data
└── README.md
```

---

## Dataset

From the [UNESCO World Heritage Centre](https://whc.unesco.org/en/list/) — 1,248 sites, 171 countries, 1978–2025.

---

**Piyathida Suwannakat** — [Portfolio](https://coachellaaaas.github.io/personal-portfolio/) · [GitHub](https://github.com/coachellaaaas) · [LinkedIn](https://www.linkedin.com/in/piyathida-suwannakat)