# LLM Data Preparation

This repository contains the data-preparation work for an LLM learning project.

## Project Overview

The project started by exploring how an LLM processes text, with a focus on tokenization. The mT5 tokenizer was tested with English, Hindi, and mixed English-Hindi examples to understand subword tokenization, token IDs, token counts, and characters-per-token.

The next stages focused on preparing English, Hindi, and H-English datasets for possible future LLM training.

The project currently focuses on:

- Dataset collection
- Text cleaning
- Language-quality filtering
- Dataset analysis
- Tokenization analysis
- Validation dataset preparation
- Reproducible data pipelines

An LLM has not yet been trained using these datasets.

---

## English + Hindi Wikipedia Dataset

Approximately 150 MB of raw English Wikipedia data and 150 MB of raw Hindi Wikipedia data were collected.

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

Tokenization results:

- English: approximately 37.65 million tokens
- Hindi: approximately 23.37 million tokens
- Total: approximately 61.01 million tokens
- English characters/token: approximately 3.87
- Hindi characters/token: approximately 2.53

The cleaned English, Hindi, and combined bilingual datasets were exported as JSONL files.

---

## H-English / Hinglish Dataset

A separate H-English (Hinglish/Romanized Hindi) data-preparation task was completed afterward.

The pipeline used:

- Hugging Face `datasets`
- Pandas
- NumPy
- Python regular expressions

Approximately 50 MB of raw conversational H-English data was selected.

### Results

- Raw conversations: 97,580
- Duplicate conversations removed: 196
- Final unique conversations: 97,384
- Cleaned text size: approximately 40.30 MB
- Final JSONL size: approximately 42.63 MB
- Final records: 97,384
- Missing input records: 0
- Missing output records: 0

The H-English dataset was exported as:

`hinglish_clean.jsonl`

Detailed methodology is documented in:

`docs/hinglish-data-preparation.md`

---

# Bharat English + Hindi Dataset

A new Bharat data-preparation stage was completed using AI4Bharat datasets.

The objective was to prepare cleaned English and Hindi text datasets for future LLM experiments.

## Bharat English Dataset

The English dataset was prepared from:

**AI4Bharat Samanantar**

Configuration:

- Language pair: English-Hindi
- English field: `src`

Approximately 200 MB of raw English data was collected.

The cleaning pipeline included:

- Text cleaning
- Empty-text removal
- Minimum character-length filtering
- Duplicate removal
- Latin-character ratio analysis
- English language-quality filtering
- Dataset statistics
- Final size-based dataset selection
- JSONL export

### Final English Statistics

- Final records: 1,231,482
- Target text size: approximately 150 MB
- Final JSONL size: approximately 164.53 MB
- Minimum characters: 50
- Average characters: 127.72
- Median characters: 108
- Missing values: 0
- Empty records: 0
- Duplicate records: 0

Output:

`bharat_english_clean.jsonl`

## Bharat Hindi Dataset

The Hindi dataset was prepared from:

**AI4Bharat IndicCorpV2**

Language:

- Hindi
- Script: Devanagari

Approximately 200 MB of raw Hindi data was collected.

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

### Final Hindi Statistics

- Final records: 182,476
- Target text size: approximately 150 MB
- Final JSONL size: approximately 152.10 MB
- Minimum characters: 50
- Average characters: 336.32
- Median characters: 254
- Missing values: 0
- Empty records: 0
- Duplicate records: 0

Output:

`bharat_hindi_clean.jsonl`

### Language Quality Filtering

For English, the proportion of Latin characters was used to identify records with insufficient English-language content.

For Hindi, the proportion of Devanagari characters was used to identify records with insufficient Hindi-script content.

Detailed Bharat preparation methodology is documented in:

`docs/bharat-data-preparation.md`

---

# Bharat Validation Dataset

A separate validation-data preparation stage was completed using the refined Bharat English and Hindi datasets.

The purpose of the validation datasets is to keep a separate portion of the prepared data that can later be used for model evaluation without using the same records for training.

A reproducible random seed was used:

`42`

Approximately 100 MB of text was selected for validation for each language.

## English Validation

Source dataset:

`bharat_english_clean.jsonl`

Results:

- Original records: 1,231,482
- Validation records: 821,026
- Remaining records: 410,456
- Target validation text: 100 MB
- Final JSONL size: 109.68 MB
- Validation overlap: 0
- Validation duplicates: 0

Quality checks:

- Missing values: 0
- Empty records: 0
- Duplicate records: 0
- Below 50 characters: 0
- Low-English records: 0

Output:

`bharat_english_validation.jsonl`

## Hindi Validation

Source dataset:

`bharat_hindi_clean.jsonl`

Results:

- Original records: 182,476
- Validation records: 121,849
- Remaining records: 60,627
- Target validation text: 100 MB
- Final JSONL size: 101.40 MB
- Validation overlap: 0
- Validation duplicates: 0

Quality checks:

- Missing values: 0
- Empty records: 0
- Duplicate records: 0
- Below 50 characters: 0
- Low-Devanagari records: 0

Output:

`bharat_hindi_validation.jsonl`

## Validation Dataset Summary

| Dataset | Records | Target Text Size | JSONL Size |
|---|---:|---:|---:|
| English validation | 821,026 | 100 MB | 109.68 MB |
| Hindi validation | 121,849 | 100 MB | 101.40 MB |

Both validation datasets were successfully separated, quality-checked, exported, and verified.

Detailed validation methodology is documented in:

`docs/bharat-validation.md`

---

# Data Storage

Large generated JSONL datasets are intentionally not committed to the normal Git repository.

The Bharat datasets are stored separately in Google Drive.

The repository contains the notebooks and documentation required to reproduce the preparation and validation pipelines.

Examples of externally stored datasets include:

```text
bharat_english_clean.jsonl
bharat_hindi_clean.jsonl
bharat_english_validation.jsonl
bharat_hindi_validation.jsonl
hinglish_clean.jsonl