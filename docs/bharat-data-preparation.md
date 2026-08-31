# Bharat English + Hindi Data Preparation

This document describes the Bharat English and Hindi dataset preparation work completed for the LLM learning project.

## Project Overview

The Bharat data-preparation stage focused on collecting, cleaning, filtering, validating, and exporting English and Hindi text data for possible future LLM training.

The prepared datasets are stored as JSONL files in Google Drive because they are too large for the normal GitHub repository.

## Data Sources

### English

Source:

AI4Bharat Samanantar

Configuration:

- Language pair: English-Hindi
- English field: `src`

### Hindi

Source:

AI4Bharat IndicCorpV2

Language:

- Hindi
- Script: Devanagari

## English Data Preparation

Approximately 200 MB of raw English data was collected.

The cleaning pipeline included:

- Unicode and text cleanup
- Empty-text removal
- Minimum character-length filtering
- Duplicate removal
- Latin-character ratio analysis
- English language-quality filtering
- Dataset statistics
- Final size-based dataset selection
- JSONL export

### English Final Statistics

- Final records: 1,231,482
- Target text size: approximately 150 MB
- Final JSONL size: approximately 164.53 MB
- Minimum characters: 50
- Average characters: 127.72
- Median characters: 108
- Missing values: 0
- Empty records: 0
- Duplicate records: 0

The final English dataset was exported as:

`bharat_english_clean.jsonl`

## Hindi Data Preparation

Approximately 200 MB of raw Hindi data was collected from AI4Bharat IndicCorpV2.

The cleaning pipeline included:

- Text cleaning
- Empty-text removal
- Minimum character-length filtering
- Duplicate removal
- Devanagari ratio analysis
- Hindi language-quality filtering
- Dataset statistics
- Final size-based dataset selection
- JSONL export

### Hindi Final Statistics

- Final records: 182,476
- Target text size: approximately 150 MB
- Final JSONL size: approximately 152.10 MB
- Minimum characters: 50
- Average characters: 336.32
- Median characters: 254
- Missing values: 0
- Empty records: 0
- Duplicate records: 0

The final Hindi dataset was exported as:

`bharat_hindi_clean.jsonl`

## Language Quality Filtering

### English

The English dataset was evaluated using the proportion of Latin characters in each record.

This helped identify records that did not contain sufficient English-language content.

### Hindi

The Hindi dataset was evaluated using the proportion of Devanagari characters in each record.

The final Hindi dataset contained no records below the selected Devanagari-quality threshold.

## Output Files

The large JSONL files are stored outside the GitHub repository.

```text
Bharat_LLM_Data/
│
├── bharat_english_clean.jsonl
└── bharat_hindi_clean.jsonl