```markdown
# Text Clustering Analysis

This notebook performs text clustering analysis on a given dataset. It covers data loading, text preprocessing, feature extraction using various techniques, clustering with K-means and Agglomerative Clustering, and evaluation of the clustering results.

## Table of Contents

1. [Setup and Library Imports](#setup-and-library-imports)
2. [Data Loading](#data-loading)
3. [Text Processing](#text-processing)
4. [Feature Extraction](#feature-extraction)
5. [Clustering](#clustering)
6. [Evaluation](#evaluation)
7. [Experiments and Results](#experiments-and-results)

## 1. Setup and Library Imports

This section imports all necessary libraries for data manipulation, visualization, text processing, and clustering algorithms.

## 2. Data Loading

- The notebook loads a dataset from a specified `DATA_PATH`.
- It extracts the text corpus and labels from the CSV file.
- Labels are then encoded using `LabelEncoder`.

## 3. Text Processing

Two main preprocessing variants are implemented:

- `basic_preprocess`: Converts text to lowercase, removes non-alphabetic characters (preserving Kazakh alphabet), punctuation, and numbers.
- `SW_preprocess`: Applies `basic_preprocess` and then removes stop words loaded from `stop_words_kzt.txt`.

## 4. Feature Extraction

Text data is converted into numerical representations using:

- `make_tf_matrix`: Creates Term Frequency (TF) matrix using `CountVectorizer`.
- `make_tf_norm_matrix`: Normalizes the TF matrix.
- `make_tfidf_matrix`: Creates Term Frequency-Inverse Document Frequency (TF-IDF) matrix using `TfidfVectorizer`.

## 5. Clustering

Two clustering algorithms are used:

- `cluster_kmeans`: K-means clustering.
- `clusters_hierarchical`: Agglomerative Hierarchical Clustering.

## 6. Evaluation

Clustering performance is evaluated using:

- **Adjusted Rand Index (ARI)**
- **Normalized Mutual Information (NMI)**

## 7. Experiments and Results

The `run_experiments` function orchestrates the entire process, testing different combinations of preprocessing methods, text representations, and clustering algorithms.

The results are compiled into a DataFrame, showing the ARI and NMI scores for each configuration. The best-performing configuration is typically highlighted.

### Current Results Summary:

Based on the last run, the following table summarizes the clustering performance:

| Preprocessing | Representation | Algorithm     | ARI      | NMI      |
| ------------- | -------------- | ------------- | -------- | -------- |
| basic         | TFIDF          | Agglomerative | 0.202028 | 0.265037 |
| SW            | TFIDF          | Agglomerative | 0.202028 | 0.265037 |
| basic         | TFIDF          | K-means       | 0.125140 | 0.200640 |
| SW            | TFIDF          | K-means       | 0.125140 | 0.200640 |
| ...           | ...            | ...           | ...      | ...      |

**Observations:**

- `TFIDF` representation combined with `Agglomerative` clustering consistently yields the highest ARI and NMI scores, regardless of the preprocessing method (basic or with stop words).
- The `K-means` algorithm also performs better with `TFIDF` compared to `TF` or `TF_Norm`.
- Removing stop words (`SW` preprocessing) does not significantly change the performance for the best configurations in this particular dataset.

### Plot

The results are visualized using a `catplot` showing the ARI and NMI scores across different preprocessing, representation, and algorithm combinations.
```
