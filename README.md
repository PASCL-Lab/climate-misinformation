# Climate Misinformation

> Early-stage research notebooks exploring transformer and knowledge-graph approaches to climate-change misinformation detection.

## Overview

This repository collects the exploratory work conducted at PASCL Lab (UBC) on detecting climate-change misinformation from short text. Under `UBC_project/` it contains the Jupyter notebooks used to prototype a RoBERTa-based classifier, a BERT baseline, a knowledge-graph augmentation track, and a notebook that combines transformer and knowledge-graph signals into a single decision pipeline. A cleaned dataset, a reference Flask serving script, and links to the trained RoBERTa weights are included so that subsequent work — including the lab's downstream explainable classifier and browser extension — can reproduce these experiments. The repository captures the research investigation rather than a production deployment.

## Research Context

This codebase forms part of PASCL Lab's broader programme on climate misinformation detection and seeds the lab's downstream Domain-Aware Transformer with XAI work.

## Features

- End-to-end RoBERTa fine-tuning notebook for binary misinformation classification
- BERT baseline notebook for benchmarking against the RoBERTa architecture
- Knowledge-graph experimentation notebook for grounding claims against structured facts
- Combined-model notebook that fuses transformer and knowledge-graph signals
- Cleaned, deduplicated training CSV (`UBC_project/cleaned_data_no_special_characters.csv`)
- Reference Flask serving script (`UBC_project/sample_code_test.txt`) demonstrating preprocessing and inference

## Architecture

The primary classifier is a RoBERTa-base transformer fine-tuned on a curated climate-claim corpus, with a parallel BERT baseline for benchmarking. Preprocessing covers URL/HTML stripping, punctuation and stopword removal, emoji filtering, spaCy lemmatisation, and spell correction. A separate knowledge-graph track investigates augmenting the language-model verdict with structured climate-fact lookups, and a final combination notebook fuses the two signals into a single classification.

## Tech Stack

- Python, TensorFlow / Keras, Hugging Face Transformers (RoBERTa, BERT)
- NLTK, spaCy, TextBlob for linguistic preprocessing
- Jupyter for experimentation
- Flask for the reference serving script

## Getting Started

### Prerequisites

- Python 3.8+
- Jupyter Notebook or JupyterLab
- TensorFlow, `transformers`, `nltk`, `spacy`, `textblob`, `flask`
- The pretrained RoBERTa weights and dataset linked below

### Installation

```bash
git clone https://github.com/PASCL-Lab/climate-misinformation.git
cd climate-misinformation
pip install tensorflow transformers flask nltk spacy textblob
python -m spacy download en_core_web_sm
```

### Running

#### Notebooks

```bash
cd UBC_project
jupyter notebook
# Open any of:
#   RoBerta_Model_Architecture.ipynb
#   Bert_testing.ipynb
#   Knowledge_graph_testing.ipynb
#   Combining_models.ipynb
#   Climate_change_misinformation_check.ipynb
```

#### Reference Flask server

Use `UBC_project/sample_code_test.txt` as the starting point for a local inference endpoint. After loading the trained RoBERTa weights linked below, save the file as `app.py` and run:

```bash
python app.py
```

### Pretrained Weights & Dataset

- RoBERTa model: https://drive.google.com/file/d/1VCT4m1XxsgNxf43g0yNUsLAU4pZRJjP_/view?usp=sharing
- Dataset: https://drive.google.com/file/d/1pFhEa_WwuPNb_la7Bj8GJJTbRwFq8NFO/view?usp=sharing

## Project Structure

```
UBC_project/
  RoBerta_Model_Architecture.ipynb            # RoBERTa fine-tuning pipeline
  Bert_testing.ipynb                          # BERT baseline
  Knowledge_graph_testing.ipynb               # KG-grounded experiments
  Combining_models.ipynb                      # Transformer + KG fusion
  Climate_change_misinformation_check.ipynb   # End-to-end demo notebook
  cleaned_data_no_special_characters.csv      # Preprocessed training corpus
  sample_code_test.txt                        # Reference Flask serving script
  README.md                                   # Pointers to model and dataset downloads
```

## License

This project is the intellectual property of **PASCL Lab**. All rights reserved.

Unauthorized copying, distribution, modification, or use of this codebase, in whole or in part, is strictly prohibited without prior written permission from PASCL Lab.

(c) 2026 PASCL Lab. All rights reserved.
