# ArXive TF–IDF + Zero-shot Term Extractor & Classifier

A research prototype for extracting and classifying domain-specific terms from arXiv papers using TF–IDF to propose candidate terms and a zero-shot classifier to label or filter those candidates. Intended for researchers and engineers who want an interpretable, easily-repeatable pipeline for term extraction from scientific documents.

## Features
- Candidate-term extraction using TF–IDF (document- and corpus-level scoring).
- Zero-shot classification / filtering to assign labels or decide relevance for candidate terms (no task-specific fine-tuning required).
- Interactive Colab-ready Jupyter notebook demonstrating the end-to-end workflow.
- Designed for experimentation on arXiv (PDF/text) datasets or other scientific corpora.

## Why this exists
Many domain-specific terminology extraction systems require extensive labeled data or heavy NLP pipelines. This project provides a lightweight pipeline that pairs unsupervised TF–IDF ranking with a zero-shot model to rapidly produce and filter candidate domain terms, enabling fast iteration when labeled datasets are unavailable.

## Quicklinks
- Notebook: MY_term_extraction_ipynb".ipynb (Colab-compatible)
- Example usage: open the notebook in Google Colab to run on GPU

## Stack
- **Language(s):** Python (notebook-based)
- **Runtime / environment:** Jupyter / Google Colab (GPU recommended for zero-shot models)
- **Notable libraries (suggested):** scikit-learn (TF–IDF), pandas, numpy, transformers (Hugging Face) or similar zero-shot/NLI models, sentence-transformers (optional), torch

## Getting started (Colab)
1. Open the provided notebook in Colab (recommended for quick GPU-backed runs).
2. Follow the notebook cells: install dependencies, upload or mount your dataset, then run the extraction and classification cells.

## Quick local setup
1. Clone the repository:
   git clone https://github.com/Kate-PSU/ArXive_TF-IDF_Zeroshot_term_extractor_classifier.git
2. Create and activate a Python virtual environment:
   python -m venv .venv
   source .venv/bin/activate   # macOS / Linux
   .venv\Scripts\activate      # Windows
3. Install dependencies:
   - If the repo has a requirements.txt:
       pip install -r requirements.txt
   - Otherwise, install common packages used by the notebook:
       pip install pandas numpy scikit-learn transformers torch sentence-transformers jupyterlab tqdm
4. Launch Jupyter:
   jupyter lab
5. Open the notebook MY_term_extraction_ipynb".ipynb (recommend renaming to MY_term_extraction_ipynb.ipynb to avoid issues).

## Typical workflow (what the notebook does)
1. Data ingestion: load arXiv paper text (plain text, extracted full text, or abstracts).
2. Preprocessing: tokenization, normalization, stopword removal, optional lemmatization.
3. TF–IDF candidate generation: compute TF–IDF across the corpus and select top-scoring n-grams per document (configurable n and k).
4. Candidate filtering & ranking: optional heuristics (POS filters, frequency thresholds).
5. Zero-shot classification / labeling: use a pre-trained zero-shot model (NLI or hypothesis-based classifier) to accept/reject or label candidates against a set of target labels or hypotheses.
6. Output & analysis: aggregated term lists, per-document term lists, and basic evaluation metrics.

## Configuration & important knobs
- n-gram size (unigram/bi-gram/tri-gram)
- min document frequency or global frequency thresholds
- top-k TF–IDF candidates per document
- zero-shot model & hypothesis templates
- GPU vs CPU: zero-shot models run much faster on GPU

## Notes on files & models
- The notebook appears prepared for Colab (includes widgets and progress bars).
- There are references to model artifacts (e.g., model.safetensors, tokenizer_config.json) — if you plan to use local model files, place them in a models/ directory or configure the notebook to load from Hugging Face.
- Consider adding a requirements.txt to pin versions for reproducibility.

## Evaluation
- Add a small labeled evaluation set (term presence or term-label pairs) to report precision, recall, and F1 for extracted/filtered terms.
- Compare TF–IDF-only baselines vs TF–IDF + zero-shot filtering.

## Recommended next steps
- Add a requirements.txt or environment.yml for reproducibility.
- Rename the notebook file to remove embedded quote characters (e.g., MY_term_extraction_ipynb.ipynb).
- Add a LICENSE (MIT recommended for research prototypes) and a CONTRIBUTING.md if you want collaborators.
- Add a sample dataset or a small demo to validate end-to-end results quickly.

## Contributing
1. Fork the repository and create a feature branch.
2. Add tests or a runnable demo where possible.
3. Open a pull request describing your changes.

## License
- Add a LICENSE file. MIT or Apache-2.0 are common choices for research code; pick one and add it to the repo.

## Contact
- Maintainer: Kate-PSU (GitHub)
- For questions, open an issue or a discussion on the repository.
