
---

# 2. `docs/bharat-validation.md`

```markdown
# Bharat English + Hindi Validation Data Preparation

This document describes the validation-data preparation performed on the refined Bharat English and Hindi datasets.

The purpose of the validation datasets is to keep a separate portion of the prepared data that can later be used to evaluate model performance without using the same records for training.

## Validation Strategy

The validation datasets were created from the refined Bharat datasets.

A reproducible random seed was used:

`42`

Approximately 100 MB of text was selected for validation for each language.

The validation data was separated from the remaining data and checked for overlap.

## English Validation Dataset

The refined English dataset contained:

- Original records: 1,231,482

A validation subset was created with:

- Validation records: 821,026
- Target text size: 100 MB
- Random seed: 42

The remaining records were kept separate for potential training use.

### English Separation Check

- Original records: 1,231,482
- Validation records: 821,026
- Remaining records: 410,456
- Validation overlap: 0
- Validation duplicates: 0

Status:

**English validation data was properly separated.**

### English Quality Check

The validation dataset was checked for:

- Missing values
- Empty records
- Duplicate records
- Records below 50 characters
- Low-English records
- Latin-character ratio

Results:

- Missing values: 0
- Empty records: 0
- Duplicate records: 0
- Below 50 characters: 0
- Low-English records: 0

The validation dataset passed the quality check.

### English Output

The validation dataset was exported as:

`bharat_english_validation.jsonl`

Final JSONL file size:

Approximately 109.68 MB

## Hindi Validation Dataset

The refined Hindi dataset contained:

- Original records: 182,476

A validation subset was created with:

- Validation records: 121,849
- Target text size: 100 MB
- Random seed: 42

The remaining records were kept separate for potential training use.

### Hindi Separation Check

- Original records: 182,476
- Validation records: 121,849
- Remaining records: 60,627
- Validation overlap: 0
- Validation duplicates: 0

Status:

**Hindi validation data was properly separated.**

### Hindi Quality Check

The validation dataset was checked for:

- Missing values
- Empty records
- Duplicate records
- Records below 50 characters
- Low-Devanagari records
- Devanagari-character ratio

Results:

- Missing values: 0
- Empty records: 0
- Duplicate records: 0
- Below 50 characters: 0
- Low-Devanagari records: 0

The validation dataset passed the quality check.

### Hindi Output

The validation dataset was exported as:

`bharat_hindi_validation.jsonl`

Final JSONL file size:

Approximately 101.40 MB

## Final Validation Dataset Summary

| Dataset | Records | Target Text Size | JSONL Size |
|---|---:|---:|---:|
| English validation | 821,026 | 100 MB | 109.68 MB |
| Hindi validation | 121,849 | 100 MB | 101.40 MB |

## Final Validation Status

Both validation datasets were successfully:

- Created from the refined datasets
- Randomly separated using seed 42
- Checked for overlap
- Checked for duplicates
- Checked for missing values
- Checked for empty records
- Checked for minimum text length
- Checked for language/script quality
- Exported as JSONL
- Verified after export

Both datasets are ready for future model evaluation.

## Storage

The large validation JSONL files are stored in Google Drive rather than committed to the normal GitHub repository.

```text
Bharat_LLM_Data/
│
├── bharat_english_validation.jsonl
└── bharat_hindi_validation.jsonl