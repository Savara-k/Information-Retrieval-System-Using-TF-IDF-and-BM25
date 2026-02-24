# Information-Retrieval-System-Using-TF-IDF-and-BM25

Design and Evaluation of a Full Information Retrieval System
Boolean Retrieval vs. TF-IDF vs. BM25 Ranking
An implementation and evaluation of a classical Information Retrieval (IR) system comparing Boolean retrieval, TF-IDF with cosine normalization, and the BM25 probabilistic ranking model.

---
## Executive Summary
This project implements a complete classical search engine pipeline to evaluate the effectiveness of different retrieval strategies on unstructured text.

Using a collection of 50 synthetic documents focused on infrastructure and transportation, we compare:

* Boolean Retrieval (exact matching)
* TF-IDF with cosine normalization
* BM25 probabilistic ranking
  
Results show that while Boolean retrieval provides strict precision, BM25 produces superior ranking quality by balancing term frequency with document length normalization.

---
## Research Objective
To analyze the strengths and limitations of classical Information Retrieval models and determine which approach produces the most effective ranking of relevant documents.

# Dataset
* 50 synthetic documents
* Topic domain: infrastructure and transportation
* High term overlap to simulate realistic search ambiguity

# Example recurring terms:
* government
* funding
* transportation
* infrastructure
* System Architecture

---
The project implements the classical IR pipeline:

1 — Text Preprocessing
A multi-stage normalization process:
Tokenization (regex-based)
Lowercasing
Stopword removal (NLTK)
Stemming (Porter Stemmer)
This reduces noise and standardizes vocabulary for indexing.

2 — Inverted Index Construction
An inverted index maps each term to:
Document IDs
Term frequency within each document
This enables fast O(1) lookup time for query terms and efficient retrieval.

---

## Retrieval Models Implemented

# Boolean Retrieval
* Set-based logic (AND, OR)
* Returns documents containing exact term matches
* High precision but no ranking capability
  
# TF-IDF with Cosine Normalization

Weights terms based on:
* Term Frequency (TF)
* Inverse Document Frequency (IDF)
Cosine normalization prevents longer documents from dominating results.

# BM25 (Best Matching 25)
A probabilistic ranking model that improves upon TF-IDF by incorporating:
* Term frequency saturation (k₁ parameter)
* Document length normalization (b parameter)
* BM25 better reflects real-world relevance scoring.

---
## Experimental Results
Ranking Comparison
Query: "government funding transportation"

Top-ranked documents:
Document	TF-IDF Score	BM25 Score
doc26.txt	0.4051	2.1957
doc43.txt	0.4051	2.1957
doc49.txt	0.4051	2.1957
doc1.txt	0.2025	1.5641

TF-IDF and BM25 shared 9 of the top 10 results but differed in ranking order due to length normalization differences.

## Visualization
Principal Component Analysis (PCA) was applied to the TF-IDF vector space.

Findings:
* Documents clustered by topical similarity
* Validated the vector representation of semantic meaning

---
## Evaluation Metrics

Ground truth relevant documents: doc1.txt, doc3.txt

  - Mean Average Precision (MAP): 0.1269
  - Mean Reciprocal Rank (MRR): 0.1
    
The low MRR indicates relevant documents were retrieved but not ranked first, highlighting sensitivity to exact term frequencies.

---
## Key Insights
* Boolean retrieval excels at strict filtering but lacks ranking
* TF-IDF provides reasonable ranking but struggles with length bias
* BM25 offers the most robust relevance scoring
* Classical models remain efficient and interpretable despite neural alternatives

---

## Conclusion
BM25 demonstrated superior ranking performance compared to TF-IDF by accounting for the non-linear relationship between term frequency and relevance.
The system highlights the effectiveness of classical IR techniques as the foundation of modern search engines.

---

## Future Work
* Query expansion techniques
* Semantic search using word embeddings
* Hybrid keyword + neural retrieval
* Evaluation on larger real-world datasets

---

## Technical Stack
* Python
* NLTK
* NumPy
* Scikit-learn
* Matplotlib

---

## What This Project Demonstrates
* Full IR system design
* Text preprocessing pipelines
* Index construction
* Ranking algorithm implementation
* Evaluation using IR metrics
* Understanding of search engine fundamentals
