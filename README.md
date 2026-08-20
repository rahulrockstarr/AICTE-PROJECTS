# AICTE AI/ML Projects

This repository contains two AI/ML projects completed as part of the **AICTE Internship**, focusing on Natural Language Processing (NLP), Machine Learning, and Deep Learning.

## Projects

| Project                   | Area                      | Approach                             |
| ------------------------- | ------------------------- | ------------------------------------ |
| 🎬 Movie Spoiler Detector | NLP / Text Classification | BERT-based Binary Classification     |
| 📰 Text Summarizer        | NLP / Text Summarization  | Graph-based Extractive Summarization |

---

# 1. 🎬 Movie Spoiler Detector

## Overview

Movie and TV reviews can contain important plot revelations that may negatively affect the viewing experience. This project focuses on automatically identifying whether a movie review contains a **spoiler**.

The model performs binary classification:

* `0` → Non-Spoiler
* `1` → Spoiler

The project uses the IMDb Spoiler dataset containing **573,913 reviews**, of which **150,924 are spoiler reviews**. The dataset also contains information about users and movies.

## Dataset

The dataset consists of two major files:

### IMDb Movie Details

Contains:

* Movie ID
* Plot Summary
* Duration
* Genre
* Rating
* Release Date
* Plot Synopsis

### IMDb Reviews

Contains:

* Review Date
* Movie ID
* User ID
* Spoiler Label
* Review Text
* Rating
* Review Summary

The dataset contains 263,407 users and 1,572 movies.

## Exploratory Data Analysis

The analysis included:

* Missing-value analysis
* Spoiler vs. non-spoiler distribution
* Review-length analysis
* Genre distribution
* Spoiler trends over time
* Review-length distribution

No missing values were found in the analyzed columns. The dataset was also found to be imbalanced, with non-spoiler reviews forming the majority class.

## Data Preprocessing

The review text was processed through the following pipeline:

1. Remove URLs
2. Remove email addresses
3. Remove non-word characters and digits
4. Convert text to lowercase
5. Normalize whitespace
6. Tokenize the text
7. Remove stopwords
8. Apply Porter stemming
9. Reconstruct the cleaned text

These steps were used to prepare the reviews for the BERT-based model.

## Handling Class Imbalance

Two approaches were explored:

### Downsampling

The majority non-spoiler class was downsampled to create a more balanced training dataset.

The report describes a balanced training configuration with:

* Non-Spoiler: 10,000
* Spoiler: 10,000

### SMOTE

SMOTE was also explored to generate synthetic samples for the minority class rather than simply duplicating existing samples.

## Model — BERT

The project uses **BERT (Bidirectional Encoder Representations from Transformers)** for spoiler classification.

The architecture uses:

* Transformer encoder
* Self-attention
* Multi-head attention
* Layer normalization
* Feedforward networks
* Residual connections

The BERT model is fine-tuned by adding a classification head for binary spoiler detection.

### Training Pipeline

```text
Raw Reviews
     ↓
Data Cleaning
     ↓
Class Balancing
     ↓
BERT Tokenization
     ↓
Train / Validation Split
     ↓
BERT Classification Model
     ↓
Fine-tuning
     ↓
Evaluation
```

The training implementation uses a custom `SpoilerDataset` class and training/evaluation functions for PyTorch-based model training.

## Technologies

* Python
* Natural Language Processing
* BERT
* PyTorch
* Machine Learning
* Transformers
* Pandas
* Scikit-learn

---

# 2. 📰 Text Summarizer

## Overview

This project implements an **extractive text summarization system** that identifies and selects the most important sentences from an article to produce a shorter summary.

The project explores several approaches to text summarization before focusing on a **graph-based approach**.

## Dataset

The project uses a BBC news dataset containing:

* **417 political news articles**
* Articles from 2004–2005
* Five reference summaries for each article

The dataset contains articles across categories such as:

* Politics
* Sport
* Technology
* Entertainment
* Business

## Extractive vs. Abstractive Summarization

Two broad approaches were studied:

### Extractive Summarization

Selects important sentences directly from the original document.

### Abstractive Summarization

Generates a new summary based on the meaning and ideas in the original document.

This project focuses on **extractive summarization**.

## Graph-Based Summarization

The core approach uses:

* Sentence tokenization
* Sentence vectorization
* Cosine similarity
* Similarity matrix
* Graph construction
* PageRank/TextRank
* Sentence ranking

Each sentence is represented as a node in a graph.

The similarity between two sentences determines the edge between them.

```text
                 Sentence 1
                /          \
               /            \
        Sentence 2 -------- Sentence 3
               \              /
                \            /
                 Sentence 4
```

Sentences with higher importance scores are selected for the final summary.

## TextRank Pipeline

```text
Article
   ↓
Sentence Tokenization
   ↓
Sentence Vectors
   ↓
Cosine Similarity
   ↓
Similarity Matrix
   ↓
Graph Construction
   ↓
PageRank / TextRank
   ↓
Sentence Ranking
   ↓
Top N Sentences
   ↓
Final Summary
```

The implementation uses **NetworkX** to construct the graph and PageRank to rank sentences.

## Cosine Similarity

For two sentence vectors `A` and `B`:

```text
              A · B
Similarity = -------
             ||A|| ||B||
```

Higher cosine similarity indicates that two sentences are more semantically similar.

## Evaluation

Two evaluation approaches were explored:

### BLEU Score

The reported BLEU score was:

```text
0.3105109744864834
```

The project notes that BLEU is less suitable for this summarization task because it primarily evaluates n-gram overlap and may not adequately capture semantic equivalence.

### Similarity Score

The reported similarity score was:

```text
0.5627625286579132
```

The project considered similarity-based evaluation more appropriate for this use case.

## Technologies

* Python
* Natural Language Processing
* NLTK
* NetworkX
* Cosine Similarity
* PageRank / TextRank
* Machine Learning

---

# Repository Structure

```text
AICTE-Projects/
│
├── Movie-Spoiler-Detector/
│   ├── notebooks/
│   ├── src/
│   ├── data/
│   └── README.md
│
├── Text-Summarizer/
│   ├── notebooks/
│   ├── src/
│   ├── data/
│   └── README.md
│
└── README.md
```

> The exact folder structure may be modified according to the files included in this repository.

---

# Key Concepts Covered

Through these projects, the following concepts were explored:

* Natural Language Processing
* Text preprocessing
* Tokenization
* Text classification
* Class imbalance
* Downsampling
* SMOTE
* BERT
* Transformer architecture
* Self-attention
* Fine-tuning
* Extractive summarization
* Cosine similarity
* Graph-based algorithms
* PageRank
* TextRank
* Model training and evaluation

---

# Internship

**AICTE Internship — May/June 2025**

**Author:** Rahul Shah
**Institution:** IIT Delhi

---

## Projects Summary

### 🎬 Movie Spoiler Detector

A BERT-based NLP classification system designed to identify spoilers in movie reviews.

### 📰 Text Summarizer

A graph-based extractive summarization system that uses sentence similarity and PageRank/TextRank to select important sentences from news articles.

---

## Author

**Rahul Shah**
IIT Delhi

[GitHub](https://github.com/) • [LinkedIn](https://www.linkedin.com/)

---

## Acknowledgements

These projects were completed as part of the **AICTE Internship** and involved practical exploration of Natural Language Processing, Machine Learning, and Deep Learning techniques.
