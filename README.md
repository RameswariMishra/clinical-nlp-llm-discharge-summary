# Clinical NLP and LLM Pipeline for Structured Extraction from Hospital Discharge Summaries

## Overview

Healthcare systems generate large volumes of unstructured clinical documents such as discharge summaries. Extracting structured information from these documents is essential for analytics, research, and decision support.

This project builds an **end-to-end NLP pipeline** that converts **unstructured discharge summary PDFs into structured clinical datasets** using rule-based extraction and Large Language Model (LLM) techniques.

The resulting structured dataset can be used for **healthcare analytics, dashboards, and downstream machine learning applications**.

---

## Objective

The goal of this project is to transform **unstructured hospital discharge summaries into structured machine-readable data**.

The pipeline extracts the following clinical attributes:

- Patient Age
- Gender
- Final Diagnosis
- Symptoms
- Medications
- Procedures

Missing values are standardized as **"Not available"** to ensure dataset consistency.

---

## Dataset Source

This project uses a **preview subset of the Healthcare Discharge Summary Dataset available on Kaggle**.

Dataset link:  
https://www.kaggle.com/datasets/infobayai/healthcare-discharge-summary

The dataset contains hospital discharge summary reports that include clinical information such as:

- patient demographics
- diagnosis
- symptoms
- medications
- procedures

The dataset is provided as a **sample dataset for experimentation and pipeline validation**.

### Data Access

The dataset is **not included in this repository due to licensing restrictions**.

To reproduce this project:

1. Download the dataset from Kaggle.
2. Place the discharge summary PDF files inside the `data/` folder.
3. Run the notebook pipeline.

---

## Project Workflow

The pipeline converts unstructured clinical documents into structured datasets through the following stages:

PDF Discharge Summary
        ↓
Text Extraction
        ↓
Rule-Based NLP Extraction
        ↓
LLM-Based Structured Extraction
        ↓
Structured Dataset
        ↓
Power BI Dashboard


---

## Technologies Used

- Python
- Jupyter Notebook
- Pandas
- pdfplumber
- Regular Expressions (Regex)
- spaCy (NLP)
- Large Language Models (LLM)
- Power BI
- GitHub Actions (CI/CD)

---

## NLP Extraction Fields

The rule-based NLP pipeline extracts key clinical attributes from discharge summaries using text processing and regular expressions.

Extracted fields include:

- **Patient Age** – extracted from demographic information.
- **Gender** – identified from the "Age / Sex" section.
- **Final Diagnosis** – extracted from the "FINAL DIAGNOSIS" section.
- **Symptoms** – identified from clinical complaint descriptions.
- **Medications** – extracted from discharge medication sections.
- **Procedures** – extracted from surgery or procedure sections.

These fields are stored in a structured dataframe and exported as a dataset for analysis.

---

## LLM-Based Structured Output

In addition to rule-based extraction, the pipeline includes an **LLM-based information extraction layer**.

The Large Language Model processes the discharge summary and returns structured JSON output containing clinical attributes.

Example output:

```json
{
  "patient_age": "52",
  "gender": "Female",
  "diagnosis": "Dengue Fever",
  "symptoms": ["fever", "body ache", "nausea"],
  "medications": ["Paracetamol", "Levocetirizine"],
  "procedures": ["Not available"]
}
 ```
The LLM-based approach demonstrates improved flexibility in handling variations in clinical text and document formatting.

### Results

Two extraction approaches were implemented and compared:

### Method	Description
Rule-Based NLP	Uses regex patterns and structured text parsing
LLM-Based Extraction	Uses language models to interpret clinical context

The LLM-based approach produced more accurate and complete extraction results, especially for symptoms, medications, and procedures.

## Dashboard

The structured dataset generated from the NLP pipeline visualized using a Power BI dashboard.

The analytics include:

Diagnosis distribution

Patient demographic analysis

Symptom frequency

Medication usage patterns

Procedure counts

These visualizations demonstrate how structured clinical data can support healthcare analytics and decision-making.

## CI/CD Pipeline

A GitHub Actions CI/CD workflow is included to ensure project reliability.

The automated pipeline performs:

1. Dependency installation from requirements.txt

2. Python environment validation

3. Pipeline dependency checks

4. Automated validation of required libraries

This ensures that the project remains reproducible and functional across environments.

## Project Structure

clinical-nlp-llm-discharge-summary/

notebooks/
└── clinical_nlp_llm_pipeline.ipynb

src/
├── pdf_extraction.py
├── rule_based_extraction.py
├── llm_extraction.py

outputs/
├── structured_discharge_dataset.csv
└── sample_llm_output.json

dashboard/
└── powerbi_dashboard.png

.github/
└── workflows/
└── ci.yml

requirements.txt
README.md
.gitignore

## How to Run
### 1. Clone the repository
git clone https://github.com/RameswariMishra/clinical-nlp-llm-discharge-summary

### 2. Install Requirements Document
pip install -r requirements.txt

### 3. Download the dataset
Download the discharge summary dataset from Kaggle and place the PDF files inside: data/

### 4. Run the notebook
notebooks/clinical_nlp_llm_pipeline.ipynb

## Future Improvements

Potential future enhancements include:

1. Clinical Named Entity Recognition (NER) for diseases and medications

2. Automated diagnosis classification

3. Integration with electronic health record (EHR) systems

4. Scalable deployment using Databricks

5. Containerized deployment using Docker and Kubernetes

6. Real-time clinical document processing APIs

## Conclusion

This project demonstrates how Natural Language Processing and Large Language Models can convert unstructured clinical documents into structured datasets.

Such pipelines can support healthcare analytics, clinical research, and intelligent decision-support systems.

The combination of document processing, NLP extraction, LLM-based structuring, and dashboard visualization provides a scalable approach to transforming clinical text into actionable data.

