# Neighbor-Joining Tress 

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

# Parsimony Tree

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

*Note: Still recieving fatal error when running "parsimony(tre.ini, AA2)"