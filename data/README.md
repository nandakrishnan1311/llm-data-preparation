# Data

This directory contains documentation for the datasets used in the LLM data-preparation project.

Large generated dataset files are intentionally not committed directly to the normal Git repository.

## Previous English and Hindi Dataset

The English and Hindi Wikipedia data-preparation pipeline produced:

- English cleaned dataset: approximately 143.12 MB
- Hindi cleaned dataset: approximately 144.61 MB
- Combined English-Hindi dataset: approximately 287.73 MB

The datasets were exported in JSONL format and shared separately.

## H-English Dataset

The H-English (Hinglish/Romanized Hindi) data-preparation pipeline produced:

- `hinglish_clean.jsonl`
- Approximately 42.63 MB
- 97,384 unique conversation pairs

The detailed H-English pipeline and statistics are documented separately in:

`docs/hinglish-data-preparation.md`

## Data Processing

The project uses Python, Pandas, NumPy, and the Hugging Face `datasets` library for dataset collection, processing, cleaning, analysis, and export.

The corresponding notebooks contain the reproducible data-preparation pipelines.

## Important

Large generated datasets should not be committed directly to the normal Git repository unless the project explicitly requires it and an appropriate large-file-storage solution has been configured.
