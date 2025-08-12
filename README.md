# Edit the markdown cell with cell_id: new_markdown_cell
# Replace the content of the markdown cell with the following:
# # Data Visualization and Text Mining Project
#
# ## Introduction
#
# This project focuses on performing Named Entity Extraction on the **AnEM corpus**. The goal is to associate each word in the corpus with the correct anatomical entity tag. The **AnEM corpus**, created by the NaCTeM (National Center for Text Mining), contains over 90,000 words from 500 documents, representative of biomedical scientific literature.
#
# ## Data
#
# The corpus is stored in IOB2 format, a common tagging format for performing the Named Entity Recognition task. This format uses 'B-' for the beginning of a chunk, 'I-' for tokens inside a chunk, and 'O' for tokens outside of any chunk. The data is organized with the following columns:
# - **word**: The individual token/word.
# - **start**: The beginning character position of the word.
# - **end**: The ending character position of the word.
# - **ner_tag**: The classification label in IOB2 format.
#
# The labels used in this corpus are:
#
# | Labels |
# | --- |
# | Anatomical\_system |
# | Cell |
# | Cellular\_component |
# | Developing\_anatomical\_structure |
# | Immaterial\_anatomical\_entity |
# | Multi\-tissue\_structure |
# | Organ |
# | Organism\_subdivision |
# | Organism\_substance |
# | Pathological\_formation |
# | Tissue |
#
# ## Models
#
# This project implements three different models for Named Entity Recognition: Feed Forward, BiLSTM, and BERT.
#
# ### Feed Forward
#
# A Feed Forward Neural Network is a basic architecture where information flows in one direction through layers. This model consists of:
# - An **Embedding layer** to convert words into vectors.
# - A **Dense hidden layer** with ReLU activation.
# - A **Dense output layer** with 23 units and SoftMax activation for classification.
#
# **Key Results:**
# - Training Accuracy: 0.9989
# - Testing Accuracy: 0.9978
#
# ### BiLSTM
#
# A Bidirectional Long Short-Term Memory (BiLSTM) network utilizes two LSTMs to process sequences in both forward and backward directions, capturing context from both past and future words. This model incorporates:
# - An **Embedding layer**, potentially using pre-trained **GloVe embeddings**.
# - A **Dropout layer** for regularization.
# - A **Bidirectional LSTM layer**.
# - A **Dense output layer** with SoftMax activation.
#
# **Key Results (Test Set Weighted Average):**
# - Precision: 0.506
# - Recall: 0.482
# - F1-score: 0.487
#
# ### BERT
#
# BERT (Bidirectional Encoder Representations from Transformers) is a powerful, pre-trained transformer-based model that captures deep bidirectional context. It leverages the transformer architecture's attention mechanisms and positional encoding, not relying on traditional RNNs.
#
# **Key Results (Test Set Weighted Average):**
# - Precision: 0.634
# - Recall: 0.671
# - F1-score: 0.652
#
# ## Conclusion
#
# Due to the fact that our aim was the Named Entity Recognition, we have implemented three models: the feed forward, the BiLSTM and the BERT. The first model is the simplest one: made up of input layer, output layer and some hidden layers. The second allow also bidirectionality in order to improve the context information and the third, in addition, take advantage from transfer learning.
# If we want to interpret the results in a more precise way we should consider that the classes are unbalanced, so we should look at the wheighted avarage of the output. The results follow the expectation: a more complex model obtain better results, indeed the metrics obtained in the test set are:
#
# in the feed forward
#
# * precision: 0.413
# * recall: 0.369
# * f1-score: 0.386
#
# In the BiLSTM
#
# * precision: 0.506
# * recall: 0.482
# * f1-score: 0.487
#
# and in the BERT:
#
# * precision: 0.634
# * recall: 0.671
# * f1-score: 0.652
#
# If we want to inspect in a more precise way, we can see that the accuracy in the test set computed through the feed forward is near to one, probably thank to the large number of "O" tags.
# The same can be said for the BiLSTM, for which the values are little smaller but still near to one. In addition, the accuracy for the Bert model is close to the 93%.
