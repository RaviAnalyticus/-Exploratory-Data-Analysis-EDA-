# Titanic Dataset - Exploratory Data Analysis (EDA)

**Data Analyst Internship - Task 5 (Elevate Labs)**

## Objective
Extract insights from the Titanic passenger data using visual and statistical exploration - find patterns, trends, relationships and anomalies, and understand which factors influenced survival.

## Dataset
Titanic passenger dataset (891 passengers, 12 columns: `Survived`, `Pclass`, `Name`, `Sex`, `Age`, `SibSp`, `Parch`, `Ticket`, `Fare`, `Cabin`, `Embarked`, ...).

## Tools
Python, Pandas, NumPy, Matplotlib, Seaborn, SciPy, Jupyter Notebook

## What I did
1. **Data understanding** - `.info()`, `.describe()`, `.value_counts()`, missing-value analysis
2. **Cleaning and feature engineering** - filled `Embarked`, turned `Cabin` into `HasCabin`, created `FamilySize`, `IsAlone`, `Title`, `AgeGroup`, `LogFare`
3. **Univariate analysis** - histograms, count plots, boxplots (IQR outliers), log transform for skewed `Fare`
4. **Bivariate analysis** - survival rate by sex, class, port, family size, age group and title; boxplots; scatterplot
5. **Multivariate analysis** - `sns.pairplot()`, correlation `sns.heatmap()`, survival-rate heatmaps (Pclass x Sex, Pclass x AgeGroup)
6. **Statistical checks** - chi-square tests, Mann-Whitney U, VIF for multicollinearity
7. **Observations written under every visual**, anomalies list, summary of findings and answers to the interview questions

## Key findings
- Only **38.4%** of passengers survived (342 of 891).
- **Sex** was the strongest factor: 74.2% of women vs 18.9% of men survived, and the gap holds in every class.
- **Class** mattered: 63.0% (1st), 47.3% (2nd), 24.2% (3rd). Fare, cabin availability and age follow the same class ladder.
- **Children (0-12)** survived at 58.0%; passengers travelling alone (30.4%) or in families of 5+ (16.1%) did worse than families of 2-4 (55-72%).
- 3rd-class women (50.0%) survived more often than 1st-class men (36.9%).
- Data quality: `Cabin` 77% missing, `Age` 20% missing (not random), `Fare` heavily skewed (4.79 to 0.39 after log transform), 15 zero-fare passengers.
- `FamilySize` is redundant with `SibSp` + `Parch` (correlation 0.89 / 0.78).

## Repository structure
```
.
├── Titanic_EDA.ipynb          # full analysis with code, outputs and observations
├── Titanic_EDA_Report.pdf     # PDF report of findings
├── data/
│   ├── titanic.csv            # raw dataset
│   └── titanic_clean.csv      # cleaned data with engineered features
├── figures/                   # all 16 saved charts (PNG)
├── requirements.txt
└── README.md
```

## How to run
```bash
pip install -r requirements.txt
jupyter notebook Titanic_EDA.ipynb
```
Run the notebook from the repository root so the relative `data/` and `figures/` paths work.
