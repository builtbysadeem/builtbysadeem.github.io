# Global GDP Atlas

A Power BI dashboard on world GDP from 1960 to 2025. It covers 217 economies across three pages: a global overview, regions and income groups, and a spotlight on Saudi Arabia and the GCC.

**[Read the interactive story](https://builtbysadeem.github.io/Global-GDP-Atlas/)** · **[View the dashboard (PDF)](Global_GDP_Atlas.pdf)**

---

## Highlights (2025)

| | |
|---|---|
| World GDP | **$118.4T**, up 6.0% on 2024 |
| Largest economy | **United States**, 26% of world GDP |
| Fastest-growing region | **South Asia**, 6.6% a year over 10 years |
| Saudi Arabia | **#18** in the world at $1.25T (2024) |

---

## Pages

### 1. Global Overview
World GDP, growth, the largest economy and how many economies have reported for the selected year. A treemap by region, the top 10 economies and world GDP since 1960.

### 2. Regions & Income
How each region's share has changed over time, GDP split by income group, 10-year growth by region, and a region-by-decade matrix.

### 3. Country Spotlight
Choose any country to see its GDP, growth, world rank and 10-year CAGR. Also shows how it compares within the GCC, its share of GCC GDP and how its rank has changed.

---

## Data Model

A star schema built from the cleaned World Bank file:

```
Fact_GDP (CountryCode, Year, GDP_USD)
   ├── *:1 ── Dim_Country (CountryCode, CountryName, Region, IncomeGroup, EntityType, IsGCC)
   └── *:1 ── Dim_Year    (Year, Decade)
```

- Regional and income aggregates are kept apart from countries using `EntityType`
- World GDP comes from the official World Bank `WLD` row, not from adding up countries

## DAX Measures

About 30 measures, grouped as follows:

- **Core:** `GDP`, `GDP Countries`, `World GDP`
- **Growth:** `YoY %`, `World YoY %`, `CAGR 10Y`
- **Share & rank:** `Share of World`, `Share of GCC`, `World Rank`, `High / Low Income Share`
- **Dynamic text:** `Largest Economy`, `Largest Region`, `Fastest Region`, plus subtitle measures that update with the selected year
- **Conditional colour:** colours for regions, income groups and growth

---

## Files

| File | Description |
|---|---|
| `Sadeem_GDP_Atlas.pbix` | The Power BI report (open it in Power BI Desktop) |
| `Global_GDP_Atlas.pdf` | All pages exported as a PDF |
| `index.html` | The interactive web version, served with GitHub Pages |
| `GDP_PowerBI_Model.xlsx` | The cleaned data model |

---

## Data Source

**World Bank, World Development Indicators**
GDP (current US$), indicator `NY.GDP.MKTP.CD`
https://data.worldbank.org/indicator/NY.GDP.MKTP.CD
Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Last updated 13 July 2026.

**Notes**
- Values are in current US dollars and are not adjusted for inflation
- For 2025, 186 of the 217 economies had published data at the time of the update
- Full GCC coverage begins in 1970, and the UAE has no 2025 value yet, so GCC comparisons use 2024

---

## Tools

Power BI Desktop · Power Query · DAX · Python (data cleaning)

---

## Contact

**Sadeem Hasan**
Website: [sadeem.tech](https://sadeem.tech)
Email: [Sadeem.connect@gmail.com](mailto:Sadeem.connect@gmail.com)
LinkedIn: [linkedin.com/in/sadeemhasan](https://linkedin.com/in/sadeemhasan)
