# General Commands
### Connecting Github to Git on personal laptop
#### Cloning Directory
```
Pwd
Cd desktop/Botany563
Git clone https://github.com/kaitlynmabshire/Botany563.git
```
#### Adding Upstream Directory and Pushing
```
Git remote add upstream https://github.com/kaitlynmabshire/Botany563.git
Git remote -v
Git add .
git commit -m "note"
git push
```

# Finding Sequences in Transcriptome

## NCBI BLAST+
-NCBI BLAST+ was downloaded from https://www.ncbi.nlm.nih.gov/books/NBK52640/

-Sequences found from the NCBI database were used as query and searched in assembled transcriptome.

### Making local database

#### Input:
```
./makeblastdb -in cornu_aspersum.fasta -out cornu_aspersum_db -dbtype nucl -parse_seqid
```

### Running query

#### Input:
```
./tblastn -query <query_sequence_file.fasta> -out cornu_aspersum_db -out <file.txt>
```

Sequences found with the lowest E value (less than E^-20) were selected compared to ortholog sequences using ORFfinder on NCBI.

# Multiple Sequence Alignment

## Ran T-Coffee:
#### Input:
```
cd botany563/botany563-final-project
t_coffee dlx_protein.fasta
```

#### Output Results:
```
OUTPUT RESULTS
	#### File Type= GUIDE_TREE      Format= newick          Name= dlx_protein.dnd
	#### File Type= MSA             Format= aln             Name= dlx_protein.aln
	#### File Type= MSA             Format= html            Name= dlx_protein.html

# Command Line: t_coffee dlx_protein.fasta  [PROGRAM:T-COFFEE]
# T-COFFEE Memory Usage: Current= 37.306 Mb, Max= 40.739 Mb
# Results Produced with T-COFFEE Version_13.45.0.4846264 (Version_13.45.0.4846264)
# T-COFFEE is available from http://www.tcoffee.org
# Register on: https://groups.google.com/group/tcoffee/
```
## Ran Muscle:
#### Input:
```
~/Dropbox/software/muscle3.8.31_i86darwin64 -in dlx_protein.fasta -out muscle_aligned_dlx_protein.fasta
```

#### Output:
```
MUSCLE v3.8.31 by Robert C. Edgar

http://www.drive5.com/muscle
This software is donated to the public domain.
Please cite: Edgar, R.C. Nucleic Acids Res 32(5), 1792-97.

dlx_protein 17 seqs, max length 333, avg  length 250
00:00:00      1 MB(0%)  Iter   1  100.00%  K-mer dist pass 1
00:00:00      1 MB(0%)  Iter   1  100.00%  K-mer dist pass 2
00:00:00      5 MB(0%)  Iter   1  100.00%  Align node       
00:00:00      5 MB(0%)  Iter   1  100.00%  Root alignment
00:00:00      6 MB(0%)  Iter   2  100.00%  Refine tree   
00:00:00      6 MB(0%)  Iter   2  100.00%  Root alignment
00:00:00      6 MB(0%)  Iter   2  100.00%  Root alignment
00:00:00      6 MB(0%)  Iter   3  100.00%  Refine biparts
00:00:00      6 MB(0%)  Iter   4  100.00%  Refine biparts
00:00:00      6 MB(0%)  Iter   5  100.00%  Refine biparts
00:00:00      6 MB(0%)  Iter   5  100.00%  Refine biparts
```

# Neighbor-Joining Tree
#### dlx NJ tree
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
#### exd NJ tree
```
#load packages
library(ape)
library(adegenet)
library(phangorn)

#load sample data
setwd("~/Desktop/Botany563/Botany563-Final-Project/multiple_seq_align/t-coffee")
AA <- fasta2DNAbin(file="exd_protein.fasta")

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
#Maximum Likelihood
## RAxML-NG
### Description
Randomized Axelerated Maximum Likelihood (RAxML) is a phylogenetic analysis method of large datasets under maximum likelihood. It uses Subtree Pruning Regrafting (SPR) moves to quickly navigate to the best known ML tree.
### Strengths
Can be used on large datasets and quickly produces high scoring trees; supports DNA, protein, binary, multi-state morphological, and RNA secondary data; offers standard statistical significant test and options to compute Robinson-Foulds distances
### Weaknesses
Has higher variance of trees and can be less stable than IQ-Tree; may need more iterations for phylogeny building if alignments already have strong phylogentic signals
### Assumptions
1) mutation process is the same at every branch of the tree 2) all sites evolve independently of each other 3) all sites evolve the same

#### dlx tree
```
~/Dropbox/software/raxml-ng -msa dlx_protein.fasta -model VT+I+I+R2
```
#### Output Results:
```
Final LogLikelihood: -8514.276652

AIC score: 17108.553305 / AICc score: 17111.913960 / BIC score: 17305.537800
Free parameters (model + branch lengths): 40

Best ML tree saved to: /Users/kaitlynabshire/Desktop/Botany563/Botany563-Final-Project/multiple_seq_align/t-coffee/dlx_protein.fasta.raxml.bestTree
All ML trees saved to: /Users/kaitlynabshire/Desktop/Botany563/Botany563-Final-Project/multiple_seq_align/t-coffee/dlx_protein.fasta.raxml.mlTrees
Optimized model saved to: /Users/kaitlynabshire/Desktop/Botany563/Botany563-Final-Project/multiple_seq_align/t-coffee/dlx_protein.fasta.raxml.bestModel

Execution log saved to: /Users/kaitlynabshire/Desktop/Botany563/Botany563-Final-Project/multiple_seq_align/t-coffee/dlx_protein.fasta.raxml.log

Analysis started: 20-Mar-2023 10:25:30 / finished: 20-Mar-2023 10:29:27

Elapsed time: 237.832 seconds
```
#### exd tree
```
~/Dropbox/software/raxml-ng -msa exd_protein.fasta -model VT+I+I+R2
```
#### Output Results:
```
Final LogLikelihood: -12274.980149

AIC score: 24633.960298 / AICc score: 24636.496815 / BIC score: 24856.181239
Free parameters (model + branch lengths): 42

Best ML tree saved to: /Users/kaitlynabshire/Desktop/Botany563/Botany563-Final-Project/multiple_seq_align/t-coffee/exd_protein.fasta.raxml.bestTree
All ML trees saved to: /Users/kaitlynabshire/Desktop/Botany563/Botany563-Final-Project/multiple_seq_align/t-coffee/exd_protein.fasta.raxml.mlTrees
Optimized model saved to: /Users/kaitlynabshire/Desktop/Botany563/Botany563-Final-Project/multiple_seq_align/t-coffee/exd_protein.fasta.raxml.bestModel

Execution log saved to: /Users/kaitlynabshire/Desktop/Botany563/Botany563-Final-Project/multiple_seq_align/t-coffee/exd_protein.fasta.raxml.log

Analysis started: 20-Mar-2023 10:36:03 / finished: 20-Mar-2023 10:41:40

Elapsed time: 337.394 seconds
```

## iqtree2
#### dlx 
```
~/Dropbox/software/iqtree-2.2.0-MacOSX/bin/iqtree2 -s dlx_protein.fasta
```
#### exd 
```
~/Dropbox/software/iqtree-2.2.0-MacOSX/bin/iqtree2 -s exd_protein.fasta
```
#### output:
```
Akaike Information Criterion:           VT+F+I+I+R2
Corrected Akaike Information Criterion: VT+F+I+I+R2
Bayesian Information Criterion:         VT+I+I+R2
Best-fit model: VT+I+I+R2 chosen according to BIC
--------------------------------------------------------------------
|                    FINALIZING TREE SEARCH                        |
--------------------------------------------------------------------
Performs final model parameters optimization
Estimate model parameters (epsilon = 0.010)
1. Initial log-likelihood: -12068.747
Optimal log-likelihood: -12068.747
Proportion of invariable sites: 0.011
Site proportion and rates:  (0.752,0.267) (0.237,3.373)
Parameters optimization took 1 rounds (0.079 sec)
BEST SCORE FOUND : -12068.747
Total tree length: 21.735

Total number of iterations: 219
CPU time used for tree search: 69.814 sec (0h:1m:9s)
Wall-clock time used for tree search: 71.654 sec (0h:1m:11s)
Total CPU time used: 70.228 sec (0h:1m:10s)
Total wall-clock time used: 71.974 sec (0h:1m:11s)

Analysis results written to: 
  IQ-TREE report:                exd_protein.fasta.iqtree
  Maximum-likelihood tree:       exd_protein.fasta.treefile
  Likelihood distances:          exd_protein.fasta.mldist
  Screen log file:               exd_protein.fasta.log

ALISIM COMMAND
--------------
--alisim simulated_MSA -t exd_protein.fasta.treefile -m "VT+I{0.0113759}+R2{0.751691,0.267149,0.236933,3.37305}" --length 1467
```