# Healthcare ETL Mini Project

## Overview
This project implements an ETL (Extract, Transform, Load) pipeline for a healthcare admissions dataset using Python and pandas in Google Colab. The pipeline reads raw patient admission records, cleans and transforms them, generates summary reports, and saves the final processed dataset.

## Data Source
- File: `healthcare_dataset.csv`
- 55,500 patient records, 15 columns
- Format: CSV (structured data)
- Static dataset — not regularly updated
- Contains patient details (Name, Age, Gender, Blood Type), medical details (Medical Condition, Medication, Test Results), hospital information (Doctor, Hospital, Room Number, Admission Type), admission dates, billing amount, and insurance provider

## Project Structure
```
Healthcare_ETL_Project/
│
├── raw_data/       # Raw extracted copy of the source CSV
├── reports/        # Generated reports (cleaned dataset, top/bottom billing, summary stats)
├── output/         # Final cleaned and transformed dataset
└── Mini_project.ipynb   # Notebook containing the full pipeline
```

## Pipeline Stages
The pipeline follows this flow:

```
Healthcare Dataset → Extract → Validate Data → Clean Data →
Transform Data → Analyze Data → Generate Reports → Load
```

1. **extract()** – Reads `healthcare_dataset.csv` from Google Drive, prints the record and column counts, and saves a raw copy to `raw_data/`.
2. **transform()** – Removes duplicates, standardizes column names and text fields, converts date columns to datetime, calculates `length_of_stay`, standardizes gender values, and filters out invalid billing amounts.
3. **generate_reports()** – Produces four reports and saves them to `reports/`:
   - Complete cleaned dataset
   - Top 10 highest-billing records
   - Bottom 10 lowest-billing records
   - Summary statistics
4. **load()** – Saves the final cleaned dataset to `output/` and confirms all reports were generated correctly.

## Running the Pipeline
The entire pipeline runs through a single entry-point function:

```python
def run_pipeline():
  raw = extract()
  transformed = transform(raw)
  load(transformed)

if __name__ == "__main__":
  run_pipeline()
```

In the notebook, running the final cell executes `run_pipeline()`, which chains Extract → Transform → Load.

## Requirements
- Python 3
- pandas
- Google Colab 

## Author
Nanda
