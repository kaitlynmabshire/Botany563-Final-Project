#Multiple Sequence Alignment (02/24/2023)

Ran T-Coffee:
cd botany563/botany563-final-project
t_coffee dlx_protein.fasta

Output:
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
INPUT SEQUENCES: 16 SEQUENCES  [PROTEIN]
  Input File dlx_protein.fasta        Seq ADL14376.1               Length   80 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta        Seq ASY93124.1               Length  318 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta        Seq BBB36758.1               Length  178 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta        Seq CAG5114556.1             Length  305 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta        Seq CAH1775388.1             Length  298 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta        Seq CEK83647.1               Length  298 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta        Seq GFR70799.1               Length  267 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta        Seq NP_523857.1              Length  327 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta        Seq QDF46136.1               Length  221 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta        Seq QVQ68771.1               Length  333 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta        Seq TRINITY_DN57644_c0_g1_i1 Length  120 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta        Seq UPN66625.1               Length  126 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta        Seq XP_013063954.1           Length  292 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta        Seq XP_041371678.1           Length  295 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta        Seq XP_046337404.1           Length  285 type PROTEIN Struct Unchecked
  Input File dlx_protein.fasta        Seq XP_046576763.1           Length  285 type PROTEIN Struct Unchecked

	Multi Core Mode (read): 1 processor(s):

	--- Process Method/Library/Aln Sdlx_protein.fasta
	xxx Retrieved Sdlx_protein.fasta
	--- Process Method/Library/Aln Mproba_pair
	xxx Retrieved Mproba_pair

	All Methods Retrieved

MANUAL PENALTIES: gapopen=0 gapext=0

	Library Total Size: [145680]

Library Relaxation: Multi_proc [1]
 
!		[Relax Library][TOT=   16][100 %]

Relaxation Summary: [145680]--->[86607]



UN-WEIGHTED MODE: EVERY SEQUENCE WEIGHTS 1

MAKE GUIDE TREE 
	[MODE=nj][DONE]

PROGRESSIVE_ALIGNMENT [Tree Based]
Group    1: ADL14376.1
Group    2: ASY93124.1
Group    3: BBB36758.1
Group    4: CAG5114556.1
Group    5: CAH1775388.1
Group    6: CEK83647.1
Group    7: GFR70799.1
Group    8: NP_523857.1
Group    9: QDF46136.1
Group   10: QVQ68771.1
Group   11: TRINITY_DN57644_c0_g1_i1
Group   12: UPN66625.1
Group   13: XP_013063954.1
Group   14: XP_041371678.1
Group   15: XP_046337404.1
Group   16: XP_046576763.1

#Single Thread

	Group   17: [Group   11 (   1 seq)] with [Group    4 (   1 seq)]-->[Len=  306][PID:40316]
	Group   18: [Group   13 (   1 seq)] with [Group    7 (   1 seq)]-->[Len=  359][PID:40316]
	Group   19: [Group   18 (   2 seq)] with [Group   17 (   2 seq)]-->[Len=  400][PID:40316]
	Group   20: [Group   10 (   1 seq)] with [Group    9 (   1 seq)]-->[Len=  333][PID:40316]
	Group   21: [Group   20 (   2 seq)] with [Group    1 (   1 seq)]-->[Len=  333][PID:40316]
	Group   22: [Group   12 (   1 seq)] with [Group    3 (   1 seq)]-->[Len=  201][PID:40316]
	Group   23: [Group   16 (   1 seq)] with [Group   15 (   1 seq)]-->[Len=  285][PID:40316]
	Group   24: [Group   23 (   2 seq)] with [Group   14 (   1 seq)]-->[Len=  301][PID:40316]
	Group   25: [Group   24 (   3 seq)] with [Group   22 (   2 seq)]-->[Len=  305][PID:40316]
	Group   26: [Group   25 (   5 seq)] with [Group   21 (   3 seq)]-->[Len=  361][PID:40316]
	Group   27: [Group    2 (   1 seq)] with [Group   26 (   8 seq)]-->[Len=  396][PID:40316]
	Group   28: [Group    5 (   1 seq)] with [Group   27 (   9 seq)]-->[Len=  413][PID:40316]
	Group   29: [Group   28 (  10 seq)] with [Group   19 (   4 seq)]-->[Len=  525][PID:40316]
	Group   30: [Group    8 (   1 seq)] with [Group   29 (  14 seq)]-->[Len=  585][PID:40316]
	Group   31: [Group    6 (   1 seq)] with [Group   30 (  15 seq)]-->[Len=  671][PID:40316]


!		[Final Evaluation][TOT=  335][100 %]

CLUSTAL FORMAT for T-COFFEE Version_13.45.0.4846264 [http://www.tcoffee.org] [MODE:  ], CPU=0.00 sec, SCORE=843, Nseq=16, Len=671 

NP_523857.1               -------------------------------------------MDAPDAP
CAH1775388.1              -------------------------------------------ML-----
QVQ68771.1                DTVDLSTLLVRICYSRFTSGLSVSLPSTFIRKLPIINRKTGPMML-----
ASY93124.1                -------------------------------------------ML-----
BBB36758.1                --------------------------------------------------
UPN66625.1                -------------------------------------------ML-----
QDF46136.1                -------------------------------------------ML-----
GFR70799.1                --------------------------------------------------
ADL14376.1                --------------------------------------------------
XP_041371678.1            -------------------------------------------ML-----
XP_013063954.1            -------------------------------------------M------
XP_046576763.1            -------------------------------------------ML-----
XP_046337404.1            -------------------------------------------ML-----
CEK83647.1                -------------------------------------------ML-----
CAG5114556.1              -------------------------------------------M------
TRINITY_DN57644_c0_g1_i1  --------------------------------------------------
                                                                            

NP_523857.1               HTPKYMDGGNTAAS---------------------------------V-T
CAH1775388.1              ---------NMTGS----------------------------------EA
QVQ68771.1                ---------NIAGS---------------------------------VDG
ASY93124.1                ---------NV-GS---------------------------------VEG
BBB36758.1                --------------------------------------------------
UPN66625.1                ---------NMTSN---------------------------------MDG
QDF46136.1                ---------NIAGS---------------------------------VDG
GFR70799.1                --------------------------------------------------
ADL14376.1                --------------------------------------------------
XP_041371678.1            ---------NMTGP---------------------------------MDG
XP_013063954.1            --------------------------------------------------
XP_046576763.1            ---------NMAGA---------------------------------MDG
XP_046337404.1            ---------NMAGA---------------------------------MDG
CEK83647.1                ---------DYRNNIGNDSPQNGYRGQGHHHHQSHHISATESNNGTCSNG
CAG5114556.1              ------------------------------------------------DG
TRINITY_DN57644_c0_g1_i1  --------------------------------------------------
                                                                            

NP_523857.1               PGINIP-GKSAFVELQQH---AAAGYG-----GIRSTYQHFGP-QG-GQ-
CAH1775388.1              IGQDIPDSKSAFMEIQQM----QQNMGHHAAYPIRASYP---S-QH-PS-
QVQ68771.1                LDQDVT-GKSAFMELQQQP--MPPGMA-HPAYPIRSSYP---T-HQ-SQ-
ASY93124.1                MEQEMA-GKSAFMELQQS---GGMPMG-HPAYPMRSSYQ---PPHHGGQ-
BBB36758.1                --------------LQQQS--MAGGMG-HPAYNIRSGYP---T-QH-SQ-
UPN66625.1                MDPEIA-SKSAFMELQQQS--MTGGMG-HPAYNIPSGYP---R-QH-SQ-
QDF46136.1                LDQDVT-GKSAFMELQQQP--MPPGMA-HPAYPIRSSYP---T-HQ-SQ-
GFR70799.1                --------------------------------------------------
ADL14376.1                --------------------------------------------------
XP_041371678.1            LDQEMV-GKSAFMELQQQ---MPPGMG-HPAYQIRTGYP---P-QH-GH-
XP_013063954.1            --------------------------G-SP---VRTVSH---D-AH-P-H
XP_046576763.1            LEQEMV-GKSAFMELQQQ---MPPSMG-HPAYPIRSGYP---P-QH-SQ-
XP_046337404.1            LEQEMV-GKSAFMELQQQ---MPPSMG-HPAYPIRSGYP---P-QH-SQ-
CEK83647.1                GASETV-ASILSLSHKNG---IQNSRQ-HSTFVLNS--P---P-LA-AL-
CAG5114556.1              LEQDMMKQQSAFMELQQQTGGLAHSMGHHPAYQIRPQYP---G-AH-PQH
TRINITY_DN57644_c0_g1_i1  --------------------------------------------------
                                                                            

NP_523857.1               ---D-S-G-FPS--PRSAL-GYPFPPMHQNSYSGYH--------------
CAH1775388.1              ---Q-DSM-Y-TSQATRPL-GYPFS-MNGMSHTAYNS--PS---------
QVQ68771.1                ---H-ENV-FSTAQHTRPF-TYPFA-MNTMSATTYNP--PT---------
ASY93124.1                ---HGESV-FSNPQGRGPLAGYPFH-MNAMSPTAYNP--SS--------G
BBB36758.1                ---H-D-M-FPTSQHTRSF-GYPFP-MNSMAPSGYNAVPPS---------
UPN66625.1                ---H-E-M-FPTSQHTRXF-GYPFS-MNSMAPSGYNAVPPS---------
QDF46136.1                ---H-ENV-FSTAQHTRPF-TYPFA-MNTMSATTYNP--PT---------
GFR70799.1                --------------------------------------------------
ADL14376.1                --------------------------------TRDNP--PT---------
XP_041371678.1            ---H-D-GSY-TSQATRSL-GYPFS-MNSMAPTSYNP--PP---------
XP_013063954.1            ---E-S-L-VKT-DLPRFT-CHVFR-LQYNLYTSII---DD---------
XP_046576763.1            ---H-D-V-F-TSQPTRPL-AYPFP-MNSMAPTSYNP--PT--------S
XP_046337404.1            ---H-D-V-F-TSQPTRPL-AYPFP-MNSMAPTSYNP--PT--------S
CEK83647.1                ---H-N---------LTEM-KFPSS-SSSFLSQDYSP--DTLKQMQAAMS
CAG5114556.1              HQPH-D-V-FSSQQHGRMP-S-----------------------------
TRINITY_DN57644_c0_g1_i1  --------------------------------------------------
                                                                            

NP_523857.1               ----L---------------------------------------------
CAH1775388.1              H-F-V---------------------------------------------
QVQ68771.1                HAFSV---------------------------------------------
ASY93124.1                HHFSM---------------------------------------------
BBB36758.1                HHFPM---------------------------------------------
UPN66625.1                HHFPM---------------------------------------------
QDF46136.1                HAFSV---------------------------------------------
GFR70799.1                --------------------------------------------------
ADL14376.1                HPFSV---------------------------------------------
XP_041371678.1            PHFSM---------------------------------------------
XP_013063954.1            HPFVT--------------R----------------------LTNC----
XP_046576763.1            HPFSM---------------------------------------------
XP_046337404.1            HPFSM---------------------------------------------
CEK83647.1                HALSTPHGISDILSRPHATFGLPRLDSGMYLGHQTRFPKLAELPGRQPIY
CAG5114556.1              HPFSV---------------------------------------------
TRINITY_DN57644_c0_g1_i1  --------------------------------------------------
                                                                            

NP_523857.1               ------GSYAPPCASP---------PKD--------DFSISDKCEDSGLR
CAH1775388.1              ------NPYQ--ASCP---------PRD--------DKSP----IEEQLR
QVQ68771.1                ------TPYQ--TTSP---------TREGCTFYFPTEKTQ----MEEQLR
ASY93124.1                ------PPYQ--SPSP---------TRD--------DKSQ----MD-ELR
BBB36758.1                ------SPYQ--PPSP---------TRD--------DKSQ----VEEQLR
UPN66625.1                ------SPYQ--PPSP---------TRD--------DKSQ----VEEQLR
QDF46136.1                ------TPYQ--TTSP---------TREGCTFYFPTEKSQ----MEEQLR
GFR70799.1                --------------------------------------------------
ADL14376.1                ------TPYQ--TTSP---------TREGYTFYFPTEKSQ----MEEQLR
XP_041371678.1            ------SPYQ--TPSP---------PRD--------DKSQ----VEEQLR
XP_013063954.1            -----DEDYK--SVLPGQRIRDRVWHQQ--------HKGQ----VEEQLR
XP_046576763.1            ------SPYQ--TPSP---------PRD--------EKPQ----MDDQLR
XP_046337404.1            ------SPYQ--TPSP---------PRD--------EKPQ----MDDQLR
CEK83647.1                WPGALAEPWR--SSDS---------CQR--------YGSQ-----SSPVV
CAG5114556.1              ------SPYQ--TPSP---------PRD--------DKSQ----VEEQLR
TRINITY_DN57644_c0_g1_i1  -------------------------PRD--------DKSQ----VEEQLR
                                                                            

NP_523857.1               VNGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLALPERAELAASLGLTQT
CAH1775388.1              VNGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLALPERAELAASLGLTQT
QVQ68771.1                INGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLALPERAELAASLGLTQT
ASY93124.1                INGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLALPERAELAASLGLTQT
BBB36758.1                INGKGKKLRKPRTIYSSLQLQQLNRRFQRTQYLALPERAELAASLGLTQT
UPN66625.1                INGKGKKLRKPRTIYSS---------------------------------
QDF46136.1                INGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLALPERAELAASLGLTQT
GFR70799.1                -------MRKPRTIYSSLQLQQLNRRFQRTQYLALPERAELAAALGLTQT
ADL14376.1                MNGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLALPERA-----------
XP_041371678.1            INGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLALPERAELAASLGLTQT
XP_013063954.1            INGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLALPERAELAASLGLTQT
XP_046576763.1            INGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLALPERAELAASLGLTQT
XP_046337404.1            INGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLALPERAELAASLGLTQT
CEK83647.1                VDKDGKK-KHTRPTFSGQQIFALEKTFEQTKYLAGPERARLAYALGMSES
CAG5114556.1              INGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLALPERAELAASLGLTQT
TRINITY_DN57644_c0_g1_i1  INGKGKKMRKPRTIYSSLQLQQLNRRFQRTQYLALPERAELAASLGLTQT
                                  ::.*. :*.                                 

NP_523857.1               QVKIWFQNRRSKYKKMMKAAQGPGTNSGMPLGGGGPNPGQHSPNQMHSGG
CAH1775388.1              QVKIWFQNRRSKYKKIMKHNPNGTI--------------SMSP-------
QVQ68771.1                QVKIWFQNRRSKYKKMMKQQQTNPG-QPQP--------QAQQP-------
ASY93124.1                QVKIWFQNRRSKAKKIMKQGGTPPG--P----------NQQPP-------
BBB36758.1                QVKIWFQNKRSKYKKVMKQNPNGPP--P-----------PLTP-------
UPN66625.1                --------------------------------------------------
QDF46136.1                QVKIWFQNRRSKYKKMMKQQQTNPG-QPQP--------QAQQP-------
GFR70799.1                QVKIWFQNRRSKYKKIMKQGGAPPP-SQPP--------CSQPP-------
ADL14376.1                --------------------------------------------------
XP_041371678.1            QVKIWFQNRRSKYKKIMKHNPNGPN--P-A--------QSQNP-------
XP_013063954.1            QVKIWFQNRRSKYKKIMKQGGTP-Q-SQ-P--------CSQPP-------
XP_046576763.1            QVKIWFQNRRSKYKKLMKQNPNSTP--P----------QPQQP-------
XP_046337404.1            QVKIWFQNRRSKYKKLMKQNPNSTP--P----------QPQQP-------
CEK83647.1                QVKVWFQNRRTKWRKKHAAEMATAK--K-K--------QEQAE-------
CAG5114556.1              QVKIWFQNRRSKYKKIMKQGGPP-P-TQAP--------CSQTP-------
TRINITY_DN57644_c0_g1_i1  QVKIWFQNRRSKYKKIMKQGGPP-P-TQAP--------CSQTP-------
                                                                            

NP_523857.1               NNGGGSNSGSPSHYLPPGHSPT--PSSTPVS-EL--SP------------
CAH1775388.1              PHPGS---------------GGN-PMSNGGE-PM--TP---PPM------
QVQ68771.1                PSQGH---------------TTPTPQPQQQQ-Q---------AT------
ASY93124.1                TPVTS---------------PP--ANQQMQP-PS--SP---VQH------
BBB36758.1                QGSAS---------------SP--PHGQQ---------------------
UPN66625.1                --------------------------------------------------
QDF46136.1                PSQGH---------------TTPTPQPQQPQ-Q---------AT------
GFR70799.1                SHQAS---------------SSP-G-AQHGP-GG--AP---TPSLGGVTV
ADL14376.1                --------------------------------------------------
XP_041371678.1            -HQTS---------------PQP-PSQQQQQ-QQQQQPPQSQSA------
XP_013063954.1            SHQGS---------------ASS-P-PQQQA----------------MGI
XP_046576763.1            QPQTS---------------PV--PQQQPQP-QA--QP---QPA------
XP_046337404.1            QPQTS---------------PV--PQQQPQP-QA--QP---QPA------
CEK83647.1                DMDDN---------------SE--PEDE----------------------
CAG5114556.1              VHQGS---------------AAS-PSLQQQG-S------------MGVGI
TRINITY_DN57644_c0_g1_i1  VHQGS---------------AGS-PSLQQQQGS------------MG---
                                                                            

NP_523857.1               ----------E---FPPT----GLSPP-TQAPWDQKPHW-----ID----
CAH1775388.1              ----------S---QPPQ-------S--V-SPP--TPHSQHNGQTTVPGT
QVQ68771.1                ----------V---QH---------P--T-QPT--TPQQ-----NG----
ASY93124.1                ----------S---PP---------TSNT-HAH--TPHQQLPPNGL----
BBB36758.1                --------------------------------------------------
UPN66625.1                --------------------------------------------------
QDF46136.1                ----------V---------------------------------------
GFR70799.1                KQQPGSQNSSFLDDGPSTGNSSDMHPG-SQGSP--TPQPH---GGL----
ADL14376.1                --------------------------------------------------
XP_041371678.1            ----------D---LP-S-------P--P-QAP--TPHQ-----------
XP_013063954.1            KQ----QQSSFLDDGPPG---SDMHPG-SQGSP--TPQ-----HGL----
XP_046576763.1            ----------E---LP---------P--A-QPQ--TPQQ-----SA----
XP_046337404.1            ----------E---LP---------P--A-QPQ--TPQQ-----SA----
CEK83647.1                --------------------------------------------------
CAG5114556.1              KQ----QQNSFLDEGPPG---GDMHPG-SQGSP--TPQ-----HGL----
TRINITY_DN57644_c0_g1_i1  --------------------------------------------------
                                                                            

NP_523857.1               -HKPPPQM-TPQPPHPAA--------------------------------
CAH1775388.1              VQTNNMMGQQN-VHQHPDDSVT----------------------------
QVQ68771.1                ---PAPNGQQNSSLLPPASSVSPP--------------------------
ASY93124.1                -KMEAPEQ-QHNLMVSPSSSASPE--------------------------
BBB36758.1                --------------------------------------------------
UPN66625.1                --------------------------------------------------
QDF46136.1                --------------------------------------------------
GFR70799.1                -QHPHPQG-TPTPMLPASSPLSHHHHPHHQQQQHHPHHTPHHPHSAAHHQ
ADL14376.1                --------------------------------------------------
XP_041371678.1            --VSQPQA-PPQALLPVSSSMSPQ--------------------------
XP_013063954.1            -QHPHPQG-TPTPLLPASSPMSQQ--------------------------
XP_046576763.1            -AQGQGQGQQPQPLLPVSSSMSPQ--------------------------
XP_046337404.1            -AQGQGQGQQPQPLLPVSSSMSPQ--------------------------
CEK83647.1                --------------------------------------------------
CAG5114556.1              -QHPHPQG-TPTPMLSASSPMSQQ--------------------------
TRINITY_DN57644_c0_g1_i1  --------------------------------------------------
                                                                            

NP_523857.1               ------------TLHPQT--H------------------HH---------
CAH1775388.1              ------PPSSWAEIHSS--AAHTPSMSMP---------------------
QVQ68771.1                ------P--TWSELSTT--TP-------T---------------------
ASY93124.1                ------PENHWNDHMSG--MT-------S---------------------
BBB36758.1                --------------------------------------------------
UPN66625.1                --------------------------------------------------
QDF46136.1                --------------------------------------------------
GFR70799.1                QGGAAGGVLSWSDLGAAGGIPT------SGHAHSHG--GQHVHPHAHSVS
ADL14376.1                --------------------------------------------------
XP_041371678.1            ------PVGSWSDISNN--NP-------S---------------------
XP_013063954.1            -----GNVLSWSDLGTG---PT------SGHGHTHG--QHH---------
XP_046576763.1            ------PVCTWSDLSNN--NP-------S---------------------
XP_046337404.1            ------PVCTWSDLSNN--NP-------S---------------------
CEK83647.1                -------------NSDQ---N-------L---------------------
CAG5114556.1              -----GSVLSWSDLGSN---PN------SGHIHPHSHNQHH---------
TRINITY_DN57644_c0_g1_i1  --------------------------------------------------
                                                                            

NP_523857.1               ---NPPPQMG------GY------------------VPQY---WYQPE-T
CAH1775388.1              --------PG------NY------------------MSQY--PWYSHT-A
QVQ68771.1                ---------T------SY------------------MSPY--TWYSQQQN
ASY93124.1                --------SHHAHASQPYMSMPSMPPSSSMMPSGMPMSYYHSAWYSQP--
BBB36758.1                --------------------------------------------------
UPN66625.1                --------------------------------------------------
QDF46136.1                --------------------------------------------------
GFR70799.1                SAAAHQQIGN------AY------------------MSHY-SSWYSQG-S
ADL14376.1                --------------------------------------------------
XP_041371678.1            --------TN------SYM----------------SMSHY--SWYAQN-S
XP_013063954.1            ---NHQQIGN------AY------------------MSHY-SSWYSQN-G
XP_046576763.1            --------TN------SYM----------------SMSHY--SWYAHN-N
XP_046337404.1            --------TN------SYM----------------SMSHY--SWYAHN-N
CEK83647.1                --------KA------DY------------------LSSV--DFN-----
CAG5114556.1              ---AQHQINS------AY------------------MSHY-SSWYTQN-G
TRINITY_DN57644_c0_g1_i1  --------------------------------------------------
                                                                            

NP_523857.1               N-----PSLVTVWPAV-----
CAH1775388.1              ANPVQQQQILT----------
QVQ68771.1                S--ISHQSLLT----------
ASY93124.1                M--VNQQSCLT----------
BBB36758.1                ---------------------
UPN66625.1                ---------------------
QDF46136.1                ----------Q----------
GFR70799.1                L--PHQQSLLT----------
ADL14376.1                ---------------------
XP_041371678.1            M--VPQQPLIT---KTEVPGF
XP_013063954.1            I--PHQQSLLT----------
XP_046576763.1            M--NSQQSLLT----------
XP_046337404.1            M--NSQQSLLT----------
CEK83647.1                ---------------------
CAG5114556.1              L--PHQQSLLT----------
TRINITY_DN57644_c0_g1_i1  V--VIKQ--------------
                                               





OUTPUT RESULTS
	#### File Type= GUIDE_TREE      Format= newick          Name= dlx_protein.dnd
	#### File Type= MSA             Format= aln             Name= dlx_protein.aln
	#### File Type= MSA             Format= html            Name= dlx_protein.html

# Command Line: t_coffee dlx_protein.fasta  [PROGRAM:T-COFFEE]
# T-COFFEE Memory Usage: Current= 37.363 Mb, Max= 40.549 Mb
# Results Produced with T-COFFEE Version_13.45.0.4846264 (Version_13.45.0.4846264)
# T-COFFEE is available from http://www.tcoffee.org
# Register on: https://groups.google.com/group/tcoffee/

Ran Muscle:
~/Dropbox/software/muscle3.8.31_i86darwin64 -in dlx_protein.fasta -out muscle_aligned_dlx_protein.fasta

Output:
MUSCLE v3.8.31 by Robert C. Edgar

http://www.drive5.com/muscle
This software is donated to the public domain.
Please cite: Edgar, R.C. Nucleic Acids Res 32(5), 1792-97.

dlx_protein 16 seqs, max length 333, avg  length 251
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
00:00:00      6 MB(0%)  Iter   6  100.00%  Refine biparts
00:00:00      6 MB(0%)  Iter   7  100.00%  Refine biparts
00:00:00      6 MB(0%)  Iter   7  100.00%  Refine biparts

