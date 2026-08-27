# Data

This directory is reserved for dataset files used by the project.

## Large Dataset Files

Large JSONL datasets are intentionally not committed to the normal Git
repository.

The English/Hindi dataset work produced:

-   English cleaned dataset: approximately 143.12 MB
-   Hindi cleaned dataset: approximately 144.61 MB
-   Combined English-Hindi dataset: approximately 287.73 MB

The H-English task produced:

-   `hinglish_clean.jsonl`: approximately 42.63 MB
-   Records: 97,384

For reproducibility, the notebook contains the data collection,
cleaning, analysis, and export pipeline.

## Important

Do not commit large generated datasets to GitHub unless the project
explicitly requires it and an appropriate large-file-storage solution
has been configured.
