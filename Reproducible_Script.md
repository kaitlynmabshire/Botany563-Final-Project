# General Commands
## Connecting Github to Git on personal laptop
### Cloning Directory
```
Pwd
Cd desktop/Botany563
Git clone https://github.com/kaitlynmabshire/Botany563.git
```
### Adding Upstream Directory and Pushing
```
Git remote add upstream https://github.com/kaitlynmabshire/Botany563.git
Git remote -v
Git add .
git commit -m "note"
git push
```

# Finding Sequences in C. aspersum Transcriptome

## NCBI BLAST+
-NCBI BLAST+ was downloaded from https://www.ncbi.nlm.nih.gov/books/NBK52640/

-Sequences found from the NCBI database were used as query and searched in assembled transcriptome.

### Making local database

```
cd dekstop/HCR/sequences/ncbi-blast-2.13.0+/bin
./makeblastdb -in cornu_aspersum.fasta -out cornu_aspersum_db -dbtype nucl -parse_seqid
```

### Running query

```
mv ~downloads/ncbi-blast-2.13.0 ~cd dekstop/HCR/sequences
cd dekstop/HCR/sequences/ncbi-blast-2.13.0+/bin
./tblastn -query <query_sequence_file.fasta> -out cornu_aspersum_db -out <file.txt>
```

Sequences found with the lowest E value (less than E^-20) were selected compared to ortholog sequences using ORFfinder on NCBI.

All sequences used, including ascension number, can be found in desktop/botany563/botany563-final-project/data

# Multiple Sequence Alignment

## T-Coffee:

### Downloading T-Coffee
Downloaded T-COFFEE_distribution_Version_13.45.0.4846264.tar.gz from http://www.tcoffee.org/Packages/Stable/Latest/ (Downloaded on 06/29/2021). T-Coffee can be found in dekstop/software/T-COFFEE_distribution_Version_13.45.61.3c310a9
```
mv ~/Downloads/T-COFFEE* ~/Desktop/software
cd desktop/software/T-COFFEE*
./install all
```
### Input:
```
cd botany563/botany563-final-project
t_coffee dlx_protein.fasta
t_coffee exd_protein.fasta
```

### Output:
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

###############

OUTPUT RESULTS
	#### File Type= GUIDE_TREE      Format= newick          Name= exd_protein.dnd
	#### File Type= MSA             Format= aln             Name= exd_protein.aln
	#### File Type= MSA             Format= html            Name= exd_protein.html

# Command Line: t_coffee dlx_protein.fasta  [PROGRAM:T-COFFEE]
# T-COFFEE Memory Usage: Current= 37.306 Mb, Max= 40.739 Mb
# Results Produced with T-COFFEE Version_13.45.0.4846264 (Version_13.45.0.4846264)
# T-COFFEE is available from http://www.tcoffee.org
# Register on: https://groups.google.com/group/tcoffee/
```

All T-Coffee aligned sequences can be found in desktop/botany563/botany563-final-project/multiple_seq_align/t-coffee

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

data = read.FASTA("~/desktop/botany563/botany563-final-project/multiple_seq_align/t-coffee/dlx_protein.fna", seqtype = "AA")
write.nexus.data(data, file="~/desktop/botany563/botany563-final-project/nexus_dlx_protein.nex", format="protein")

data = read.fasta("~/desktop/botany563/botany563-final-project/multiple_seq_align/t-coffee/exd_protein.fasta", seqtype = "AA")
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
### Output (dlx)
All dlx output files can be found in desktop/botany563/botany563-final-project/trees/mrbayes/dlx
```
Analysis completed in 93 hours 20 mins 11 seconds
      Analysis used 322163.41 seconds of CPU time on processor 0
      Likelihood of best state for "cold" chain of run 1 was -8705.22
      Likelihood of best state for "cold" chain of run 2 was -8708.96
      Likelihood of best state for "cold" chain of run 3 was -8711.49

      Acceptance rates for the moves in the "cold" chain of run 1:
         With prob.   (last 100)   chain accepted proposals by move
            25.7 %     ( 19 %)     Multiplier(Alpha)
             4.7 %     (  3 %)     ExtSPR(Tau,V)
             4.4 %     (  4 %)     ExtTBR(Tau,V)
             6.7 %     (  4 %)     NNI(Tau,V)
             0.3 %     (  0 %)     ParsSPR(Tau,V)
            26.0 %     ( 28 %)     Multiplier(V)
            28.3 %     ( 27 %)     Nodeslider(V)
            25.5 %     ( 31 %)     TLMultiplier(V)

      Acceptance rates for the moves in the "cold" chain of run 2:
         With prob.   (last 100)   chain accepted proposals by move
            25.7 %     ( 24 %)     Multiplier(Alpha)
             4.6 %     (  3 %)     ExtSPR(Tau,V)
             4.4 %     (  1 %)     ExtTBR(Tau,V)
             6.7 %     (  1 %)     NNI(Tau,V)
             0.3 %     (  0 %)     ParsSPR(Tau,V)
            26.1 %     ( 25 %)     Multiplier(V)
            28.2 %     ( 19 %)     Nodeslider(V)
            25.5 %     ( 32 %)     TLMultiplier(V)

      Acceptance rates for the moves in the "cold" chain of run 3:
         With prob.   (last 100)   chain accepted proposals by move
            25.6 %     ( 20 %)     Multiplier(Alpha)
             4.7 %     (  5 %)     ExtSPR(Tau,V)
             4.4 %     (  5 %)     ExtTBR(Tau,V)
             6.7 %     (  6 %)     NNI(Tau,V)
             0.3 %     (  0 %)     ParsSPR(Tau,V)
            25.4 %     ( 22 %)     Multiplier(V)
            28.2 %     ( 36 %)     Nodeslider(V)
            25.5 %     ( 30 %)     TLMultiplier(V)

      Chain swap information for run 1:

                   1       2       3 
           --------------------------
         1 |            0.20    0.02 
         2 |  333548            0.31 
         3 |  333222  333230         

      Chain swap information for run 2:

                   1       2       3 
           --------------------------
         1 |            0.20    0.02 
         2 |  333210            0.31 
         3 |  333571  333219         

      Chain swap information for run 3:

                   1       2       3 
           --------------------------
         1 |            0.20    0.02 
         2 |  332925            0.31 
         3 |  333689  333386         

      Upper diagonal: Proportion of successful state exchanges between chains
      Lower diagonal: Number of attempted state exchanges between chains

      Chain information:

        ID -- Heat 
       -----------
         1 -- 1.00  (cold chain)
         2 -- 0.71 
         3 -- 0.56 

      Heat = 1 / (1 + T * (ID - 1))
         (where T = 0.40 is the temperature and ID is the chain number)

      Summarizing trees in files "nexus_dlx_protein.nex.run1.t", "nexus_dlx_protein.nex.run2.t",...,"nexus_dlx_protein.nex.run3.t"
      Using relative burnin ('relburnin=yes'), discarding the first 25 % of sampled trees
      Writing statistics to files nexus_dlx_protein.nex.<parts|tstat|vstat|trprobs|con>
      Examining first file ...
      Found one tree block in file "nexus_dlx_protein.nex.run1.t" with 10001 trees in last block
      Expecting the same number of trees in the last tree block of all files

      Tree reading status:

      0      10      20      30      40      50      60      70      80      90     100
      v-------v-------v-------v-------v-------v-------v-------v-------v-------v-------v
      *********************************************************************************

      Read a total of 30003 trees in 3 files (sampling 22503 of them)
         (Each file contained 10001 trees of which 7501 were sampled)
                                                                                                                                     
      List of taxa in bipartitions:                                                 
                                                                                   
         1 -- Drosophila_melanogaster
         2 -- Owenia_fusiformis
         3 -- Doryteuthis_pealeii
         4 -- Pinctada_fucata
         5 -- Elysia_marginata
         6 -- Octopus_bimaculoides
         7 -- Gigantopelta_aegis
         8 -- Biomphalaria_glabrata
         9 -- Haliotis_rubra
        10 -- Haliotis_rufescens
        11 -- Candidula_unifasciata
        12 -- Cornu_aspersum
        13 -- Elysia_chlorotica
        14 -- Mizuhopecten_yessoensis
        15 -- Pecten_maximus
        16 -- Crassostrea_gigas
        17 -- Crassostrea_virginica
        18 -- Aplysia_californica
        19 -- Patella_vulgata
        20 -- Pomacea_canaliculata
        21 -- Sepia_pharaonis

      Key to taxon bipartitions (saved to file "nexus_dlx_protein.nex.parts"):

      ID -- Partition
      ---------------------------
       1 -- .********************
       2 -- .*...................
       3 -- ..*..................
       4 -- ...*.................
       5 -- ....*................
       6 -- .....*...............
       7 -- ......*..............
       8 -- .......*.............
       9 -- ........*............
      10 -- .........*...........
      11 -- ..........*..........
      12 -- ...........*.........
      13 -- ............*........
      14 -- .............*.......
      15 -- ..............*......
      16 -- ...............*.....
      17 -- ................*....
      18 -- .................*...
      19 -- ..................*..
      20 -- ...................*.
      21 -- ....................*
      22 -- ....*.......*........
      23 -- ...............**....
      24 -- ..*..*..............*
      25 -- ........**...........
      26 -- .............**......
      27 -- ...*...........**....
      28 -- ..........**.........
      29 -- ....*..*..***....*.*.
      30 -- ....*..*..***........
      31 -- ....*..*..***....*...
      32 -- ...*.........****....
      33 -- ....*.*******....***.
      34 -- .......*..**.........
      35 -- ..*******************
      36 -- ......*.**........*..
      37 -- ..**.*.......****...*
      38 -- ..*.................*
      39 -- ......*...........*..
      40 -- .....*..............*
      41 -- ......*.**...........
      42 -- .**.*********....****
      43 -- .*..*.*******....***.
      44 -- .*................*..
      45 -- .*....*.**........*..
      46 -- .*....*...........*..
      47 -- ....*.....***........
      48 -- ....*.**..***....***.
      ---------------------------

      Summary statistics for informative taxon bipartitions
         (saved to file "nexus_dlx_protein.nex.tstat"):

      ID   #obs     Probab.     Sd(s)+      Min(s)      Max(s)   Nruns 
      -----------------------------------------------------------------
      22  22503    1.000000    0.000000    1.000000    1.000000    3
      23  22503    1.000000    0.000000    1.000000    1.000000    3
      24  22503    1.000000    0.000000    1.000000    1.000000    3
      25  22503    1.000000    0.000000    1.000000    1.000000    3
      26  22502    0.999956    0.000077    0.999867    1.000000    3
      27  22494    0.999600    0.000133    0.999467    0.999733    3
      28  22488    0.999333    0.000353    0.998933    0.999600    3
      29  21912    0.973737    0.001442    0.972137    0.974937    3
      30  21786    0.968138    0.001991    0.966671    0.970404    3
      31  21250    0.944319    0.001149    0.943074    0.945341    3
      32  19348    0.859796    0.008044    0.855086    0.869084    3
      33  18182    0.807981    0.006383    0.800827    0.813092    3
      34  17753    0.788917    0.005830    0.785095    0.795627    3
      35  17124    0.760965    0.014209    0.752300    0.777363    3
      36  16586    0.737057    0.005555    0.731236    0.742301    3
      37  15886    0.705950    0.012679    0.694174    0.719371    3
      38  13562    0.602675    0.005236    0.599520    0.608719    3
      39   9430    0.419055    0.003181    0.416478    0.422610    3
      40   8464    0.376128    0.005047    0.370351    0.379683    3
      41   5900    0.262187    0.004684    0.258099    0.267298    3
      42   4960    0.220415    0.012342    0.206239    0.228769    3
      43   4908    0.218104    0.013393    0.202640    0.225837    3
      44   2979    0.132382    0.008799    0.123584    0.141181    3
      45   2853    0.126783    0.007933    0.118784    0.134649    3
      46   2709    0.120384    0.007400    0.112918    0.127716    3
      47   2567    0.114074    0.004200    0.111452    0.118917    3
      48   2546    0.113140    0.008337    0.104653    0.121317    3
      -----------------------------------------------------------------
      + Convergence diagnostic (standard deviation of split frequencies)
        should approach 0.0 as runs converge.


      Summary statistics for branch and node parameters
         (saved to file "nexus_dlx_protein.nex.vstat"):

                                              95% HPD Interval
                                            --------------------
      Parameter      Mean       Variance     Lower       Upper       Median     PSRF+  Nruns
      --------------------------------------------------------------------------------------
      length[1]     0.937376    0.017470    0.698475    1.209510    0.928639    1.000    3
      length[2]     0.413741    0.010094    0.232029    0.610023    0.401768    1.000    3
      length[3]     0.025446    0.000246    0.000738    0.055663    0.022666    1.000    3
      length[4]     0.192570    0.001069    0.131722    0.259000    0.190462    1.000    3
      length[5]     0.017264    0.000147    0.000004    0.040183    0.014788    1.000    3
      length[6]     0.098808    0.002513    0.014874    0.196828    0.091425    1.000    3
      length[7]     0.105636    0.000578    0.061749    0.154717    0.103894    1.000    3
      length[8]     0.260675    0.001521    0.184963    0.336736    0.258595    1.000    3
      length[9]     0.003415    0.000012    0.000000    0.010233    0.002373    1.000    3
      length[10]    0.003438    0.000012    0.000000    0.010431    0.002369    1.000    3
      length[11]    0.024574    0.000330    0.000006    0.059671    0.020757    1.000    3
      length[12]    0.067936    0.000866    0.016212    0.124485    0.063752    1.000    3
      length[13]    0.188698    0.000939    0.130949    0.249496    0.187064    1.000    3
      length[14]    0.024229    0.000094    0.006870    0.043312    0.023207    1.000    3
      length[15]    0.011211    0.000053    0.000001    0.025012    0.009922    1.000    3
      length[16]    0.017422    0.000075    0.002559    0.033979    0.016191    1.000    3
      length[17]    0.024049    0.000092    0.006851    0.042997    0.023066    1.000    3
      length[18]    0.120519    0.001862    0.040998    0.211769    0.117205    1.000    3
      length[19]    0.221954    0.002044    0.124276    0.306615    0.223634    1.000    3
      length[20]    0.336216    0.003901    0.217340    0.460523    0.332562    1.000    3
      length[21]    0.180830    0.005566    0.006834    0.286411    0.197191    1.000    3
      length[22]    0.129435    0.001093    0.066500    0.195753    0.128232    1.000    3
      length[23]    0.125918    0.000705    0.075303    0.178150    0.124605    1.000    3
      length[24]    0.244039    0.003008    0.139666    0.354666    0.243058    1.000    3
      length[25]    0.135439    0.000850    0.079503    0.192945    0.133783    1.000    3
      length[26]    0.147349    0.001176    0.081429    0.217206    0.146805    1.000    3
      length[27]    0.114163    0.000983    0.057087    0.179478    0.112566    1.000    3
      length[28]    0.087511    0.000806    0.031614    0.141786    0.086262    1.000    3
      length[29]    0.117169    0.002935    0.015913    0.222864    0.112782    1.000    3
      length[30]    0.093030    0.002164    0.011360    0.184600    0.087706    1.000    3
      length[31]    0.156980    0.003715    0.035100    0.276783    0.155611    1.000    3
      length[32]    0.151890    0.002138    0.052881    0.245237    0.152666    1.000    3
      length[33]    0.082983    0.001210    0.020035    0.152051    0.080188    1.000    3
      length[34]    0.042548    0.000681    0.000008    0.090063    0.039249    1.000    3
      length[35]    0.175453    0.003977    0.058959    0.301277    0.171736    1.000    3
      length[36]    0.064058    0.000559    0.021062    0.110606    0.061836    1.000    3
      length[37]    0.070906    0.001145    0.008960    0.135289    0.067255    1.000    3
      length[38]    0.052618    0.001132    0.000509    0.117243    0.046586    1.000    3
      length[39]    0.025335    0.000251    0.000079    0.054529    0.023014    1.000    3
      length[40]    0.116067    0.004930    0.000067    0.234352    0.112449    1.000    3
      length[41]    0.021701    0.000215    0.000016    0.049355    0.019019    1.000    3
      length[42]    0.150607    0.002776    0.046968    0.249136    0.152178    1.000    3
      length[43]    0.091303    0.001498    0.017669    0.166515    0.089704    1.000    3
      length[44]    0.084913    0.000844    0.029626    0.141452    0.083560    1.000    3
      length[45]    0.062146    0.000575    0.019661    0.109559    0.060615    1.000    3
      length[46]    0.033647    0.000248    0.006426    0.066777    0.032109    1.000    3
      length[47]    0.012428    0.000105    0.000011    0.032586    0.009778    0.999    3
      length[48]    0.049790    0.000409    0.015269    0.091687    0.047616    1.000    3
      --------------------------------------------------------------------------------------
      + Convergence diagnostic (PSRF = Potential Scale Reduction Factor; Gelman
        and Rubin, 1992) should approach 1.0 as runs converge. NA is reported when
        deviation of parameter values within all runs is 0 or when a parameter
        value (a branch length, for instance) is not sampled in all runs.


      Summary statistics for partitions with frequency >= 0.10 in at least one run:
          Average standard deviation of split frequencies = 0.005126
          Maximum standard deviation of split frequencies = 0.014209
          Average PSRF for parameter values (excluding NA and >10.0) = 1.000
          Maximum PSRF for parameter values = 1.000


      Clade credibility values:

      /---------------------------------------------------------- Drosophila_mela~ (1)
      |                                                                               
      |---------------------------------------------------------- Owenia_fusiform~ (2)
      |                                                                               
      |                                                  /------- Doryteuthis_pea~ (3)
      |                                           /--60--+                            
      |                                           |      \------- Sepia_pharaonis (21)
      |                            /------100-----+                                   
      |                            |              \-------------- Octopus_bimacul~ (6)
      |                            |                                                  
      |                            |              /-------------- Pinctada_fucata (4)
      |      /----------71---------+              |                                   
      +      |                     |      /--100--+      /------- Crassostrea_gi~ (16)
      |      |                     |      |       \--100-+                            
      |      |                     |      |              \------- Crassostrea_vi~ (17)
      |      |                     \--86--+                                           
      |      |                            |              /------- Mizuhopecten_y~ (14)
      |      |                            \------100-----+                            
      |      |                                           \------- Pecten_maximus (15)
      |      |                                                                        
      |      |                                           /------- Elysia_marginata (5)
      |      |                            /------100-----+                            
      |      |                            |              \------- Elysia_chlorot~ (13)
      \--76--+                            |                                           
             |                     /--97--+       /-------------- Biomphalaria_gl~ (8)
             |                     |      |       |                                   
             |                     |      \---79--+      /------- Candidula_unif~ (11)
             |              /--94--+              \--100-+                            
             |              |      |                     \------- Cornu_aspersum (12)
             |              |      |                                                  
             |       /--97--+      \----------------------------- Aplysia_califo~ (18)
             |       |      |                                                         
             |       |      \------------------------------------ Pomacea_canali~ (20)
             |       |                                                                
             \---81--+                            /-------------- Gigantopelta_ae~ (7)
                     |                            |                                   
                     |                            |      /------- Haliotis_rubra (9)
                     \-------------74-------------+--100-+                            
                                                  |      \------- Haliotis_rufes~ (10)
                                                  |                                   
                                                  \-------------- Patella_vulgata (19)
                                                                                      

      Phylogram (based on average branch lengths):

      /---------------------------------------------------------- Drosophila_mela~ (1)
      |                                                                               
      |------------------------- Owenia_fusiform~ (2)
      |                                                                               
      |                                /- Doryteuthis_pea~ (3)
      |                             /--+                                              
      |                             |  \------------ Sepia_pharaonis (21)
      |              /--------------+                                                 
      |              |              \------ Octopus_bimacul~ (6)
      |              |                                                                
      |              |               /------------ Pinctada_fucata (4)
      |          /---+               |                                                
      +          |   |        /------+       /- Crassostrea_gi~ (16)
      |          |   |        |      \-------+                                        
      |          |   |        |              \-- Crassostrea_vi~ (17)
      |          |   \--------+                                                       
      |          |            |         /- Mizuhopecten_y~ (14)
      |          |            \---------+                                             
      |          |                      \ Pecten_maximus (15)
      |          |                                                                    
      |          |                                  /- Elysia_marginata (5)
      |          |                          /-------+                                 
      |          |                          |       \------------ Elysia_chlorot~ (13)
      \----------+                          |                                         
                 |                    /-----+ /----------------- Biomphalaria_gl~ (8)
                 |                    |     | |                                       
                 |                    |     \-+     /- Candidula_unif~ (11)
                 |           /--------+       \-----+                                 
                 |           |        |             \---- Cornu_aspersum (12)
                 |           |        |                                               
                 |    /------+        \-------- Aplysia_califo~ (18)
                 |    |      |                                                        
                 |    |      \--------------------- Pomacea_canali~ (20)
                 |    |                                                               
                 \----+   /------ Gigantopelta_ae~ (7)
                      |   |                                                           
                      |   |       / Haliotis_rubra (9)
                      \---+-------+                                                   
                          |       \ Haliotis_rufes~ (10)
                          |                                                           
                          \-------------- Patella_vulgata (19)
                                                                                      
      |-----------| 0.200 expected changes per site

      Calculating tree probabilities...

      Credible sets of trees (1313 trees sampled):
         50 % credible set contains 13 trees
         90 % credible set contains 230 trees
         95 % credible set contains 459 trees
         99 % credible set contains 1088 trees

      Summarizing parameters in 3 files (nexus_dlx_protein.nex.run1.p,
         nexus_dlx_protein.nex.run2.p, etc)
      Writing summary statistics to file nexus_dlx_protein.nex.pstat
      Using relative burnin ('relburnin=yes'), discarding the first 25 % of samples

      Below are rough plots of the generation (x-axis) versus the log   
      probability of observing the data (y-axis). You can use these     
      graphs to determine what the burn in for your analysis should be. 
      When the log probability starts to plateau you may be at station- 
      arity. Sample trees and parameters after the log probability      
      plateaus. Of course, this is not a guarantee that you are at sta- 
      tionarity. Also examine the convergence diagnostics provided by   
      the 'sump' and 'sumt' commands for all the parameters in your     
      model. Remember that the burn in is the number of samples to dis- 
      card. There are a total of ngen / samplefreq samples taken during 
      a MCMC analysis.                                                  

      Overlay plot for all 3 runs:
      (1 = Run number 1; 2 = Run number 2 etc.; * = Several runs)

      +------------------------------------------------------------+ -8720.06
      |        1                                                   |
      |                                                    1    1  |
      |                                              3             |
      |     3              12  3            1                      |
      |3 2  13        3  13   1    21  1      2 2 *    2     1  3  |
      |  1 1    2333  22    3 2       2  1*131 *1  1  *1 1   2   31|
      |23 32 2*  2   * 1   2 33   * 2  *2  2 232 * 31   223 1 2    |
      | 2 23  3 3 2     33   1 12  3321 33  2 1   32312 3 23 313  *|
      | 1 1    *111 * 1 2 *312  1131     2 3 3  3   2    3 2   2   |
      |  3  2      233   2      32   *3 1 3             1 1 3 3    |
      |1           1    1      2                               1   |
      |      1                   3                   2          22 |
      |                                                3    2    1 |
      |                                                            |
      |                3                                           |
      +------+-----+-----+-----+-----+-----+-----+-----+-----+-----+ -8723.60
      ^                                                            ^
      2500000                                                      10000000


      Estimated marginal likelihoods for runs sampled in files
         "nexus_dlx_protein.nex.run1.p", "nexus_dlx_protein.nex.run2.p", etc:
         (Use the harmonic mean for Bayes factor comparisons of models)

         (Values are saved to the file nexus_dlx_protein.nex.lstat)

      Run   Arithmetic mean   Harmonic mean
      --------------------------------------
        1      -8714.59         -8734.52
        2      -8715.28         -8739.07
        3      -8714.77         -8738.45
      --------------------------------------
      TOTAL    -8714.84         -8738.41
      --------------------------------------


      Model parameter summaries over all 3 runs sampled in files
         "nexus_dlx_protein.nex.run1.p", "nexus_dlx_protein.nex.run2.p" etc:
         Summaries are based on a total of 22503 samples from 3 runs.
         Each run produced 10001 samples of which 7501 samples were included.
         Parameter summaries saved to file "nexus_dlx_protein.nex.pstat".

                                            95% HPD Interval
                                          --------------------
      Parameter      Mean      Variance     Lower       Upper       Median    min ESS*  avg ESS    PSRF+ 
      --------------------------------------------------------------------------------------------------
      TL          5.278405    0.108902    4.655247    5.948243    5.261960   6611.19   6828.64    1.000
      alpha       0.993775    0.009667    0.802640    1.184501    0.988473   7215.86   7327.43    1.000
      --------------------------------------------------------------------------------------------------
      * Convergence diagnostic (ESS = Estimated Sample Size); min and avg values
        correspond to minimal and average ESS among runs. 
        ESS value below 100 may indicate that the parameter is undersampled. 
      + Convergence diagnostic (PSRF = Potential Scale Reduction Factor; Gelman
        and Rubin, 1992) should approach 1.0 as runs converge.
```
### Output (exd)
All exd output files can be found in desktop/botany563/botany563-final-project/trees/mrbayes/exd
Output files include:
"nexus_exd_protein.nex.mcmc"
"nexus_exd_protein.nex.tstat", "nexus_exd_protein.nex.vstat", "nexus_exd_protein.nex.parts"
"nexus_exd_protein.nex.run1.p", "nexus_exd_protein.nex.run2.p", etc.

_

All MrBayes output files can be found in desktop/botany563/botany563-final-project/trees/mrbayes

## BEAST2
### Download
Downloaded BEAST 2.7.4 from http://www.beast2.org/download-mac/ (04/24/2023). BEAST2 can be found in desktop/software/beast_2.7.4
Tutorial for running multispecies coalescent was followed from https://www.beast2.org/2022/03/31/starbeast3.html and https://taming-the-beast.org/tutorials/StarBeast-Tutorial/
```
1) Opened BEAUti application. 
2) Installed OBAMA and StarBeast2 package by (File->Manage Packages)
3) Changed template mode to StarBeast3 using (File->Template->StarBeast3).
4) Imported files "nexus_dlx_protein.nex" and "nexus_exd_protein.nex" by (File->Import Alignment)
5) In Taxon Sets tab, click on Guess. Selected Split on Character and Take Groups 2.
6) In the Site Model tab, OBAMA was selected for both gene alignments. Additionally, substitution site estimate was selected (checked off).
7) In Species Clock Model tab, Species Tree Relaxed Model was chosen, and both Stdev and Clock rate estimate were selected (checked off).
8) In MCMC tab, Chain Length was set to 10000000 and Store Every was set to 5000. Under TraceLog, file name was changed to "dlx_exd.log" and Log Every was changed to 5000. Under SpeciesTreeLogger, File Name was changed to "mollusk.species.tre" and Log Every was changed to 5000.
9) File was saved as dlx_exd2_.xml in desktop/botany563/botany563-final-project/trees/BEAST
10) Opened BEAST and inputted dlx_exd2_.xml. Then clicked run.
11) Once BEAST run was finished, TreeAnnotator v2.7.4 was used to create consensus trees (output files: "dlx_beast.tre", "exd_beast.tre", "species_beast.tre")
```
### Output
```
Operator                                                                                                      Tuning    #accept    #reject      Pr(m)  Pr(acc|m)
starbeast3.operators.NodeReheight2(Reheight.t:Species)                                                             -    5660260    3879788    0.09544    0.59332 
starbeast3.operators.CoordinatedExponential(CoordinatedExponential.t:Species)                                0.00525     148269    5205872    0.04772    0.02769 
starbeast3.operators.CoordinatedUniform(CoordinatedUniform.t:Species)                                              -    4150477    6012451    0.09544    0.40839 
kernel.BactrianSubtreeSlide(BactrianSubtreeSlide.t:Species)                                                  0.06003      70369    4700580    0.04772    0.01475 Try decreasing size to about 0.03
WilsonBalding(WilsonBalding.t:Species)                                                                             -      82083    4690859    0.04772    0.01720 
Exchange(Wide.t:Species)                                                                                           -      71407    4701277    0.04772    0.01496 
AdaptableOperatorSampler(AdaptableTopologyOperator.tree.Species)                                                   -    1419152    3354136    0.04772    0.29731 
Uniform(UniformOperator.t:Species)                                                                                 -    5497466    6964445    0.00954    0.44114 
kernel.BactrianScaleOperator(TreeRootScaler.t:Species)                                                       0.43401      27161     927558    0.00954    0.02845 Try setting scale factor to about 0.217
kernel.BactrianNodeOperator(BactrianNodeOperator.t:Species)                                                  1.94208    2341846    5231856    0.00954    0.30921 
AdaptableOperatorSampler(AdaptableTopologyOperator.lengths.Species)                                                -   10473890   21337233    0.31812    0.32925 
starbeast3.operators.PopSizeGibbsSampler(PopSizeGibbsSampler.Species)                                              -   15906726          0    0.15906    1.00000 
AdaptableOperatorSampler(AdaptableOperatorSampler.popmean:Species)                                                 -     450065    1137901    0.01591    0.28342 
AdaptableOperatorSampler(AdaptableOperatorSampler.YuleModel.t:Species)                                             -     449474    1140894    0.01591    0.28262 
kernel.BactrianScaleOperator(clockRateScaler.c:nexus_dlx_protein)                                            0.13525       7871      23569    0.00032    0.25035 
kernel.BactrianScaleOperator(clockRateScaler.c:nexus_exd_protein)                                            0.21632       8454      23348    0.00032    0.26583 
kernel.AdaptableVarianceMultivariateNormalOperator(OBAMA_FrequenciesAVMNOperator.s:nexus_dlx_protein)        0.49241       3948      11906    0.00016    0.24902 
bmodeltest.evolution.operators.BMTScaleOperator(OBAMA_gammaShapeScaler.s:nexus_dlx_protein)                  0.46623       3332      12344    0.00016    0.21255 
bmodeltest.evolution.operators.BMTScaleOperator(OBAMA_ProportionInvariableScaler.s:nexus_dlx_protein)        0.46548       3479      12321    0.00016    0.22019 
bmodeltest.evolution.operators.BMTBirthDeathOperator(OBAMA_hasGammaRatesFlipper.s:nexus_dlx_protein)               -          0      31871    0.00032    0.00000 
bmodeltest.evolution.operators.BMTBirthDeathOperator(OBAMA_hasInvariableSitesFlipper.s:nexus_dlx_protein)          -          0      31813    0.00032    0.00000 
beast.base.inference.operator.BitFlipOperator(OBAMA_FreqsFlipOperator.s:nexus_dlx_protein)                         -          4      31677    0.00032    0.00013 
beast.base.inference.operator.UniformOperator(OBAMA_ModelIndicatorUniformOperator.s:nexus_dlx_protein)             -      63522     891508    0.00954    0.06651 
kernel.AdaptableVarianceMultivariateNormalOperator(OBAMA_FrequenciesAVMNOperator.s:nexus_exd_protein)        0.49916       4277      11870    0.00016    0.26488 
bmodeltest.evolution.operators.BMTScaleOperator(OBAMA_gammaShapeScaler.s:nexus_exd_protein)                  0.58450       3190      12585    0.00016    0.20222 
bmodeltest.evolution.operators.BMTScaleOperator(OBAMA_ProportionInvariableScaler.s:nexus_exd_protein)        0.16472       2349      13771    0.00016    0.14572 
bmodeltest.evolution.operators.BMTBirthDeathOperator(OBAMA_hasGammaRatesFlipper.s:nexus_exd_protein)               -          0      31976    0.00032    0.00000 
bmodeltest.evolution.operators.BMTBirthDeathOperator(OBAMA_hasInvariableSitesFlipper.s:nexus_exd_protein)          -       3608      28032    0.00032    0.11403 
beast.base.inference.operator.BitFlipOperator(OBAMA_FreqsFlipOperator.s:nexus_exd_protein)                         -          0      31599    0.00032    0.00000 
beast.base.inference.operator.UniformOperator(OBAMA_ModelIndicatorUniformOperator.s:nexus_exd_protein)             -      63864     890854    0.00954    0.06689 
kernel.BactrianScaleOperator(OBAMA_mutationRateScaler.s:nexus_exd_protein)                                   0.20786       4941      11054    0.00016    0.30891 
kernel.BactrianScaleOperator(OBAMA_mutationRateScaler.s:nexus_dlx_protein)                                   0.12530       4930      10948    0.00016    0.31049 
starbeast3.operators.ParallelMCMCTreeOperator(ParallelMCMCTreeOperator)                                            -          0          0    0.01000        NaN 

     Tuning: The value of the operator's tuning parameter, or '-' if the operator can't be optimized.
    #accept: The total number of times a proposal by this operator has been accepted.
    #reject: The total number of times a proposal by this operator has been rejected.
      Pr(m): The probability this operator is chosen in a step of the MCMC (i.e. the normalized weight).
  Pr(acc|m): The acceptance probability (#accept as a fraction of the total proposals for this operator).


Total calculation time: 551336.975 seconds
End likelihood: -14331.269858383224
```
Output files for BEAST can be found in desktop/botany563/botany563-final-project/trees/BEAST