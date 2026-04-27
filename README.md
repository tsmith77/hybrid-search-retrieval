# Hybrid Retrieval with PubMedQA

This project builds a simple hybrid search pipeline for biomedical research data using the PubMedQA dataset.

It combines:

- Dense retrieval for semantic meaning
- Sparse retrieval for keyword matching
- Hybrid retrieval to bring both approaches together

The current project logic lives in [`hybrid-retrieval.py`](/Users/teasmith/Documents/IQ_homeworks/hybrid-retrieval.py).

## What This Project Does

The script:

1. Loads the `qiaojin/PubMedQA` dataset
2. Selects a small training subset for faster experimentation
3. Cleans the data
4. Builds searchable text from the PubMedQA context and long answer
5. Generates:
   - Sparse embeddings with SPLADE
   - Dense embeddings with BGE

This is a good starting point for a hybrid biomedical search system.

## Project Structure

```text
IQ_homeworks/
├── hybrid-retrieval.py
├── README.md
├── .env
└── .venv/
```

## Requirements

You will need:

- Python 3.10+
- A virtual environment
- Internet access to download models and the dataset the first time you run the script

Main Python packages used in the script:

- `numpy`
- `pandas`
- `datasets`
- `qdrant-client`
- `transformers`
- `fastembed`

## Setup

Create and activate a virtual environment if you do not already have one:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Install the required packages:

```bash
pip install numpy pandas datasets qdrant-client transformers fastembed
```

## How to Run

From the project folder, run:

```bash
python hybrid-retrieval.py
```

## What to Expect

When the script runs, it should:

- Print the installed `fastembed` version
- Load the PubMedQA dataset
- Keep the first 100 rows from the training split
- Remove duplicate and incomplete records
- Build a `combined_text` field for each document
- Generate sparse embeddings
- Generate dense embeddings

## Current Notes

- The script currently focuses on data loading, cleaning, and embedding generation.
- Qdrant imports are present, but indexing and search logic do not appear to be completed yet.
- Because large models are used, the first run may take some time.

## Troubleshooting

If the script fails, these are the most likely causes:

- Missing Python packages
- Model download issues on first run
- Dataset download/network issues
- Limited memory while loading embedding models

A quick fix is usually:

```bash
pip install --upgrade pip
pip install numpy pandas datasets qdrant-client transformers fastembed
```

## Next Improvements

Good next steps for this project would be:

- Add Qdrant collection creation
- Store both dense and sparse vectors
- Implement dense-only, sparse-only, and hybrid search
- Add Reciprocal Rank Fusion (RRF)
- Add example queries and result comparisons
- Add a `requirements.txt` file

## Summary

This repository is an early hybrid retrieval prototype for biomedical question answering. It is set up to prepare PubMedQA data and generate the embeddings needed for a future hybrid search workflow.
