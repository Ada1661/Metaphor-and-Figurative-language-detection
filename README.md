# Metaphor and Figurative Language Detection

**Authors:** Andrada Bejenaru & Iulia Pincu 

## Overview
A simple pipeline that takes a sentence containing a metaphor and chooses the correct literal interpretation from two candidates. Uses TF-IDF features and a logistic regression classifier.

## Dataset
- **Fig-QA (Hugging Face)**  
- Each entry has:
  - A sentence with a metaphor
  - Two possible literal endings (ending1, ending2)
  - A label (0 or 1) indicating which ending is correct

## Preprocessing
1. For each row, create two examples:
   - (metaphor + ending1) with label = 1 if label == 0, else 0
   - (metaphor + ending2) with label = 1 if label == 1, else 0
2. Vectorize using TF-IDF:
   - Word n-grams (unigrams + bigrams)
   - Char-level n-grams (length 3–5)
3. Combine both into a single feature set.

## Model
- **Classifier:** Logistic Regression
- **Pipeline:** TF-IDF → Logistic Regression
- Hyperparameter search over C, n-gram ranges, etc.
