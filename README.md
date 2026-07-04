# Multimodal Alzheimer's Disease Detection from Speech

This project explores machine learning approaches for detecting Alzheimer's disease from speech and transcripts using the DementiaBank Pitt Corpus Cookie Theft picture-description task.

The work compares text, acoustic, semantic, and multimodal fusion features for session-level classification.

## Quick Read

- **Problem:** Detect Alzheimer's disease patterns from speech and language data.
- **Dataset:** DementiaBank Pitt Corpus Cookie Theft task. Data is restricted and is not committed to this repository.
- **Approach:** Compare transcript models, acoustic speech models, semantic image-grounded features, and late-fusion classifiers.
- **Best result:** Multimodal fusion reached **86.8% accuracy**, improving over the text baseline at **83.8% accuracy**.
- **Key takeaway:** Transcript/text features were the strongest individual signal, and fusion added useful complementary information.

## Methods

### Text Models

- TF-IDF 1-2 gram features
- Logistic regression baseline
- RoBERTa transcript classification
- Sentence-transformer embeddings with `sentence-transformers/all-MiniLM-L6-v2`

### Acoustic Models

- MFCC features
- Log-mel spectrogram features
- HuBERT embeddings
- Layer-level HuBERT feature analysis

### Semantic Models

The semantic branch compares transcripts against expected Cookie Theft image concepts, such as objects, people, and actions in the picture. This measures whether a participant mentions clinically relevant visual content.

### Fusion

Late fusion combines model probabilities from text, audio, metadata, and semantic branches. Fusion weights and decision thresholds are selected on a development set and evaluated on a held-out test set.

## Results

| Model | Accuracy |
|---|---:|
| Text baseline | 83.8% |
| Multimodal fusion | 86.8% |

## Repository Layout

```text
README.md                 Project summary and results
requirements.txt          Python dependencies
.gitignore                Keeps restricted data and generated artifacts out of Git
docs/                     Setup notes and project details
notebooks/                Place cleaned experiment notebooks here
src/                      Place reusable Python modules here
results/                  Place non-sensitive plots and result summaries here
```

## How To Run

The DementiaBank data is restricted, so this repo does not include the raw corpus. After receiving access from DementiaBank/TalkBank, place data locally using the layout described in [`docs/RUNNING.md`](docs/RUNNING.md).

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook
```

Then open the cleaned notebook or scripts for the experiment branch you want to run.

## Data Access Note

This repository intentionally excludes raw DementiaBank files, transcripts, audio, derived participant-level CSVs, trained models, and pickled artifacts. Those files may contain restricted or sensitive clinical data and should remain local.

## Project Status

This repo is organized as a readable project portfolio. The next cleanup step is to add a cleaned notebook or Python pipeline under `notebooks/` or `src/` once the final experiment code is ready to share without restricted data.
