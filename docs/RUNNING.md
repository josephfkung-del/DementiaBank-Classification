# Running The Project

## 1. Create An Environment

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

On macOS/Linux, use:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## 2. Add Restricted Data Locally

The DementiaBank Pitt Corpus is not included in this repository. After receiving access from DementiaBank/TalkBank, keep the data outside Git.

Suggested local layout:

```text
data/
  raw/
    pitt/
      audio/
      transcripts/
  processed/
```

The `.gitignore` file excludes `data/raw/`, `data/processed/`, audio files, transcript files, and generated model artifacts.

## 3. Run Notebooks Or Scripts

Start Jupyter:

```bash
jupyter notebook
```

Open the cleaned experiment notebook once it is added under `notebooks/`.

## 4. Reproducibility Notes

Because the raw dataset is restricted, the repository is intended to show project design, modeling choices, and non-sensitive results. To fully reproduce results, a reviewer needs DementiaBank access and the same local data layout.
