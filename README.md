# DDoS Attack Detection

Binary classification of network traffic (benign vs DDoS) using the CIC-DDoS2019 dataset.

**Course:** AI Methods in Cybersecurity — Politechnika Krakowska, sem. 2  
**Models:** Random Forest, SVM

## Setup

```bash
git clone https://github.com/KonSprin/MSI-DDoS_Detection.git
cd MSI-DDoS_Detection

poetry install

poetry run jupyter notebook
```

## Running with Docker

The easiest way to run the project is via Docker — no local Python setup required.

```bash
docker compose up --build
```

Then open Jupyter at `http://localhost:8888` (no password required).

Run the notebooks in order:

1. `02_preprocessing.ipynb` — cleans the raw data and saves `data/processed/ddos_basic_preprocessed.csv`
2. `03_modeling.ipynb` — trains Random Forest and Linear SVM, evaluates on the test set, saves models

Use `Kernel → Restart & Run All` in each notebook.

## Dataset

Download **CIC-DDoS2019** from `https://www.unb.ca/cic/datasets/ddos-2019.html` and place the CSV files in `data/raw/`. Raw data is not committed to the repo.

## Project structure

```txt
data/             # (gitignored)
  raw/ 
    CSVs          # raw CSVs 
    PCAPs         # raw PCAPs
  processed/    # cleaned data ready for training
notebooks/      # one notebook per task (EDA, preprocessing, models, evaluation)
src/
  ddos_detection/   # shared helper code
reports/
  figures/      # saved plots
tests/
```

## Contributing

### Branches

Work on a feature branch, never commit directly to `main`.

```bash
git checkout -b feature/your-task-name
```

Suggested naming: `feature/eda`, `feature/random-forest`, `feature/svm`, etc.

### Workflow

1. Pull latest `main` before starting any work.
2. Make small, focused commits.
3. Open a pull request when done — at least one teammate reviews before merging.

### Commits

Write commit messages in English, lowercase, present tense:

```txt
add confusion matrix plot
fix class imbalance in preprocessing
update README with dataset instructions
```

### Notebooks

- One notebook per task (e.g. `01_eda.ipynb`, `03_random_forest.ipynb`).
- Clear all outputs before committing (`Kernel -> Restart & Clear Output`).
- Make sure the notebook runs top-to-bottom without errors.

### Data

Never commit files from `data/raw/` or `data/processed/` — they are gitignored.
Share data via the group chat or a shared drive link.

### Dependencies

If you need a new library, add it via Poetry — do not edit `pyproject.toml` by hand:

```bash
poetry add <package-name>
```

Then commit the updated `pyproject.toml`.
