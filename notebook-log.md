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

## T-Coffee:

#### Downloading T-Coffee
Downloaded T-COFFEE_distribution_Version_13.45.0.4846264.tar.gz from http://www.tcoffee.org/Packages/Stable/Latest/ (Downloaded on 06/29/2021). T-Coffee can be found in dekstop/software/T-COFFEE_distribution_Version_13.45.61.3c310a9
```
mv ~/Downloads/T-COFFEE* ~/Desktop/ncbi_dataset
# cd ncbi_dataset/T-COFFEE*
# ./install all
```
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
## Muscle:
#### Downloading Muscle
Downloaded Muscle from https://drive5.com/muscle/downloads_v3.htm (muscle3.8.31_i86darwin64.tar.gz) (02/2023). Muscle can be found in desktop/software/muscle3.8.31_i86darwin64
```
tar -zxvf muscle3.8.31_i86darwin64.tar.gz
```
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

#### Downloading RAxML
Downloaded RAxML from https://github.com/amkozlov/raxml-ng (06/29/2021). RAxML can be found in desktop/software/raxml-ng_v1
```
mv ~/Downloads/raxml* ~/Desktop/ncbi_dataset
cd ncbi_dataset/raxml*

./raxml-ng -v
```
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
#### Downloading iqtree2
Downloaded iqtree2 from http://www.iqtree.org/#download (03/2023). iqTree2 can be found in desktop/software/iqtree01.6.12-MacOSX

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

# Bayesian Inference
## MrBayes
### Downloading MrBayes
Followed instruction for Mrbayes installation from https://nbisweden.github.io/MrBayes/download.html (06/29/2021). MrBayes can be found in desktop/software/MrBayes
```
cd desktop/ncbi_database
git clone --depth=1 https://github.com/NBISweden/MrBayes.git
cd MrBayes
./configure
brew tap brewsci/bio

==> Tapping brewsci/bio
Cloning into '/usr/local/Homebrew/Library/Taps/brewsci/homebrew-bio'...
remote: Enumerating objects: 13905, done.
remote: Counting objects: 100% (681/681), done.
remote: Compressing objects: 100% (493/493), done.
remote: Total 13905 (delta 251), reused 585 (delta 187), pack-reused 13224
Receiving objects: 100% (13905/13905), 2.85 MiB | 12.97 MiB/s, done.
Resolving deltas: 100% (9489/9489), done.
Tapped 321 formulae (346 files, 3.7MB).

brew install mrbayes --with-open-mpi
```
### Converting Fasta File to Nexus File
```
install.packages("seqinr")
install.packages("ape")
library(seqinr)
library(ape)

data = read.FASTA("~/desktop/botany563/botany563-final-project/multiple_seq_align/t-coffee/dlx_protein.fna", type = "AA")
write.nexus.data(data, file="~/desktop/botany563/botany563-final-project/nexus_dlx_protein.nex", format="protein")

data = read.fasta("~/desktop/botany563/botany563-final-project/multiple_seq_align/t-coffee/exd_protein.aln", type = "AA")
write.nexus.data(data, file="~/desktop/botany563/botany563-final-project/nexus_exd_protein.nex", format="protein")
```
### MrBayes Block (added to Nexus File)
```
begin mrbayes;
    set nowarnings=yes;
    set autoclose=yes;
    set seed=112491;
    set swapseed=1337;
    lset nst=6 rates=gamma;
    mcmcp ngen=10000000 burninfrac=.25 samplefreq=1000 printfreq=1000 diagnfreq=10000 nruns=3 nchains=3 temp=0.40 swapfreq=10;
    outgroup Drosophila_melanogaster;
    mcmc;
        sumt;
        sump;
end;

```
### Running MrBayes
```
cd desktop/botany563/botany562-final-project
~/Dropbox/software/MrBayes mb nexus_dlx_protein.nex
~/Dropbox/software/MrBayes mb nexus_exd_protein.nex
```

# Coalescent 
## ASTRAL
Downloaded from https://github.com/smirarab/ASTRAL/blob/master/README.md#installation (04/16/2023). ASTRAL can be found in desktop/software/Astral
### Running ASTRAL
```
cd desktop/botany563/botany563-final-project/FINISHPATHNAME
java -jar ~/Desktop/software/astral/astral.5.7.8.jar -i (File name) -o (output file name)
```
## BUCKy
Downloaded v1.4.4 from https://pages.stat.wisc.edu/~ane/bucky/downloads.html (04/16/2023). BUCKy can be found in desktop/software/bucky-1.4.4
More information on BUCKy at https://pages.stat.wisc.edu/~larget/AustinWorkshop/tutorial.pdf
```
cd desktop/sofwater/bucky-1.4.4
bucky -a 1 -k 4 -n 1000000 -c 4 -s1 23546 -s2 4564 -o (output file name) 
```