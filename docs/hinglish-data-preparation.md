# H-English / Hinglish Data Preparation

## Overview

This document describes the H-English (Hinglish/Romanized Hindi)
conversational data preparation pipeline completed as part of the LLM
data-preparation project.

H-English, also called Hinglish, refers to the use of Hindi and English
together, often with Hindi written using the Roman/English alphabet.

Example:

> Mujhe aaj office jana hai, but I will come back early.

The goal of this task was to collect approximately 50 MB of H-English
conversational data, analyze it using Pandas and NumPy, clean and refine
the data, remove duplicate conversations, perform quality checks, and
export the final dataset in JSONL format.

## Dataset Source

The dataset was obtained from the Hugging Face dataset:

`theguywithblacktie/hinglish-conversations`

The dataset contains conversational `input` and `output` fields.

## Libraries Used

-   Hugging Face `datasets`
-   Pandas
-   NumPy
-   Python `re` module
-   Python `os` module

### Purpose of Pandas

Pandas was used for loading and organizing the conversation data,
inspecting rows and columns, checking missing values, removing
duplicates, calculating statistics, and exporting/verifying JSONL data.

### Purpose of NumPy

NumPy was used for numerical processing and cumulative size calculations
while selecting approximately 50 MB of raw data.

## Data Collection

The original dataset was inspected before selecting the required subset.

### Raw Dataset

-   Raw conversations: **97,580**
-   Target size: **50 MB**
-   Actual selected size: **50.00 MB**

## Data Inspection

The selected dataset contained:

-   `input`
-   `output`

Temporary columns were used during analysis to measure input, output,
and total conversation sizes.

There were no missing values.

### Missing-value check

-   Empty inputs: **0**
-   Empty outputs: **0**

## Conversation Text Extraction

The original `input` and `output` fields contained structured
conversation messages such as:

``` text
[
    {'role': 'user', 'content': '...'},
    {'role': 'assistant', 'content': '...'}
]
```

The `content` values were extracted to create plain text fields for
cleaning and analysis.

## Cleaning Pipeline

The extracted conversation text was cleaned using Python.

The cleaning process included:

1.  Whitespace normalization
2.  URL removal
3.  Removal of unnecessary control characters
4.  Trimming leading and trailing whitespace
5.  Checking for empty conversations

Romanized Hindi words were preserved because they are part of the target
H-English data.

## Empty-Value Check

After cleaning:

-   Empty inputs: **0**
-   Empty outputs: **0**

Therefore, no conversations needed to be removed because of empty input
or output fields.

## Duplicate Detection

A combined conversation key was created from the cleaned input and
output. Exact duplicate conversations were identified and removed.

### Results

-   Before duplicate removal: **97,580**
-   Duplicate conversations: **196**
-   Unique conversations: **97,384**

## H-English Quality Check

A rule-based indicator check was performed using common Romanized-Hindi
words such as:

``` text
hai, hain, haan, nahi, mujhe, tum, aap, mera,
meri, kya, kaise, bahut, bohot, yaar, bhai,
acha, arre, matlab, wala, wali, raha, rahi,
tha, thi, toh, bhi
```

This was used as a basic quality indicator and is not a complete
language classifier.

### Results

-   Total unique conversations: **97,384**
-   Conversations with at least one H-English indicator: **97,381**
-   Conversations without an indicator: **3**
-   Average indicators per conversation: **17.40**

## Final Dataset Statistics

  Statistic                               Result
  --------------------------------- ------------
  Final conversations                     97,384
  Cleaned text size                     40.30 MB
  Total characters                    42,190,252
  Average characters/conversation         433.24
  Minimum characters                          37
  Maximum characters                       9,979
  Median characters                          280

## JSONL Export

The final dataset contains two fields:

``` text
input
output
```

It was exported as:

`hinglish_clean.jsonl`

### Final JSONL

-   Records: **97,384**
-   File size: **42.63 MB**

The JSONL file was reloaded using Pandas to verify the exported data.

### Verification

``` text
Verified rows: 97,384
Verified columns: ['input', 'output']
Missing input: 0
Missing output: 0
```

## Complete Pipeline

``` text
Hugging Face Dataset
        ↓
Inspect Dataset
        ↓
Select ~50 MB
        ↓
Pandas + NumPy Analysis
        ↓
Extract Conversation Content
        ↓
Text Cleaning
        ↓
Empty-Value Check
        ↓
Duplicate Detection
        ↓
Remove 196 Duplicates
        ↓
H-English Indicator Check
        ↓
Final Statistics
        ↓
Export JSONL
        ↓
Reload and Verify
```

## Final Output

The main output of this task is:

`hinglish_clean.jsonl`

It contains **97,384 unique H-English conversation pairs**.

The cleaned text size is approximately **40.30 MB**, and the final JSONL
file is approximately **42.63 MB**.

## Current Status

-   H-English dataset collection: **Complete**
-   Pandas analysis: **Complete**
-   NumPy-based size analysis: **Complete**
-   Text extraction: **Complete**
-   Basic cleaning: **Complete**
-   Empty-value validation: **Complete**
-   Duplicate removal: **Complete**
-   H-English indicator analysis: **Complete**
-   Final statistics: **Complete**
-   JSONL export: **Complete**
-   JSONL verification: **Complete**
-   GitHub documentation: **Ready to add**

## Notes

This work focuses on data preparation and analysis. An LLM has not been
trained using this dataset yet.

Large generated dataset files are kept separately rather than being
committed directly to the normal Git repository.
