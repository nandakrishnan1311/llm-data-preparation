# LLM Data Preparation

This repository contains the data-preparation work for an LLM learning
project.

## Project Overview

The project started by exploring how an LLM processes text, with a focus
on tokenization. The mT5 tokenizer was tested with English, Hindi, and
mixed English-Hindi examples to understand subword tokenization, token
IDs, token counts, and characters-per-token.

The project then moved to preparing multilingual and H-English
conversational datasets for possible future LLM training and local
testing.

---

## English + Hindi Wikipedia Dataset

Approximately 150 MB of raw English Wikipedia data and 150 MB of raw
Hindi Wikipedia data were collected.

The cleaning pipeline included:

- Unicode normalization
- URL removal
- Citation-marker removal
- Removal of unwanted Wikipedia sections
- Control-character and whitespace cleanup
- Minimum text-length filtering
- Exact duplicate removal
- Language-quality checking
- Dataset statistics
- mT5 tokenization

### Final Statistics

| Dataset | Articles | Cleaned Size |
|---|---:|---:|
| English | 24,579 | 139.43 MB |
| Hindi | 21,473 | 141.69 MB |
| **Total** | **46,052** | **281.13 MB** |

### Tokenization Results

- English: approximately 37.65 million tokens
- Hindi: approximately 23.37 million tokens
- Total: approximately 61.01 million tokens
- English characters/token: approximately 3.87
- Hindi characters/token: approximately 2.53

The cleaned English, Hindi, and combined bilingual datasets were
exported as JSONL files.

---

## H-English / Hinglish Dataset

A separate H-English (Hinglish/Romanized Hindi) data-preparation task
was completed using conversational data.

The pipeline used:

- Hugging Face `datasets`
- Pandas
- NumPy
- Python regular expressions

Approximately 50 MB of raw conversational H-English data was selected.

### Final Statistics

- Raw conversations: **97,580**
- Duplicate conversations removed: **196**
- Final unique conversations: **97,384**
- Cleaned text size: approximately **40.30 MB**
- Final JSONL size: approximately **42.63 MB**
- Missing input records: **0**
- Missing output records: **0**

The final H-English dataset was exported as:

`hinglish_clean.jsonl`

For the complete H-English data-preparation pipeline, analysis,
cleaning process, and statistics, see:

`docs/hinglish-data-preparation.md`

---

## Data Preparation Approach

The general data-preparation workflow used in this project is:

```text
Data Source
    ↓
Dataset Collection
    ↓
Pandas + NumPy Analysis
    ↓
Text Extraction
    ↓
Cleaning
    ↓
Missing-Value Check
    ↓
Duplicate Detection
    ↓
Quality Check
    ↓
Dataset Statistics
    ↓
JSONL Export
    ↓
Verification