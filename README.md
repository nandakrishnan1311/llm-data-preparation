# LLM Data Preparation

This repository contains the data-preparation work for an LLM learning
project.

## Project Overview

The project started by exploring how an LLM processes text, with a focus
on tokenization. The mT5 tokenizer was tested with English, Hindi, and
mixed English-Hindi examples to understand subword tokenization, token
IDs, token counts, and characters-per-token.

The next stage was preparing English and Hindi Wikipedia data for
possible future LLM training.

## English + Hindi Dataset

Approximately 150 MB of raw English Wikipedia data and 150 MB of raw
Hindi Wikipedia data were collected.

The cleaning pipeline included:

-   Unicode normalization
-   URL removal
-   Citation-marker removal
-   Removal of unwanted Wikipedia sections
-   Control-character and whitespace cleanup
-   Minimum text-length filtering
-   Exact duplicate removal
-   Language-quality checking
-   Dataset statistics
-   mT5 tokenization

### Final Statistics

  Dataset         Articles    Cleaned Size
  ----------- ------------ ---------------
  English           24,579       139.43 MB
  Hindi             21,473       141.69 MB
  **Total**     **46,052**   **281.13 MB**

Tokenization results:

-   English: approximately 37.65 million tokens
-   Hindi: approximately 23.37 million tokens
-   Total: approximately 61.01 million tokens
-   English characters/token: approximately 3.87
-   Hindi characters/token: approximately 2.53

The cleaned English, Hindi, and combined bilingual datasets were
exported as JSONL files.

## H-English / Hinglish Work

A separate H-English (Hinglish/Romanized Hindi) data-preparation task
was started afterward.

The pipeline used:

-   Hugging Face `datasets`
-   Pandas
-   NumPy
-   Python regular expressions

Approximately 50 MB of raw conversational H-English data was selected.

Results:

-   Raw conversations: 97,580
-   Duplicate conversations removed: 196
-   Final unique conversations: 97,384
-   Cleaned text size: approximately 40.30 MB
-   Final JSONL size: approximately 42.63 MB
-   Final records: 97,384
-   Missing input records: 0
-   Missing output records: 0

The H-English dataset was exported as:

`hinglish_clean.jsonl`

## Current Scope

This repository documents **data preparation and tokenizer analysis**.
An LLM has not yet been trained using PyTorch or TensorFlow.

Future learning stages include:

-   Tensors
-   Matrix multiplication
-   Embeddings
-   Attention
-   Automatic differentiation
-   Loss functions
-   Backpropagation
-   Optimization
-   Eventually building and training model components

## Repository Structure

``` text
llm-data-preparation/
│
├── english-hindi-llm-data-preparation.ipynb
├── README.md
├── requirements.txt
└── data/
    └── README.md
```
