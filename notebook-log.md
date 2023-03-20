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

#### Output:
```
PROGRAM: T-COFFEE Version_13.45.0.4846264 (Version_13.45.0.4846264)
-full_log      	S	[0] 
-genepred_score	S	[0] 	nsd
-run_name      	S	[0] 
-mem_mode      	S	[0] 	mem
-extend        	D	[1] 	1 
-extend_mode   	S	[0] 	very_fast_triplet
-max_n_pair    	D	[0] 	10 
-seq_name_for_quadruplet	S	[0] 	all
-compact       	S	[0] 	default
-clean         	S	[0] 	no
-do_self       	FL	[0] 	0
-do_normalise  	D	[0] 	1000 
-template_file 	S	[0] 
-setenv        	S	[0] 	0
-export        	S	[0] 	0
-template_mode 	S	[0] 
-flip          	D	[0] 	0 
-remove_template_file	D	[0] 	0 
-profile_template_file	S	[0] 
-in            	S	[0] 
-seq           	S	[1] 	dlx_protein.fasta
-aln           	S	[0] 
-method_limits 	S	[0] 
-method        	S	[0] 
-lib           	S	[0] 
-profile       	S	[0] 
-profile1      	S	[0] 
-profile2      	S	[0] 
-pdb           	S	[0] 
-relax_lib     	D	[0] 	1 
-filter_lib    	D	[0] 	0 
-shrink_lib    	D	[0] 	0 
-out_lib       	W_F	[0] 	no
-out_lib_mode  	S	[0] 	primary
-lib_only      	D	[0] 	0 
-outseqweight  	W_F	[0] 	no
-seq_source    	S	[0] 	ANY
-cosmetic_penalty	D	[0] 	0 
-gapopen       	D	[0] 	0 
-gapext        	D	[0] 	0 
-fgapopen      	D	[0] 	0 
-fgapext       	D	[0] 	0 
-nomatch       	D	[0] 	0 
-newtree       	W_F	[0] 	default
-tree          	W_F	[0] 	NO
-usetree       	R_F	[0] 
-tree_mode     	S	[0] 	nj
-distance_matrix_mode	S	[0] 	ktup
-distance_matrix_sim_mode	S	[0] 	idmat_sim1
-quicktree     	FL	[0] 	0
-outfile       	W_F	[0] 	default
-maximise      	FL	[1] 	1
-output        	S	[0] 	aln	html
-len           	D	[0] 	0 
-infile        	R_F	[0] 
-matrix        	S	[0] 	default
-tg_mode       	D	[0] 	1 
-profile_mode  	S	[0] 	cw_profile_profile
-profile_comparison	S	[0] 	profile
-dp_mode       	S	[0] 	linked_pair_wise
-ktuple        	D	[0] 	1 
-ndiag         	D	[0] 	0 
-diag_threshold	D	[0] 	0 
-diag_mode     	D	[0] 	0 
-sim_matrix    	S	[0] 	vasiliky
-transform     	S	[0] 
-extend_seq    	FL	[0] 	0
-outorder      	S	[0] 	input
-inorder       	S	[0] 	aligned
-seqnos        	S	[0] 	off
-case          	S	[0] 	keep
-cpu           	D	[0] 	0 
-ulimit        	D	[0] 	-1 
-maxnseq       	D	[0] 	-1 
-maxlen        	D	[0] 	-1 
-sample_dp     	D	[0] 	0 
-weight        	S	[0] 	default
-seq_weight    	S	[0] 	no
-align         	FL	[1] 	1
-mocca         	FL	[0] 	0
-domain        	FL	[0] 	0
-start         	D	[0] 	0 
-len           	D	[0] 	0 
-scale         	D	[0] 	0 
-mocca_interactive	FL	[0] 	0
-method_evaluate_mode	S	[0] 	default
-color_mode    	S	[0] 	new
-aln_line_length	D	[0] 	0 
-evaluate_mode 	S	[0] 	triplet
-get_type      	FL	[0] 	0
-clean_aln     	D	[0] 	0 
-clean_threshold	D	[1] 	1 
-clean_iteration	D	[1] 	1 
-clean_evaluate_mode	S	[0] 	t_coffee_fast
-extend_matrix 	FL	[0] 	0
-prot_min_sim  	D	[0] 	0 
-prot_max_sim  	D	[100] 	100 
-psiJ          	D	[0] 	3 
-psitrim_mode  	S	[0] 	regtrim
-psitrim_tree  	S	[0] 	codnd
-psitrim       	D	[100] 	100 
-prot_min_cov  	D	[90] 	90 
-pdb_type      	S	[0] 	d
-pdb_min_sim   	D	[35] 	35 
-pdb_max_sim   	D	[100] 	100 
-pdb_min_cov   	D	[50] 	50 
-pdb_blast_server	W_F	[0] 	EBI
-blast         	W_F	[0] 
-blast_server  	W_F	[0] 	EBI
-pdb_db        	W_F	[0] 	pdb
-protein_db    	W_F	[0] 	uniref50
-method_log    	W_F	[0] 	no
-struc_to_use  	S	[0] 
-cache         	W_F	[0] 	use
-print_cache   	FL	[0] 	0
-align_pdb_param_file	W_F	[0] 	no
-align_pdb_hasch_mode	W_F	[0] 	hasch_ca_trace_bubble
-external_aligner	S	[0] 	NO
-msa_mode      	S	[0] 	tree
-et_mode       	S	[0] 	et
-master        	S	[0] 	no
-blast_nseq    	D	[0] 	0 
-lalign_n_top  	D	[0] 	10 
-iterate       	D	[0] 	0 
-trim          	D	[0] 	0 
-split         	D	[0] 	0 
-trimfile      	S	[0] 	default
-split         	D	[0] 	0 
-split_nseq_thres	D	[0] 	0 
-split_score_thres	D	[0] 	0 
-check_pdb_status	D	[0] 	0 
-clean_seq_name	D	[0] 	0 
-seq_to_keep   	S	[0] 
-dpa_master_aln	S	[0] 
-dpa_maxnseq   	D	[0] 	0 
-dpa_min_score1	D	[0] 
-dpa_min_score2	D	[0] 
-dpa_keep_tmpfile	FL	[0] 	0
-dpa_debug     	D	[0] 	0 
-multi_core    	S	[0] 	templates_jobs_relax_msa_evaluate
-n_core        	D	[0] 	1 
-thread        	D	[0] 	1 
-max_n_proc    	D	[0] 	1 
-lib_list      	S	[0] 
-prune_lib_mode	S	[0] 	5
-tip           	S	[0] 	none
-rna_lib       	S	[0] 
-no_warning    	D	[0] 	0 
-run_local_script	D	[0] 	0 
-proxy         	S	[0] 	unset
-email         	S	[0] 
-clean_overaln 	D	[0] 	0 
-overaln_param 	S	[0] 
-overaln_mode  	S	[0] 
-overaln_model 	S	[0] 
-overaln_threshold	D	[0] 	0 
-overaln_target	D	[0] 	0 
-overaln_P1    	D	[0] 	0 
-overaln_P2    	D	[0] 	0 
-overaln_P3    	D	[0] 	0 
-overaln_P4    	D	[0] 	0 
-exon_boundaries	S	[0] 
-display       	D	[0] 	100 

INPUT FILES
	Input File (S) dlx_protein.fasta  Format fasta_seq
	Input File (M) proba_pair 

Identify Master Sequences [no]:

Master Sequences Identified
INPUT SEQUENCES: 17 SEQUENCES  [PROTEIN]
  Input File dlx_protein.fasta                       Seq Biomphalaria_                           Length  292 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta                       Seq Candidula_                              Length  305 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta                       Seq Cornu_aspersum_TRINITY_DN57644_c0_g1_i1 Length  120 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta                       Seq Doryteuthis_pealeii_QVQ68771.1          Length  333 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta                       Seq Drosophila_melanogaster_NP_523857.1     Length  327 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta                       Seq Elysia_                                 Length  267 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta                       Seq Elysia_chlorotica_RUS90064.1            Length  326 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta                       Seq Gigantopelta_                           Length  295 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta                       Seq Haliotis_rubra_XP_046576763.1           Length  285 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta                       Seq Haliotis_rufescens_XP_046337404.1       Length  285 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta                       Seq Nipponacmea_fuscoviridis_BBB36758.1     Length  178 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta                       Seq Octopus_                                Length   80 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta                       Seq Owenia_fusiformis_CAH1775388.1          Length  298 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta                       Seq Patelloida_mimula_UPN66625.1            Length  126 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta                       Seq Pinctada_fucata_ASY93124.1              Length  318 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta                       Seq Plakobranchus_ocellatus_GFO48356.1      Length  206 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta                       Seq Sepia_bandensis_QDF46136.1              Length  221 type PROTEIN Struct Unchecked

  Multi Core Mode (read): 1 processor(s):

	--- Process Method/Library/Aln Sdlx_protein.fasta
	xxx Retrieved Sdlx_protein.fasta
	--- Process Method/Library/Aln Mproba_pair
	xxx Retrieved Mproba_pair

	All Methods Retrieved

MANUAL PENALTIES: gapopen=0 gapext=0

	Library Total Size: [158420]

Library Relaxation: Multi_proc [1]
 
!		[Relax Library][TOT=   17][100 %]

Relaxation Summary: [158420]--->[97566]



UN-WEIGHTED MODE: EVERY SEQUENCE WEIGHTS 1

MAKE GUIDE TREE 
	[MODE=nj][DONE]

PROGRESSIVE_ALIGNMENT [Tree Based]
Group    1: Biomphalaria_
Group    2: Candidula_
Group    3: Cornu_aspersum_TRINITY_DN57644_c0_g1_i1
Group    4: Doryteuthis_pealeii_QVQ68771.1
Group    5: Drosophila_melanogaster_NP_523857.1
Group    6: Elysia_
Group    7: Elysia_chlorotica_RUS90064.1
Group    8: Gigantopelta_
Group    9: Haliotis_rubra_XP_046576763.1
Group   10: Haliotis_rufescens_XP_046337404.1
Group   11: Nipponacmea_fuscoviridis_BBB36758.1
Group   12: Octopus_
Group   13: Owenia_fusiformis_CAH1775388.1
Group   14: Patelloida_mimula_UPN66625.1
Group   15: Pinctada_fucata_ASY93124.1
Group   16: Plakobranchus_ocellatus_GFO48356.1
Group   17: Sepia_bandensis_QDF46136.1

#Single Thread

	Group   18: [Group    3 (   1 seq)] with [Group    2 (   1 seq)]-->[Len=  306][PID:57241]
	Group   19: [Group   18 (   2 seq)] with [Group    1 (   1 seq)]-->[Len=  337][PID:57241]
	Group   20: [Group   17 (   1 seq)] with [Group    4 (   1 seq)]-->[Len=  333][PID:57241]
	Group   21: [Group   12 (   1 seq)] with [Group   20 (   2 seq)]-->[Len=  333][PID:57241]
	Group   22: [Group   10 (   1 seq)] with [Group    9 (   1 seq)]-->[Len=  285][PID:57241]
	Group   23: [Group   22 (   2 seq)] with [Group    8 (   1 seq)]-->[Len=  300][PID:57241]
	Group   24: [Group   14 (   1 seq)] with [Group   11 (   1 seq)]-->[Len=  201][PID:57241]
	Group   25: [Group   24 (   2 seq)] with [Group   23 (   3 seq)]-->[Len=  303][PID:57241]
	Group   26: [Group   25 (   5 seq)] with [Group   21 (   3 seq)]-->[Len=  360][PID:57241]
	Group   27: [Group   26 (   8 seq)] with [Group   15 (   1 seq)]-->[Len=  398][PID:57241]
	Group   28: [Group   13 (   1 seq)] with [Group    5 (   1 seq)]-->[Len=  369][PID:57241]
	Group   29: [Group   28 (   2 seq)] with [Group   27 (   9 seq)]-->[Len=  481][PID:57241]
	Group   30: [Group   29 (  11 seq)] with [Group   19 (   3 seq)]-->[Len=  514][PID:57241]
	Group   31: [Group   16 (   1 seq)] with [Group    6 (   1 seq)]-->[Len=  269][PID:57241]
	Group   32: [Group    7 (   1 seq)] with [Group   31 (   2 seq)]-->[Len=  373][PID:57241]
	Group   33: [Group   32 (   3 seq)] with [Group   30 (  14 seq)]-->[Len=  587][PID:57241]


!		[Final Evaluation][TOT=  293][100 %]

CLUSTAL FORMAT for T-COFFEE Version_13.45.0.4846264 [http://www.tcoffee.org] [MODE:  ], CPU=0.00 sec, SCORE=827, Nseq=17, Len=587 

Drosophila_melanogaster_NP_523857.1      -------------------------------------------MDAPDAP
Owenia_fusiformis_CAH1775388.1           -------------------------------------------ML-----
Doryteuthis_pealeii_QVQ68771.1           DTVDLSTLLVRICYSRFTSGLSVSLPSTFIRKLPIINRKTGPMML-----
Pinctada_fucata_ASY93124.1               -------------------------------------------ML-----
Nipponacmea_fuscoviridis_BBB36758.1      --------------------------------------------------
Patelloida_mimula_UPN66625.1             -------------------------------------------ML-----
Sepia_bandensis_QDF46136.1               -------------------------------------------ML-----
Elysia_                                  --------------------------------------------------
Octopus_                                 --------------------------------------------------
Gigantopelta_                            -------------------------------------------ML-----
Biomphalaria_                            -------------------------------------------M------
Haliotis_rubra_XP_046576763.1            -------------------------------------------ML-----
Haliotis_rufescens_XP_046337404.1        -------------------------------------------ML-----
Candidula_                               -------------------------------------------M------
Cornu_aspersum_TRINITY_DN57644_c0_g1_i1  --------------------------------------------------
Elysia_chlorotica_RUS90064.1             -------------------------------------------MS-----
Plakobranchus_ocellatus_GFO48356.1       --------------------------------------------------
                                                                                           

Drosophila_melanogaster_NP_523857.1      HTPKYMDGGNTAAS-VTPGINIP-GKSAFVELQQH---AAAGYG-----G
Owenia_fusiformis_CAH1775388.1           ---------NMTGS-EAIGQDIPDSKSAFMEIQQM----QQNMGHHAAYP
Doryteuthis_pealeii_QVQ68771.1           ---------NIAGSVDGLDQDVT-GKSAFMELQQQP--MPPGMA-HPAYP
Pinctada_fucata_ASY93124.1               ---------NV-GSVEGMEQEMA-GKSAFMELQQS---GGMPMG-HPAYP
Nipponacmea_fuscoviridis_BBB36758.1      -------------------------------LQQQS--MAGGMG-HPAYN
Patelloida_mimula_UPN66625.1             ---------NMTSNMDGMDPEIA-SKSAFMELQQQS--MTGGMG-HPAYN
Sepia_bandensis_QDF46136.1               ---------NIAGSVDGLDQDVT-GKSAFMELQQQP--MPPGMA-HPAYP
Elysia_                                  --------------------------------------------------
Octopus_                                 --------------------------------------------------
Gigantopelta_                            ---------NMTGPMDGLDQEMV-GKSAFMELQQQ---MPPGMG-HPAYQ
Biomphalaria_                            -------------------------------------------GS-P---
Haliotis_rubra_XP_046576763.1            ---------NMAGAMDGLEQEMV-GKSAFMELQQQ---MPPSMG-HPAYP
Haliotis_rufescens_XP_046337404.1        ---------NMAGAMDGLEQEMV-GKSAFMELQQQ---MPPSMG-HPAYP
Candidula_                               ---------------DGLEQDMMKQQSAFMELQQQTGGLAHSMGHHPAYQ
Cornu_aspersum_TRINITY_DN57644_c0_g1_i1  --------------------------------------------------
Elysia_chlorotica_RUS90064.1             ---------------------------------------HHHHH-HPAYQ
Plakobranchus_ocellatus_GFO48356.1       --------------------------------------------------
                                                                                           

Drosophila_melanogaster_NP_523857.1      IRST-YQHFGP-QG-G-----Q---DSGF-PS-PRSAL-GYPFPPMHQNS
Owenia_fusiformis_CAH1775388.1           IRAS-YP---S-QH-PS----Q---DSMY-TSQATRPL-GYPFS-MNGMS
Doryteuthis_pealeii_QVQ68771.1           IRSS-YP---T-HQ-SQ----H---ENVFSTAQHTRPF-TYPFA-MNTMS
Pinctada_fucata_ASY93124.1               MRSS-YQ---PPHHGGQ----HG--ESVFSNPQGRGPLAGYPFH-MNAMS
Nipponacmea_fuscoviridis_BBB36758.1      IRSG-YP---T-QH-SQ----H---D-MFPTSQHTRSF-GYPFP-MNSMA
Patelloida_mimula_UPN66625.1             IPSG-YP---R-QH-SQ----H---E-MFPTSQHTRXF-GYPFS-MNSMA
Sepia_bandensis_QDF46136.1               IRSS-YP---T-HQ-SQ----H---ENVFSTAQHTRPF-TYPFA-MNTMS
Elysia_                                  --------------------------------------------------
Octopus_                                 --------------------------------------------------
Gigantopelta_                            IRTG-YP---P-QH-GH----H---DGSY-TSQATRSL-GYPFS-MNSMA
Biomphalaria_                            VRTV-SH---D-AH-PH--------ESLVKT-DLPRFT-CHVFR-LQYNL
Haliotis_rubra_XP_046576763.1            IRSG-YP---P-QH-SQ----H---D-VF-TSQPTRPL-AYPFP-MNSMA
Haliotis_rufescens_XP_046337404.1        IRSG-YP---P-QH-SQ----H---D-VF-TSQPTRPL-AYPFP-MNSMA
Candidula_                               IRPQ-YP---G-AH-PQ----HHQPHDVFSSQQHGRMP-S----------
Cornu_aspersum_TRINITY_DN57644_c0_g1_i1  --------------------------------------------------
Elysia_chlorotica_RUS90064.1             LRAAQYG---S-AH-AQHAQGH---DSVFSSGQHGRAL-AYPFG-MNGMG
Plakobranchus_ocellatus_GFO48356.1       --------------------------------------------------
                                                                                           

Drosophila_melanogaster_NP_523857.1      YSGYH---------L------GSYAPPCASP---------PKD-------
Owenia_fusiformis_CAH1775388.1           HTAYNS--PSH-F-V------NPYQ--ASCP---------PRD-------
Doryteuthis_pealeii_QVQ68771.1           ATTYNP--PTHAFSV------TPYQ--TTSP---------TREGCTFYFP
Pinctada_fucata_ASY93124.1               PTAYNP-SSGHHFSM------PPYQ--SPSP---------TRD-------
Nipponacmea_fuscoviridis_BBB36758.1      PSGYNAVPPSHHFPM------SPYQ--PPSP---------TRD-------
Patelloida_mimula_UPN66625.1             PSGYNAVPPSHHFPM------SPYQ--PPSP---------TRD-------
Sepia_bandensis_QDF46136.1               ATTYNP--PTHAFSV------TPYQ--TTSP---------TREGCTFYFP
Elysia_                                  --------------------------------------------------
Octopus_                                 -TRDNP--PTHPFSV------TPYQ--TTSP---------TREGYTFYFP
Gigantopelta_                            PTSYNP-PP-PHFSM------SPYQ--TPSP---------PRD-------
Biomphalaria_                            YTSI-I--DDHPFVTRLTNCDEDYK--SVLPGQRIRDRVWHQQ-------
Haliotis_rubra_XP_046576763.1            PTSYNP-PTSHPFSM------SPYQ--TPSP---------PRD-------
Haliotis_rufescens_XP_046337404.1        PTSYNP-PTSHPFSM------SPYQ--TPSP---------PRD-------
Candidula_                               ----------HPFSV------SPYQ--TPSP---------PRD-------
Cornu_aspersum_TRINITY_DN57644_c0_g1_i1  ----------------------------------------PRD-------
Elysia_chlorotica_RUS90064.1             GNPYGS-PGAHPFSV------SPYQ--TPSP---------PRD-------
Plakobranchus_ocellatus_GFO48356.1       --------------------------------------------------
                                                                                           

Drosophila_melanogaster_NP_523857.1      -DFSISDKCEDSGLRVNGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLAL
Owenia_fusiformis_CAH1775388.1           -DKSP----IEEQLRVNGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLAL
Doryteuthis_pealeii_QVQ68771.1           TEKTQ----MEEQLRINGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLAL
Pinctada_fucata_ASY93124.1               -DKSQ----MDE-LRINGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLAL
Nipponacmea_fuscoviridis_BBB36758.1      -DKSQ----VEEQLRINGKGKKLRKPRTIYSSLQLQQLNRRFQRTQYLAL
Patelloida_mimula_UPN66625.1             -DKSQ----VEEQLRINGKGKKLRKPRTIYSS------------------
Sepia_bandensis_QDF46136.1               TEKSQ----MEEQLRINGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLAL
Elysia_                                  ----------------------MRKPRTIYSSLQLQQLNRRFQRTQYLAL
Octopus_                                 TEKSQ----MEEQLRMNGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLAL
Gigantopelta_                            -DKSQ----VEEQLRINGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLAL
Biomphalaria_                            -HKGQ----VEEQLRINGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLAL
Haliotis_rubra_XP_046576763.1            -EKPQ----MDDQLRINGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLAL
Haliotis_rufescens_XP_046337404.1        -EKPQ----MDDQLRINGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLAL
Candidula_                               -DKSQ----VEEQLRINGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLAL
Cornu_aspersum_TRINITY_DN57644_c0_g1_i1  -DKSQ----VEEQLRINGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLAL
Elysia_chlorotica_RUS90064.1             -DKSQ----VEEQLRINGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLAL
Plakobranchus_ocellatus_GFO48356.1       --------------------------------------------------
                                                                                           

Drosophila_melanogaster_NP_523857.1      PERAELAASLGLTQTQVKIWFQNRRSKYKKMMKAAQGPGTN-SGMPLGGG
Owenia_fusiformis_CAH1775388.1           PERAELAASLGLTQTQVKIWFQNRRSKYKKIMKHNPNG-TI-SMSP----
Doryteuthis_pealeii_QVQ68771.1           PERAELAASLGLTQTQVKIWFQNRRSKYKKMMKQQQTN-PG-Q-------
Pinctada_fucata_ASY93124.1               PERAELAASLGLTQTQVKIWFQNRRSKAKKIMKQGGTP-PG---------
Nipponacmea_fuscoviridis_BBB36758.1      PERAELAASLGLTQTQVKIWFQNKRSKYKKVMKQNPNG-PP---------
Patelloida_mimula_UPN66625.1             --------------------------------------------------
Sepia_bandensis_QDF46136.1               PERAELAASLGLTQTQVKIWFQNRRSKYKKMMKQQQTN-PG-Q-------
Elysia_                                  PERAELAAALGLTQTQVKIWFQNRRSKYKKIMKQGGAP-PPSQ-------
Octopus_                                 PERA----------------------------------------------
Gigantopelta_                            PERAELAASLGLTQTQVKIWFQNRRSKYKKIMKHNPNG-PN---------
Biomphalaria_                            PERAELAASLGLTQTQVKIWFQNRRSKYKKIMKQGGTP-QS-Q-------
Haliotis_rubra_XP_046576763.1            PERAELAASLGLTQTQVKIWFQNRRSKYKKLMKQNPNS-TP---------
Haliotis_rufescens_XP_046337404.1        PERAELAASLGLTQTQVKIWFQNRRSKYKKLMKQNPNS-TP---------
Candidula_                               PERAELAASLGLTQTQVKIWFQNRRSKYKKIMKQGGPP-PT-Q-------
Cornu_aspersum_TRINITY_DN57644_c0_g1_i1  PERAELAASLGLTQTQVKIWFQNRRSKYKKIMKQGGPP-PT-Q-------
Elysia_chlorotica_RUS90064.1             PERAELAAALGLTQTQVKIWFQNRRSKYKKIMKQGGAP-PP---------
Plakobranchus_ocellatus_GFO48356.1       -------------------------------MKQGGAP-PPSQ-------
                                                                                           

Drosophila_melanogaster_NP_523857.1      GPNPGQHSPNQ--MHSGGNNGGGSNSGSPSHYLPPGHSPT-PSST-P---
Owenia_fusiformis_CAH1775388.1           -PHPGS-------------------------------GGN-PMSNGG---
Doryteuthis_pealeii_QVQ68771.1           -PQPQAQQPPS--Q-G-----H--------------TTPT-PQPQ-Q---
Pinctada_fucata_ASY93124.1               ---PNQQPPTP--V-T---------------------SPP-ANQQ-M---
Nipponacmea_fuscoviridis_BBB36758.1      ---P-PLTPQG--S-A---------------------SSP-PHGQ-Q---
Patelloida_mimula_UPN66625.1             --------------------------------------------------
Sepia_bandensis_QDF46136.1               -PQPQAQQPPS--Q-G-----H--------------TTPT-PQPQ-Q---
Elysia_                                  --PPCSQPPSH--Q-A---------------------SSS-PGAQ-HGPG
Octopus_                                 --------------------------------------------------
Gigantopelta_                            ---PAQSQNPH--Q-T---------------------SPQPPSQQ-Q---
Biomphalaria_                            ---PCSQPPSH--Q-G--------------------SASS-PPQQ-Q---
Haliotis_rubra_XP_046576763.1            ---PQPQQPQP--Q-T---------------------SPV-PQQQ-P---
Haliotis_rufescens_XP_046337404.1        ---PQPQQPQP--Q-T---------------------SPV-PQQQ-P---
Candidula_                               --APCSQTPVH--Q-G--------------------SAAS-PSLQ-Q---
Cornu_aspersum_TRINITY_DN57644_c0_g1_i1  --APCSQTPVH--Q-G--------------------SAGS-PSLQ-Q---
Elysia_chlorotica_RUS90064.1             --PPSSQPQSSSPG-G---------------------APT-PS-------
Plakobranchus_ocellatus_GFO48356.1       --APCSQPPSH--Q-A---------------------SSS-PGAQ-HGPG
                                                                                           

Drosophila_melanogaster_NP_523857.1      ---------V------SE--------LS--PEFP----PTGLSPPTQA--
Owenia_fusiformis_CAH1775388.1           ---------E--------------------PMTP---PPMSQPPQSVS--
Doryteuthis_pealeii_QVQ68771.1           ---------Q------QQ--------------------ATVQH-PTQ---
Pinctada_fucata_ASY93124.1               ---------Q------PP--------SS-----P----VQHSP-PTSNTH
Nipponacmea_fuscoviridis_BBB36758.1      --------------------------------------------------
Patelloida_mimula_UPN66625.1             --------------------------------------------------
Sepia_bandensis_QDF46136.1               --------------------------------------------------
Elysia_                                  GAPTPSLGG-V-----TVKQQPGSQNSSFLDDGPSTGNSSDMHPGSQG--
Octopus_                                 --------------------------------------------------
Gigantopelta_                            ---------Q------QQ--------QQ---QQPPQSQSADLPSPPQ---
Biomphalaria_                            ---------AM-----GIKQ----QQSSFLDDGP---PGSDMHPGSQG--
Haliotis_rubra_XP_046576763.1            ---------Q------PQ--------AQ-----P---QPAELP-PAQ---
Haliotis_rufescens_XP_046337404.1        ---------Q------PQ--------AQ-----P---QPAELP-PAQ---
Candidula_                               ---------QG-SMGVGIKQ----QQNSFLDEGP---PGGDMHPGSQG--
Cornu_aspersum_TRINITY_DN57644_c0_g1_i1  ---------QQGS-------------------------------------
Elysia_chlorotica_RUS90064.1             ------LGGVV-----NVKQQPGSQSNSFLDEGPPTGNSSDMHPGSQG--
Plakobranchus_ocellatus_GFO48356.1       GAPTPSLGN-V-----TVKQQPGSQGNSFLDDGPQSGSGSEMHPGSQG--
                                                                                           

Drosophila_melanogaster_NP_523857.1      PWDQKPH--W----------IDH---------------------------
Owenia_fusiformis_CAH1775388.1           PP--TPH--S--------QHNGQT--TVPGTVQTNNMMGQQ---------
Doryteuthis_pealeii_QVQ68771.1           PTT--PQ--Q-----NGP--APNGQQNSSLLPPASS-VSPP---------
Pinctada_fucata_ASY93124.1               AHT--PH--QQLPPNGLKMEAPEQ-QHNLMVSPSSS-ASPE---------
Nipponacmea_fuscoviridis_BBB36758.1      --------------------------------------------------
Patelloida_mimula_UPN66625.1             --------------------------------------------------
Sepia_bandensis_QDF46136.1               -----PQ--Q----------------------------------------
Elysia_                                  SPT--PQPHG-----GLQHPHPQG-TPTPMLPASSP-LSHHHH--PHHQ-
Octopus_                                 --------------------------------------------------
Gigantopelta_                            APT--PH--Q--------VSQPQA-PPQALLPVSSS-MSPQ---------
Biomphalaria_                            SPT--PQ--H-----GLQHPHPQG-TPTPLLPASSP-MSQQ---------
Haliotis_rubra_XP_046576763.1            PQT--PQ--Q-----SAAQGQGQGQQPQPLLPVSSS-MSPQ---------
Haliotis_rufescens_XP_046337404.1        PQT--PQ--Q-----SAAQGQGQGQQPQPLLPVSSS-MSPQ---------
Candidula_                               SPT--PQ--H-----GLQHPHPQG-TPTPMLSASSP-MSQQ---------
Cornu_aspersum_TRINITY_DN57644_c0_g1_i1  ----------------------------------------M---------
Elysia_chlorotica_RUS90064.1             SPT--PQPHG-----GIQHPGSQG-TPTPMLPASSP-LSHHHHHHQHHQH
Plakobranchus_ocellatus_GFO48356.1       SPT--PQPHG-----GLQHPHPQG-TPTPMLPASSP-LSHHHH--QHHQ-
                                                                                           

Drosophila_melanogaster_NP_523857.1      --------------------------------KPPPQMTPQPPHPAATLH
Owenia_fusiformis_CAH1775388.1           ------------------------------NVHQHPDDSVTPPSSWAEIH
Doryteuthis_pealeii_QVQ68771.1           -------------------------------------------PTWSELS
Pinctada_fucata_ASY93124.1               ------------------------------PE-----------NHWNDHM
Nipponacmea_fuscoviridis_BBB36758.1      --------------------------------------------------
Patelloida_mimula_UPN66625.1             --------------------------------------------------
Sepia_bandensis_QDF46136.1               --------------------------------------------------
Elysia_                                  -QQQH--HPHHTPHHPHSAAH-HQQGGAAGGV-----------LSWSDLG
Octopus_                                 --------------------------------------------------
Gigantopelta_                            ------------------------------PV-----------GSWSDIS
Biomphalaria_                            -----------------------------GNV-----------LSWSDLG
Haliotis_rubra_XP_046576763.1            ------------------------------PV-----------CTWSDLS
Haliotis_rufescens_XP_046337404.1        ------------------------------PV-----------CTWSDLS
Candidula_                               -----------------------------GSV-----------LSWSDLG
Cornu_aspersum_TRINITY_DN57644_c0_g1_i1  -----------------------------GVV------------------
Elysia_chlorotica_RUS90064.1             QQQQH----QQHQHHPHHSHHNNHQGGAAGGV-----------LSWSDLG
Plakobranchus_ocellatus_GFO48356.1       -QQHHSAHPHHNPHHPHSAAH-HPQGAGGGGV-----------LSWSDLG
                                                                                           

Drosophila_melanogaster_NP_523857.1      PQTHHHNP-PPQM----------------------------------GGY
Owenia_fusiformis_CAH1775388.1           SSAAHTPSMSMPP----------------------------------GNY
Doryteuthis_pealeii_QVQ68771.1           TTT-------PT-----------------------------------TSY
Pinctada_fucata_ASY93124.1               SGM-------TSS-H-HAHAS--------QPYMSMPSMPPSSSMMPSGMP
Nipponacmea_fuscoviridis_BBB36758.1      --------------------------------------------------
Patelloida_mimula_UPN66625.1             --------------------------------------------------
Sepia_bandensis_QDF46136.1               --------------------------------------------------
Elysia_                                  AAGG-----IPTSGHAHSHGGQHVHPHAHSVSS------AAAHQQIGNAY
Octopus_                                 --------------------------------------------------
Gigantopelta_                            NNN-------PST----------------------------------NSY
Biomphalaria_                            TGP-------TSG-HGHTHG----------QHH--------NHQQIGNAY
Haliotis_rubra_XP_046576763.1            NNN-------PST----------------------------------NSY
Haliotis_rufescens_XP_046337404.1        NNN-------PST----------------------------------NSY
Candidula_                               SNP-------NSG-HIHPHSH--------NQHH--------AQHQINSAY
Cornu_aspersum_TRINITY_DN57644_c0_g1_i1  --------------------------------------------------
Elysia_chlorotica_RUS90064.1             AAGG-----IPTSGH----------------------------------V
Plakobranchus_ocellatus_GFO48356.1       AAGG-----IPTSGQ---HGGQHGHPHAHSVSS-------AAHQQIGNAY
                                                                                           

Drosophila_melanogaster_NP_523857.1      --VPQY---WYQPE-TN-----PSLVTVWPAV-----
Owenia_fusiformis_CAH1775388.1           --MSQY--PWYSHT-AANPVQQQQILT----------
Doryteuthis_pealeii_QVQ68771.1           --MSPY--TWYSQQQNS--ISHQSLLT----------
Pinctada_fucata_ASY93124.1               --MSYYHSAWYSQP--M--VNQQSCLT----------
Nipponacmea_fuscoviridis_BBB36758.1      -------------------------------------
Patelloida_mimula_UPN66625.1             -------------------------------------
Sepia_bandensis_QDF46136.1               ----------------------ATV-Q----------
Elysia_                                  --MSHY-SSWYSQG-SL--PHQQSLLT----------
Octopus_                                 -------------------------------------
Gigantopelta_                            MSMSHY--SWYAQN-SM--VPQQPLIT---KTEVPGF
Biomphalaria_                            --MSHY-SSWYSQN-GI--PHQQSLLT----------
Haliotis_rubra_XP_046576763.1            MSMSHY--SWYAHN-NM--NSQQSLL----------T
Haliotis_rufescens_XP_046337404.1        MSMSHY--SWYAHN-NM--NSQQSLL----------T
Candidula_                               --MSHY-SSWYTQN-GL--PHQQSLLT----------
Cornu_aspersum_TRINITY_DN57644_c0_g1_i1  -------------------IKQ---------------
Elysia_chlorotica_RUS90064.1             --HSHG--GQHVHP-HA--HSVSSAAAHQ--------
Plakobranchus_ocellatus_GFO48356.1       --MSHY-SSWYSQG-SL--PHQQSLLT----------
                                                                              





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