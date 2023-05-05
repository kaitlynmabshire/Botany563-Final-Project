# Botany563-Final-Project

This repository is for the course final project for Botany563.

# Description of Dataset

Distal-less (dlx) and extradenticle (exd) are expressed in cephalopod cephalic tentacles (i.e., eye/olfactory stalks; limbs). However, much is unknown about dlx and exd in other mollusk groups. Examining the evolution of these genes within mollusks will help address fundamental questions underlying the evolution of novel phenotypes, as well as the consequences of gene duplication and loss.

# Steps

1) Potential ortholog sequences where found using BLAST across available mollusk genomes, with an annelid and arthropod outgroup. (done)
2) Assemble *Cornu aspersum* transcriptome (received 02/13/2023) and find dlx and exd. (done)
3) Run multiple sequence alignment using T-Coffee and Muscle. (done)
4) Create neighbor-joining trees. (done)
5) Create parsimony trees.
6) Create maximum likelihood trees. (done)
7) Create Bayesian trees. (done)
8) Create Coalescent trees. (done)
9) Create Co-estimation trees. (done)

# Quality Control

Dataset was produced from NCBI Mollusca sequences, with an Arthropoda and Annedlida outgroup. After running multiple sequence alignment, taxa with poor alignment were removed from the dataset.

*Cornu aspersum* sequences were assembled using Trinity-v2.15.0