# 🌍 COVID-19 Global Impact Dashboard

An interactive **Power BI dashboard** exploring the global impact of COVID-19 across **cases, deaths, vaccination, healthcare capacity, and socioeconomic indicators**.

Built using the **Our World in Data COVID-19 dataset**, this project transforms large-scale pandemic data into an interactive analytical report that allows users to explore global trends, compare countries, evaluate vaccination progress, and examine healthcare and socioeconomic context.

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat\&logo=powerbi\&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-217346?style=flat\&logo=microsoftexcel\&logoColor=white)
![Power Query](https://img.shields.io/badge/Power%20Query-742774?style=flat\&logo=microsoft\&logoColor=white)
![Our World in Data](https://img.shields.io/badge/Data-Our%20World%20in%20Data-blue)

---

## 📌 Project Overview

COVID-19 affected countries differently in terms of infection rates, mortality, vaccination coverage, healthcare capacity, and socioeconomic conditions.

This dashboard was developed to provide a **multi-dimensional view of the pandemic**, allowing users to move from a global perspective into country-level comparisons and deeper analysis of vaccination, healthcare, and socioeconomic indicators.

### The dashboard answers four key questions:

| Dashboard Page                     | Key Question                                                                         |
| ---------------------------------- | ------------------------------------------------------------------------------------ |
| 🌍 **Global Overview**             | What does the worldwide COVID-19 picture look like?                                  |
| 📍 **Country Analysis**            | How do countries compare in terms of cases, deaths, and fatality rates?              |
| 💉 **Vaccination Analysis**        | How far has vaccination progressed across different locations?                       |
| 🏥 **Healthcare & Socioeconomics** | How do healthcare capacity and socioeconomic indicators relate to COVID-19 outcomes? |

---

# 📊 Dashboard Preview

## 1. Global Overview

![Global Overview](co-vid%20pics/global-overview.png.png)

The Global Overview provides a high-level snapshot of COVID-19 activity across the selected date and location filters.

### Key metrics

* Total Cases
* Total Deaths
* New Cases
* New Deaths
* Total Vaccinations
* People Vaccinated
* People Fully Vaccinated
* Case Fatality Rate
* Positive Rate Status
* Full Vaccination Coverage Status

### Visualizations

* Monthly Cases vs. Deaths trend
* Top 10 locations by total cases
* Global geographic distribution
* Interactive filtering by date, continent, and location

---

## 2. Country Analysis

![Country Analysis](co-vid%20pics/country-analysis.png.png)

The Country Analysis page provides a more detailed comparison of COVID-19 outcomes across individual locations.

### Key metrics

* Population
* Median Age
* Human Development Index
* GDP per Capita
* Population Density
* Positive Rate
* Total Cases
* Total Deaths
* Case Fatality Rate

### Visualizations

* New Cases vs. New Deaths trend
* Cases per Million comparison
* Country-level comparison table
* Case Fatality Rate and status
* Demographic and socioeconomic indicators

---

## 3. Vaccination Analysis

![Vaccination Analysis](co-vid%20pics/vaccination-analysis.png.png)

This page focuses on global vaccination rollout and coverage.

### Key metrics

* Total Vaccinations
* People Vaccinated
* People Fully Vaccinated
* New Vaccinations
* Full Vaccination Coverage Status

### Visualizations

* Vaccination rollout trend
* People Vaccinated vs. Fully Vaccinated
* Vaccination coverage gauge
* Top 10 locations by vaccinations
* Location-level vaccination coverage table

A **70% full-vaccination benchmark** is used to classify locations as either:

* 🟢 **High — Above 70%**
* 🔴 **Low — Below 70%**

---

## 4. Healthcare & Socioeconomics

![Healthcare & Socioeconomics](co-vid%20pics/healthcare-socioeconomics.png.png)

This page adds healthcare and socioeconomic context to the analysis.

### Key metrics

* Hospital Beds per Thousand
* ICU Patients
* Hospital Patients
* Average Reproduction Rate
* GDP per Capita

### Visualizations

* Monthly ICU and hospital patient trends
* Hospital Beds per Thousand by continent
* GDP per Capita vs. Case Fatality Rate
* Continent-level socioeconomic comparison

### Additional indicators

* Diabetes prevalence
* Cardiovascular death rate
* Median age
* GDP per capita

> **Important:** Relationships shown in the dashboard are descriptive and should not be interpreted as evidence of causation.

---

# 🔎 Analytical Highlights

The dashboard enables exploration of several important patterns within the dataset.

### 🌍 Global COVID-19 Impact

Users can examine how cumulative cases and deaths evolved over time and identify locations with the highest reported case volumes.

### 💉 Vaccination Coverage

Vaccination progress varied considerably across locations, allowing users to identify countries above or below the **70% full-vaccination benchmark**.

### 🏥 Healthcare Capacity

Hospital beds, ICU patients, and hospital patients provide additional context for understanding differences in healthcare capacity and pandemic burden.

### 💰 Socioeconomic Context

GDP per capita, human development, population characteristics, diabetes prevalence, and cardiovascular mortality provide additional dimensions for comparing countries and regions.

---

# 🧮 DAX & Data Analysis

The report uses DAX measures to calculate KPIs, ratios, rates, and conditional classifications dynamically based on the selected filters.

### Case Fatality Rate

```dax
Case Fatality Rate =
DIVIDE(
    [Total Deaths],
    [Total Cases]
)
```

### Fully Vaccinated Rate

```dax
Fully Vaccinated Rate % =
DIVIDE(
    [People Fully Vaccinated],
    [Population]
)
```

### Full Vaccination Coverage Status

```dax
Full Vaccination Coverage Status =
IF(
    [Fully Vaccinated Rate %] > 0.70,
    "High - Above 70%",
    "Low - Below 70%"
)
```

### Positive Rate Status

```dax
Positive Rate Status =
IF(
    [Positive Rate] > 0.05,
    "High - Above 5%",
    "Low - At or below 5%"
)
```

---

# ⚙️ Data Modeling Considerations

One of the important considerations when working with the dataset is the difference between **daily values, cumulative values, and static country-level attributes**.

Cumulative fields such as:

* `total_cases`
* `total_deaths`
* `total_vaccinations`
* `people_vaccinated`
* `people_fully_vaccinated`

are repeated across daily records.

Simply summing these fields across all dates would therefore produce misleading results.

The report instead uses **latest available date/value logic**, including `LASTNONBLANK` and `MAX` where appropriate, to ensure cumulative metrics represent the selected point in time rather than the sum of repeated historical values.

Static attributes such as population, median age, GDP per capita, and population density are also handled differently from daily measures.

---

# 🗂️ Dataset

### Source

**Our World in Data — COVID-19 Dataset**

The dataset contains COVID-19 statistics and related demographic, healthcare, and socioeconomic indicators for countries and regions around the world.

### Data grain

**One row per location per date**

### Key fields

#### COVID-19

* `total_cases`
* `new_cases`
* `total_deaths`
* `new_deaths`

#### Vaccination

* `total_vaccinations`
* `people_vaccinated`
* `people_fully_vaccinated`
* `new_vaccinations`

#### Healthcare

* `hospital_beds_per_thousand`
* `icu_patients`
* `hosp_patients`

#### Demographics

* `population`
* `population_density`
* `median_age`

#### Socioeconomic indicators

* `gdp_per_capita`
* `human_development_index`
* `diabetes_prevalence`
* `cardiovasc_death_rate`

---

# 🛠️ Tools & Technologies

| Technology            | Purpose                                            |
| --------------------- | -------------------------------------------------- |
| **Power BI Desktop**  | Dashboard development and visualization            |
| **Power Query**       | Data cleaning and transformation                   |
| **DAX**               | Measures, KPIs, calculations and conditional logic |
| **Our World in Data** | Source dataset                                     |

---

# 📈 Skills Demonstrated

This project demonstrates practical experience in:

* Data cleaning and transformation
* Power Query
* Data modeling
* DAX
* KPI development
* Time-series analysis
* Comparative analysis
* Geographic visualization
* Data visualization
* Conditional logic
* Interactive dashboard design
* Data storytelling

---

# 🚀 How to Use

### 1. Clone the repository

```bash
git clone https://github.com/olatomzy2/Covid-19-Analysis.git
```

### 2. Open the Power BI file

Open:

```text
Covid-19_Analysis.pbix
```

using **Power BI Desktop**.

### 3. Refresh the dataset

If Power BI prompts you to update or reconnect the data source, follow the prompts to refresh the underlying dataset.

### 4. Explore the dashboard

Use the navigation bar and filters to explore:

**Global Overview → Country Analysis → Vaccination Analysis → Healthcare & Socioeconomics**

---

# 📁 Repository Structure

```text
Covid-19-Analysis/
│
├── Covid-19_Analysis.pbix
│
├── co-vid pics/
│   ├── global-overview.png.png
│   ├── country-analysis.png.png
│   ├── vaccination-analysis.png.png
│   └── healthcare-socioeconomics.png.png
│
└── README.md
```

---

# 👤 Author

## Emmanuel Tomiwa Agboola

**Data Analyst | Power BI · SQL · Python**

🔗 **LinkedIn:**
https://www.linkedin.com/in/emmanueltomiwaagboola

💻 **GitHub:**
https://github.com/olatomzy2

---

# 📚 Data Source

**Our World in Data**

COVID-19 Dataset:
https://github.com/owid/covid-19-data

---

## ⭐ If you found this project useful

Feel free to explore the repository, review the dashboard, and connect with the author on LinkedIn.
