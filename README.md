# Botany563-Final-Project

This repository is for the course final project for Botany563.

# Description of Dataset

Distal-less (Dlx) are expressed in cephalopod cephalic tentacles (i.e., eye/olfactory stalks; limbs). However, much is unknown about Dlx in other mollusk groups. Examining the evolution of this gene within mollusks will help address fundamental questions underlying the evolution of novel phenotypes, as well as the consequences of gene duplication and loss.

# Steps

1) Potential ortholog sequences will be found using reciprocal BLAST across available mollusk genomes, with an annelid outgroup. (done)
2) Assemble *Cornu aspersum* transcriptome (received 02/13/2023) and find Dlx. (done)
3) Run multiple sequence alignment using T-Coffee and Muscle. (done)
4) Create neighbor-joining trees. (done)
5) Create parsimony trees.
6) Create maximum likelihood trees.
7) Create Bayesian trees.
8) Create Coalescent trees.

# Quality Control

Dataset was produced from NCBI Mollusc sequences, with an arthropod and annedlid outgroup. After running multiple sequence alignment, taxa with poor alignment were removed from the dataset.

*Cornu aspersum* sequences were assembled using Trinity-v2.15.0