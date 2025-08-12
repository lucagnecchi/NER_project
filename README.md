# Data Visualization and Text Mining Project

## Introduction

This project focuses on **Named Entity Extraction** using the **AnEM corpus**.  
The goal is to associate each word in the corpus with the correct **anatomical entity tag**.

The **AnEM corpus**, created by the **NaCTeM (National Center for Text Mining)**, contains over **90,000 words** from **500 biomedical scientific documents**.

---

## Data

The corpus is stored in **IOB2 format**, a common tagging format for Named Entity Recognition (NER).  

**IOB2 tags:**
- **B-**: Beginning of a chunk
- **I-**: Inside a chunk
- **O**: Outside of any chunk

**Dataset columns:**
- **word**: The individual token/word
- **start**: Beginning character position of the word
- **end**: Ending character position of the word
- **ner_tag**: Classification label in IOB2 format

**Labels used:**
| Label |
| --- |
| Anatomical_system |
| Cell |
| Cellular_component |
| Developing_anatomical_structure |
| Immaterial_anatomical_entity |
| Multi-tissue_structure |
| Organ |
| Organism_subdivision |
| Organism_substance |
| Pathological_formation |
| Tissue |

---

## Models

Three different models for NER were implemented: **Feed Forward**, **BiLSTM**, and **BERT**.

### 1. Feed Forward Neural Network
A basic architecture where information flows in one direction through layers.

**Architecture:**
- Embedding layer to convert words into vectors
- Dense hidden layer with ReLU activation
- Dense output layer (23 units) with SoftMax activation

**Key Results:**
- **Training Accuracy**: 0.9989
- **Testing Accuracy**: 0.9978

---

### 2. BiLSTM
A **Bidirectional Long Short-Term Memory** network processes sequences in both forward and backward directions, capturing context from past and future words.

**Architecture:**
- Embedding layer (optionally using pre-trained **GloVe** embeddings)
- Dropout layer for regularization
- Bidirectional LSTM layer
- Dense output layer with SoftMax activation

**Key Results (Test Set Weighted Average):**
- **Precision**: 0.506
- **Recall**: 0.482
- **F1-score**: 0.487

---

### 3. BERT
**BERT (Bidirectional Encoder Representations from Transformers)** is a transformer-based model that captures deep bidirectional context, leveraging attention mechanisms and positional encoding.

**Key Results (Test Set Weighted Average):**
- **Precision**: 0.634
- **Recall**: 0.671
- **F1-score**: 0.652

---

## Conclusion

Since our goal was **Named Entity Recognition**, we tested three models:

1. **Feed Forward** — simplest model, consisting of input, hidden, and output layers.
2. **BiLSTM** — introduces bidirectionality to improve context understanding.
3. **BERT** — leverages transfer learning and transformer-based attention.

Given the class imbalance in the dataset, **weighted averages** give a better picture of model performance.

**Weighted average results:**

| Model       | Precision | Recall | F1-score |
|-------------|-----------|--------|----------|
| Feed Forward| 0.413     | 0.369  | 0.386    |
| BiLSTM      | 0.506     | 0.482  | 0.487    |
| BERT        | 0.634     | 0.671  | 0.652    |

**Observations:**
- The Feed Forward and BiLSTM models have high accuracy mainly due to the large proportion of "O" tags.
- BERT achieves significantly better weighted metrics, with **test set accuracy ~93%**.
- Performance increases as the complexity of the model increases.

---
