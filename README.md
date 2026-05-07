## Project Overview
This project automates the extraction of key medical data from natural language patient encounter transcripts. Developed for **Lakeside Healthcare Network**, the system leverages the **OpenAI API** to transform dense, unstructured medical notes into a structured format suitable for insurance claims, billing, and clinical documentation.

The core objective is to accurately identify patient demographics, medical specialties, and treatment plans while automatically matching treatments with their corresponding **ICD-10** (International Classification of Diseases) codes.

## Features
- **Automated Extraction**: Pulls patient age and medical specialty directly from raw text.
- **Treatment Analysis**: Identifies recommended treatments or medication plans within the transcription.
- **ICD-10 Mapping**: Uses LLM reasoning to associate recommended treatments with standardized ICD-10 billing codes.
- **JSON Structured Output**: Utilizes OpenAI's `json_object` response format to ensure data integrity and seamless integration with Pandas.

## Technical Stack
- **Language**: Python 3.x
- **Libraries**: `pandas`, `openai`, `json`
- **Model**: OpenAI `gpt-3.5-turbo`
- **Data Format**: CSV input, structured DataFrame output

## Dataset
The project utilizes an anonymized dataset (`transcriptions.csv`) containing:
- `medical_specialty`: The original labeled specialty.
- `transcription`: Detailed medical texts including subjective complaints, objective findings, assessments, and plans.

## Implementation Details
The extraction process uses a specialized system prompt to guide the model:
1. **System Instruction**: Defines the role as an expert medical data extractor.
2. **Deterministic Output**: Sets `temperature=0.0` to ensure factual accuracy and consistent results.
3. **Structured Mapping**: Iterates through the dataset and parses JSON responses into a final pandas DataFrame named `df_structured`.

## Usage
1. **Setup**: Ensure you have an OpenAI API key configured in your environment.
2. **Install Dependencies**:
```bash
pip install pandas openai