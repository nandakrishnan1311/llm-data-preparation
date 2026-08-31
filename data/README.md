# Data

This directory is reserved for dataset information and documentation.

Large generated datasets are intentionally stored outside the normal Git repository.

---

## English + Hindi Wikipedia Datasets

The original English and Hindi Wikipedia data-preparation work produced:

- English cleaned dataset: approximately 139.43 MB
- Hindi cleaned dataset: approximately 141.69 MB
- Combined cleaned dataset: approximately 281.13 MB

The datasets were cleaned, filtered, analyzed, and exported as JSONL files.

---

## H-English / Hinglish Dataset

The H-English data-preparation task produced:

- `hinglish_clean.jsonl`
- Records: 97,384
- Cleaned text size: approximately 40.30 MB
- JSONL size: approximately 42.63 MB

The dataset is stored outside GitHub because of its size.

---

## Bharat Datasets

The Bharat data-preparation work produced cleaned English and Hindi datasets.

### Bharat English

- Source: AI4Bharat Samanantar
- Final records: 1,231,482
- Target text size: approximately 150 MB
- JSONL size: approximately 164.53 MB
- Output: `bharat_english_clean.jsonl`

### Bharat Hindi

- Source: AI4Bharat IndicCorpV2
- Language: Hindi
- Script: Devanagari
- Final records: 182,476
- Target text size: approximately 150 MB
- JSONL size: approximately 152.10 MB
- Output: `bharat_hindi_clean.jsonl`

---

## Bharat Validation Datasets

Separate validation datasets were created from the refined Bharat English and Hindi datasets.

A reproducible random seed of `42` was used.

### English Validation

- Records: 821,026
- Target text size: 100 MB
- JSONL size: approximately 109.68 MB
- Validation overlap: 0
- Duplicate records: 0
- Output: `bharat_english_validation.jsonl`

### Hindi Validation

- Records: 121,849
- Target text size: 100 MB
- JSONL size: approximately 101.40 MB
- Validation overlap: 0
- Duplicate records: 0
- Output: `bharat_hindi_validation.jsonl`

Both validation datasets passed their quality checks.

---

## Large Dataset Files

The following large JSONL files are stored in Google Drive rather than committed to GitHub:

```text
bharat_english_clean.jsonl
bharat_hindi_clean.jsonl
bharat_english_validation.jsonl
bharat_hindi_validation.jsonl
hinglish_clean.jsonl