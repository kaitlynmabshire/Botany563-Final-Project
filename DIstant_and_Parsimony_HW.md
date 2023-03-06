# Neighbor-Joining Trees 
### Description
Uses a distance matrix to construct a tree by determining which leaves/branches are neighbors. NJ trees aim to show the minimum amount of evolution to explain differences among sequences.
### Strengths
Topologically accurate and fast
### Weaknesses
Data reduction occurs and only one possible tree is produced; rely on an evolution model
### Assumptions


```
#load packages
library(ape)
library(adegenet)
library(phangorn)

#load sample data
setwd("~/Desktop/Botany563/Botany563-Final-Project/multiple_seq_align/t-coffee")
AA <- fasta2DNAbin(file="dlx_protein.fasta")

#compute genetic distances
A1 <- dist.aa(AA)

#Get NJ trees
tre1 <- nj(A1)

#add ladderize funcation
tre1 <- ladderize(tre1)

#plot tree
plot(tre1, cex=.6)
title("A simple NJ tree")

#root tree
rootedtree <- root(tre1, outgroup = "Drosophila_melanogaster", resolve.root = "true")
is.rooted(rootedtree)
plot(rootedtree, type = "tidy", edge.width = 2)
```
# Parsimony Tree
### Description
Uses aligned character-based data (4 nucleotides or 20 amino acids) and seeks the trees that minimizes the amount of evolutionary change (i.e., lowest cost of change) that explains the data
### Strengths
Most effective when rates of evolution is slow and equal among branches
### Weaknesses
May create errors for trees where evolution rates are not equal (long-branch attraction; Felsenstein zone)
### Assumptions
Independence among characters

```
setwd("~/Desktop/Botany563/Botany563-Final-Project/multiple_seq_align/t-coffee")
AA1 <- fasta2DNAbin(file="dlx_protein.fasta")
AA2 <- as.phyDat(AA1)

#compute genetic distances
A1 <- dist.aa(AA)

#Get NJ trees
tre.ini <- nj(A1)
tre.ini

#Get Parsimony tree
parsimony(tre.ini, AA2)

> tre.pars <- optim.parsimony(tre.ini, AA2)
Final p-score 420 after  2 nni operations

plot(tre.pars, cex=0.6)
```
*Note: Still recieving fatal error when running "parsimony(tre.ini, AA2)"