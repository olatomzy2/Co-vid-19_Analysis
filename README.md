# COVID-19 Global Impact Dashboard

An interactive **Power BI** dashboard analyzing the global impact of COVID-19 — cases, deaths, vaccinations, healthcare capacity, and socioeconomic context — built on the [Our World in Data](https://ourworldindata.org/covid-deaths) COVID-19 dataset.

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-217346?style=flat&logo=microsoftexcel&logoColor=white)

---

## 📊 Overview

The report is split into four pages, each answering a different question about the pandemic's global impact:

| Page | What it answers |
|---|---|
| **Global Overview** | What's the current worldwide picture — total cases, deaths, vaccination progress, and the monthly trend? |
| **Country Analysis** | How does one country or region compare to others on cases, deaths, and case fatality? |
| **Vaccination Analysis** | How far has vaccine rollout progressed, and which locations are above/below a coverage target? |
| **Healthcare & Socioeconomics Analysis** | How do hospital capacity, GDP, and other socioeconomic factors relate to outcomes? |

All four pages share a common filter panel (Date, Continent/Location) and a consistent navigation bar, so any page can be explored independently or used to drill from a global view into a single country.

---

## 🖼️ Screenshots

![Global Overview](co-vid%20pics/global-overview.png.png)

![Country Analysis](co-vid%20pics/country-analysis.png.png)

![Vaccination Analysis](co-vid%20pics/vaccination-analysis.png.png)

![Healthcare & Socioeconomics Analysis](co-vid%20pics/healthcare-socioeconomics.png.png)

---

## 📁 Pages in detail

### 1. Global Overview
KPI cards for Total Cases, Total Deaths, New Cases, New Deaths, Vaccinations, People Vaccinated, People Fully Vaccinated, Case Fatality Rate, and two status indicators (Positive Rate Status, Full Vaccination Coverage Status). Below the cards: a monthly Cases-vs-Deaths trend line, a Top 10 locations by cases bar chart, and a world map.

### 2. Country Analysis
KPI cards plus gauge visuals for Population, Median Age, Human Development Index, GDP per Capita, Population Density, and Positive Rate. A trend chart of New Cases/New Deaths by location and month, a Cases Per Million bar chart, and a sortable country-level table with Case Fatality Rate and Status.

### 3. Vaccination Analysis
KPI cards for Vaccinations, People Vaccinated, People Fully Vaccinated, Full Vaccination Coverage Status, and New Vaccinations. A rollout trend chart (People Vaccinated vs. Fully Vaccinated over time), a radial gauge tracking coverage against a target, a Top 10 locations by vaccinations bar chart, and a location-level coverage table.

### 4. Healthcare & Socioeconomics Analysis
KPI cards for Hospital Beds per Thousand, ICU Patients, Hospital Patients, Average Reproduction Rate, and GDP per Capita. A monthly ICU/Hospital patients trend, a Hospital Beds per Thousand by continent bar chart, a GDP-per-capita vs. Case Fatality Rate scatter plot, and a continent-level socioeconomic indicators table (diabetes prevalence, cardiovascular death rate, median age).

---

## 🧮 Key DAX measures

A few of the core measures behind the report (add the rest of your measures here as the model grows):

```dax
Case Fatality Rate =
DIVIDE([Total Deaths], [Total Cases])

Fully Vaccinated Rate % =
DIVIDE([People Fully Vaccinated], [Population])

Full Vaccination Coverage Status =
IF([Fully Vaccinated Rate %] > 0.70, "High - Above 70%", "Low - Below 70%")

Positive Rate Status =
IF([Positive Rate] > 0.05, "High - Above 5%", "Low - At or below 5%")
```

> **Note on cumulative fields:** the underlying dataset repeats cumulative figures (e.g. `total_cases`, `people_fully_vaccinated`) and static fields (e.g. `population`) on every daily row. Measures that need a single point-in-time value use `LASTNONBLANK` / `MAX` over `date` rather than a plain `SUM`, so totals reflect the latest available date instead of summing across every row.

---

## 🗂️ Data source

- **Dataset:** [Our World in Data — COVID-19 dataset](https://github.com/owid/covid-19-data)
- **Grain:** one row per location per date
- **Key fields used:** `location`, `continent`, `date`, `total_cases`, `total_deaths`, `new_cases`, `new_deaths`, `people_vaccinated`, `people_fully_vaccinated`, `total_vaccinations`, `hospital_beds_per_thousand`, `icu_patients`, `hosp_patients`, `gdp_per_capita`, `human_development_index`, `population`, `population_density`, `median_age`, `diabetes_prevalence`, `cardiovasc_death_rate`

---

## 🛠️ Tools used

- **Power BI Desktop** — data modeling, DAX measures, report design
- **Power Query** — data shaping and transformation
- **DAX** — calculated measures and conditional status logic

---

## 🚀 Getting started

1. Clone this repository.
2. Open `Covid-19_Analysis.pbix` in Power BI Desktop.
3. If prompted, refresh the data source connection.
4. Explore the four report pages via the navigation bar at the top of each page.

---

## 👤 Author

**Emmanuel Tomiwa Agboola**
Data Analyst | Power BI · SQL · Python

- LinkedIn: [linkedin.com/in/emmanueltomiwaagboola](https://www.linkedin.com/in/emmanueltomiwaagboola)
- GitHub: [github.com/olatomzy2](https://github.com/olatomzy2)
