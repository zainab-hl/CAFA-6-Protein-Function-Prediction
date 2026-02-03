## Protein Function Prediction
This project focuses on predicting protein functions using machine learning models that assign Gene Ontology (GO) annotations directly from amino acid sequences.

Gene Ontology describes protein functions across three complementary biological aspects:

1- Molecular Function (MF) – The biochemical activity performed by a protein

2- Biological Process (BP) – The biological processes in which the protein participates

3- Cellular Component (CC) – The cellular location where the protein operates

Protein function prediction is formulated as a multi-label classification task, since a single protein can perform multiple functions and contribute to multiple biological processes simultaneously. The problem is particularly challenging due to:
- The hierarchical structure of the Gene Ontology
- The presence of incomplete and noisy biological annotations
- The complexity of protein interactions and functional diversity

 ### CAFA Challenge Context

This work is developed within the CAFA (Critical Assessment of Functional Annotation) challenge. The goal of CAFA is to evaluate computational methods that predict protein functions using experimentally validated annotations.

Models are trained on annotated protein datasets and evaluated using weighted F1-score metrics, which prioritize biologically informative predictions and account for the hierarchical nature of GO terms.

### Approach:

1- Encode protein sequences using ESM2 transformer
2- Apply mean pooling to obtain sequence-level embeddings
3- Feed embeddings into separate linear classifiers for MF, BP, and CC
4- Train each head for multi-label GO term prediction

#### Post-Processing: Hierarchical Consistency
Objective: Enforce the Hard Propagation Rule:

𝑃(parent)=max(𝑃(parent),𝑃(child))  why? 
because, if a model predicts a specific function (Child), it must logically predict the broader function (Parent) with equal or higher probability.

1- Build GO DAG: Parse go-basic.obo and precompute ancestors for all GO terms.
2- Combine previous ESM2 model predictions with GOA annotations.
3- Apply IA and Taxonomy Boosts: Optionally adjust scores using information accretion weights and protein taxonomy data.
4- Hierarchical Propagation:

   - Positive propagation: ensure parent scores ≥ child scores.
   - Negative propagation: constrain child scores ≤ parent scores.

#### Training Note:

- Used only half of the training dataset.
- Trained each GO aspect for 10 epochs to reduce runtime while testing the approach.
- Achieved a final CAFA6 weighted F1 score of 0.366.




