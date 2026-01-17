# Modeling Interiority in Fiction

Computational analysis of narrative interiority in late nineteenth- and early twentieth-century English-language fiction using supervised NLP models and large language models.

## Overview
Interiority—the representation of a character’s inner thoughts, feelings, and perceptions—is a core element of narrative fiction, yet it remains difficult to identify consistently using computational methods. This project investigates whether interiority can be detected automatically at the paragraph level and where current NLP models succeed or fail in capturing subtle forms of inner life.

We introduce a three-level annotation scheme (high, low, none) grounded in narratological theory and construct a manually annotated dataset of 600 passages drawn from 15 literary works published between 1890 and 1930. Using this dataset, we evaluate traditional classifiers, fine-tuned transformer models, and prompted large language models on the task of interiority classification.

## Key Contributions
- A theory-informed operationalization of narrative interiority based on narratology
- A manually annotated dataset of 600 literary paragraphs with graded interiority labels
- Analysis of inter-annotator agreement highlighting ambiguity in implicit interiority
- A comparative evaluation of baseline NLP models, fine-tuned transformers, and large language models
- Empirical evidence that xplicit interiority is learnable, while indirect forms (e.g. free indirect discourse) remain challenging

## Dataset
- **Texts:** 15 works of English-language fiction (1890–1930), spanning modernist, realist, and genre fiction
- **Unit of annotation:** Paragraphs (50–400 words)
- **Labels:**
  - `high`: Explicit access to a character’s inner thoughts, feelings, or perceptions
  - `low`: Indirect, ambiguous, or minimal interiority
  - `none`: Purely external narration or dialogue
- **Size:** 600 annotated paragraphs

Annotation was performed by three graduate-level annotators using shared guidelines. Final labels were assigned via majority vote, with discussion for unresolved cases.

## Models Evaluated
- **Baselines:** Logistic Regression, Naive Bayes (count & TF-IDF features)
- **Fine-tuned encoders:** DistilBERT, BERT-large, RoBERTa-base
- **Sequence-to-sequence models:** Flan-T5 (various sizes, fine-tuned and prompted)
- **Large language models:** GPT-family models and LLaMA models in zero-shot and few-shot settings

Evaluation was conducted using both paragraph-level random splits and book-level splits to test generalization to unseen texts.

## Results 
- Large language models achieved the strongest overall performance, with **LLaMA-3.3-70B (few-shot)** performing best on book-level splits.
- Fine-tuned encoder models (notably **RoBERTa-base**) performed competitively despite lower computational cost.
- Across all models, the **low interiority** category proved most difficult to predict, mirroring human disagreement.
- Explicit interiority and purely external narration were consistently easier to classify than indirect or implicit cases.

## Limitations
- Interiority is inherently interpretive and context-sensitive; paragraph-level annotation limits access to broader narrative context.
- Class imbalance and ambiguity particularly affect performance on low-interiority passages.
- Models were evaluated with limited hyperparameter tuning to prioritize cross-model comparison.

## Citation
If you use this work, please cite the accompanying report:

> Kurmanbekova, A., Chen, C., & Lin, M. (2025). *Can Machines Read Minds? Detecting Interiority in Narrative Texts*. University of California, Berkeley.

## Repository Structure

This repository contains a mix of data files, notebooks, and documentation used for annotation, modeling, and analysis.

### Data
Files related to dataset construction, sampling, and annotation.
- **`.ipynb`** — Jupyter notebooks for data sampling, preprocessing, and exploratory analysis  
- **`.csv`** — Annotated datasets and metadata (e.g. paragraph-level labels, book-level splits)

### Modeling
Notebooks and artifacts used for training and evaluating models.
- **`.ipynb`** — Jupyter notebooks for baseline models, fine-tuned transformer models, and prompted large language models (e.g. BERT, Flan-T5, LLaMA)
- **`.csv`** — Gold labels and intermediate evaluation files used during training and testing

### Documentation
- **`README.md`** — Project overview, methodology, and results summary
- **`.pdf`** — Full final report describing the dataset, annotation scheme, modeling experiments, and analysis
