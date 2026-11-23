# lyon-equipements-population
 
A university group project (master's in Digital Humanities, ENSSIB – Université Lumière Lyon 2, academic year 2025–2026): a Jupyter notebook that explores whether the types of public facilities present in a commune relate to its population, using two open datasets.
 
This is a student exercise at beginner-to-intermediate level, not a production tool. Its authors describe it themselves as a first analysis with several methodological limits (see [Limitations](#limitations)).
 
> The notebook and the report are written in French.
 
## Research question
 
Do the types of public facilities (schools, cultural venues, health services, etc.) found in a commune of the Métropole de Lyon relate to the commune's population size?
 
## Repository structure
 
```
lyon-equipements-population/
├── data/
│   ├── equipements-publics-metropole-lyon.csv
│   ├── population-annuelle-communes-metropole-lyon.csv
│   └── DATA_SOURCES.md          # origin, licence and modifications of the data
├── docs/
│   └── rapport_analyse_equipements_publics.pdf   # written report (French)
├── notebooks/
│   └── analyse_equipements_population.ipynb      # the analysis
├── requirements.txt
└── README.md
```
 
## Data
 
Both datasets come from the open data portal of the Métropole de Lyon ([data.grandlyon.com](https://data.grandlyon.com)) and are published under the Licence Ouverte v2.0 (Etalab).
 
| File | Content |
|---|---|
| `equipements-publics-metropole-lyon.csv` | 728 public facilities: theme, type, name, address, commune, INSEE code, coordinates |
| `population-annuelle-communes-metropole-lyon.csv` | Annual population per commune, from 1876 to 2022 |
 
Files are `;`-separated and UTF-8 with BOM. The contact columns (`tel`, `email`, `web`) were removed from the facilities file before publication. See [`data/DATA_SOURCES.md`](data/DATA_SOURCES.md) for full details, licence and credit.
 
## Method
 
The notebook follows these steps:
 
1. **Import and cleaning**: load both CSV files, keep the useful columns of the facilities table and drop incomplete rows.
2. **Join** of the two tables on the INSEE code, then harmonisation of the facility theme labels (typos, duplicate categories).
3. **Descriptive statistics**: number of facilities per theme and per commune.
4. **Multiple correspondence analysis (MCA)**: population is recoded into three artificial classes (small / medium / large) and crossed with the presence or absence of each facility theme; eigenvalues are corrected with Benzécri's correction.
5. **Principal component analysis (PCA)**: number of facilities per theme, crossed with the 2022 population as a quantitative variable.
The full interpretation of the results is in the report: [`docs/rapport_analyse_equipements_publics.pdf`](docs/rapport_analyse_equipements_publics.pdf).
 
## Getting started
 
### Requirements
 
- Python 3
- The packages listed in `requirements.txt` (versions are intentionally not pinned). The notebook was run with pandas 3.
### Installation
 
```bash
git clone https://github.com/parangocom/lyon-equipements-population.git
cd lyon-equipements-population
 
python -m venv .venv
source .venv/bin/activate        # on Windows: .venv\Scripts\activate
pip install -r requirements.txt
```
 
### Run the notebook
 
Launch Jupyter **from the `notebooks/` folder**, because the notebook reads the data with relative paths (`../data/...`):
 
```bash
cd notebooks
jupyter notebook analyse_equipements_population.ipynb
```
 
## Limitations
 
- Population is recoded into three arbitrary classes to be crossed with qualitative variables; the class boundaries are a choice of the authors.
- In the MCA, facility counts are capped at 1 (presence/absence), so the number of facilities per commune does not influence that analysis. The PCA partly addresses this.
- Column-point labels in the MCA output are generic (`col0_0`, `col0_1`, …), which makes that part of the results hard to read.
- The join keeps only communes present in both files, and the facilities file is a snapshot whose retrieval date is not recorded.
- This is an exploratory analysis, not a statistical test of a causal relationship.
## Authors
 
Group project by students of the master's in Digital Humanities (ENSSIB – Université Lumière Lyon 2), 2025–2026. The authors' names are on the cover of the report.
 
## Licence and credit
 
The data are reused under the Licence Ouverte v2.0 (Etalab). Source credit: *Métropole de Lyon, data.grandlyon.com, Licence Ouverte v2.0 (Etalab)*.
 
No licence has been chosen yet for the notebook and the report.
