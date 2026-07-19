# Data directory

The original research dataset was created from 111 one-page World Trade Organization dispute-summary PDFs.

## Folder use

```text
data/
├── raw/
│   └── wto_case_pdfs/       # Place permitted source PDFs here
└── processed/
    ├── wto_cases.csv
    ├── preprocessed_wto_cases.csv
    ├── title_embeddings.npy
    ├── summary_embeddings.npy
    └── articles_embeddings.npy
```

Generated data files are excluded from Git because they are derived artefacts and the source-document permissions should be checked before redistribution.

## Expected initial CSV schema

| Column | Description |
|---|---|
| Case ID | WTO dispute identifier |
| Title | Case title |
| Complainant | Complainant party |
| Respondent | Respondent party |
| Date | Adoption date or `Unknown` |
| Articles | Relevant agreement provisions |
| Summary | Extracted findings summary |

## Workflow

1. Place the WTO summary PDFs in `data/raw/wto_case_pdfs/`.
2. Run `notebooks/01_dataset_creation.ipynb`.
3. Run `notebooks/02_data_cleaning.ipynb`.
4. Run `notebooks/03_data_preprocessing.ipynb`.
5. Use the processed outputs in the retrieval notebooks.

The extraction code expects filenames that include the WTO case identifier and removes the `sum_e` prefix and `.pdf` suffix when creating the `Case ID`.
