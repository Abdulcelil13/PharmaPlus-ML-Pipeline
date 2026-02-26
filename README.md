# PharmaPlus-ML-Pipeline
PharmaPlus ML Pipeline 💊🤖

#An AI-driven data pipeline for the *Pharma+* project. This repository contains the Machine Learning architecture and documentation designed to process complex pharmacist data inputs and transform them into structured, database-ready formats using advanced LLM techniques.

## 🚀 Phase 1: LLM Integration & Data Extraction
The first phase of the ML pipeline focuses on safely extracting and structuring medical data from manual pharmacist inputs or drug requests. 

### Key Methodologies (Prompt Engineering)
Instead of standard summarization, advanced Prompt Engineering techniques were implemented to ensure high-quality data mining:
* *Extracting & Transforming (Proofreading):* Automatically corrects spelling and typing errors from manual inputs and transforms the raw text directly into a nested JSON format.
* *Condition Checking (Zero-Hallucination):* The model is strictly prohibited from hallucinating data. Unfound string values return "Not Specified", and empty arrays return [].
* *Multi-Task Inferring:* Complex warning texts are successfully categorized in a single cycle into TargetCondition, Food_interactions, and Drug_interactions.

### Model Selection & Benchmarks
After stress-testing Gemini and GPT-4o models across 5 edge-case scenarios (including typo-heavy texts, missing data, and irrelevant inputs), *Gemini Pro* was selected as the core engine. It maintained 100% format integrity and demonstrated the highest logical inference capacity suitable for upcoming Apriori algorithm integrations.

## 📋 Data Contract: Final JSON Schema
The pipeline outputs the following standardized format, ready for Backend integration and directly mapped to the DB team's Drugs table:

```json
{
  "Name": "string",
  "Manufacturer": "string",
  "Dosage_form": "string",
  "Recommended_Dosage": "string",
  "Age_of_use": "string",
  "Storage": "string",
  "Side_Effect": ["string", "string"],
  "Warning": {
    "TargetCondition": ["string"],
    "Food_interactions": ["string"],
    "Drug_interactions": ["string"]
  }
}
```
Note:For full stress-test results and architectural details,please review the Phase 1 Report PDF located in this Repository.

