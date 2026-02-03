## Protein Function Prediction
This project focuses on predicting protein functions using machine learning models that assign Gene Ontology (GO) annotations directly from amino acid sequences.

Gene Ontology describes protein functions across three complementary biological aspects:

Molecular Function (MF) – The biochemical activity performed by a protein

Biological Process (BP) – The biological processes in which the protein participates

Cellular Component (CC) – The cellular location where the protein operates

Protein function prediction is formulated as a multi-label classification task, since a single protein can perform multiple functions and contribute to multiple biological processes simultaneously. The problem is particularly challenging due to:

The hierarchical structure of the Gene Ontology

The presence of incomplete and noisy biological annotations

The complexity of protein interactions and functional diversity

 # CAFA Challenge Context

This work is developed within the CAFA (Critical Assessment of Functional Annotation) challenge. The goal of CAFA is to evaluate computational methods that predict protein functions using experimentally validated annotations.

Models are trained on annotated protein datasets and evaluated using weighted F1-score metrics, which prioritize biologically informative predictions and account for the hierarchical nature of GO terms.

