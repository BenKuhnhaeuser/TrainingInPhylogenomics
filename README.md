# Documentation for training in phylogenomics
 
**Please note - this document is under development and only contains  outlines of sections being prepared**

This repository aims to serve as a starting point for learning how to perform various phylogenomic analyses. The focus is on the estimation of species trees for angiosperm plants (but the methods can be used for other organisms).


The documentation is structured as follows:
* Some [background](#Background) to these analyses
* a [workflow outline](#Workflow-outline) and analysis of the outputs obtained. Includes links to existing tutorials, including ones compiled by people at Kew
* [brief introductions to some computing subjects](#Computing-requirements-and-software) with links to existing tutorials, including those compiled by people at Kew, and how to run analysis software
* [Skeleton workflow of useful commands](#Skeleton-workflow-of-useful-commands)


If you would like to [contribute](#Guide-to-contributors) content to this repository please contact an existing contributor at RGB Kew.

***

## Background
[ Proposed content topics (very short paragraph on each topic)]:
* Why build trees with sequence data?
  * What does it tell you that taxonomy can't?
* Discuss models of evolution and tree building algorithms
  * Discuss Jukes Cantor, Kimura, F84 and REV models; model testing
  * Discuss different types of tree method: distance matrix, parsimony, maximum likelihood and Bayesian analysis - this document discusses macimum likelihood only.
* Discuss what sequences are required for the analysis: 
  * requirement for orthologous loci
  * NGS techniques - e.g.'s:
    * RAD-Seq
    * target capture of gene regions
      * mention baits and enrichment  - requirement of short ( e.g 120bp) bait seqs designed against a subset of target genes selected from the genome
      * Various methods but recommend HybPiper (Johnson et al)
      * Requires a bait kit for enrichment and reference target sequences (Angios353)
      * Mention skimming is possible
      * Mention MEGA353 and family-specific kits
* Brief discussion of data mining - enables analysis of new data to fit into context of existing data. Example data sources: OneKP, SRA, PAFTOL, Earth biogenomes, Darwin, 10KP etc - links to all large projects
* Annotating trees with taxonomy and other data sets
  * WCVP
  * Angiosperms353 - or section on existing tree resources incl Explorer
]
* Performing the analysis - are there any online tools for estimating a species tree?

### References
* A recent review paper on phylogenomics
* Johnson et al target capture paper and Angios353 paper

### Courses
* Courses in [Evolution and genomics](https://evomics.org/), Český Krumlov, Czech Republic
* [Phylogenomics and Population Genomics: Inference and Applications](https://www.ub.edu/certfem/ppgcourse/), University of Barcelona - two week course, yearly
***

## Workflow outline for estimating a species tree
This workflow is discussed briefly in six sections below but consists of two major steps:
* **step 1:** assembly of gene sequences from samples
* **step 2** organising sequences into gene sets, aligning the genes and  using the alignments to estimate a species tree

It is assumed that target capture data is being used and available in the form of Illumina short pair end reads in [fastq format](https://en.wikipedia.org/wiki/FASTQ_format). At the end of this section, there are links to existing more detailed documentation on how to run the programs. Following this section there are some details on computing requirements and a section that summarises the commands required for a complete analysis.

### Sequencing data quality checks
* Adaptor trimming
* Quality trimming
* Trimmomatic tool
* FASTQC

**_Outputs_**     (and **_Interpretation_**)
* Trimmomatic output - expected % retained pair end and single end reads; single can also be used in HybPiper (can be 7% of total reads).
* 
**_Go further_**
  
### Choice of sample and gene name
Some thought needs to be given to sample and gene names/identifiers before starting the analysis. It is also good to understand how these identifiers are used during the analysis. HybPiper has a novel (?) convention of using the following format for the fasta header in the reference fasta targets file:
```
>SampleName-GeneName
```
with a dash between the sample and gene names. It is best that names should consist of alphanumerical characters only(1 - 9, A -Z, a - z) and underscore characters if required but certainly no dash characters or spaces. It is recommend ...
REWORK THIS
* The sample names should be simple alphanumerical identifiers during the analysis. Meanwhile a mapping file can be prepared to allow the species names to be swapped with the identifier
### 
### Gene recovery from samples
* HybPiper
* Organising sequences into gene sets
* Output DNA sequences should be in frame

**_Outputs_**    (and **_Interpretation_**)

**_Go further_**
* Captus software (?)

### Alignment of genes from samples
Intro - Various easy to use alignment programs exist - recommended ones: MAFFT, UPP for large alignments

**_Outputs_** (and **_Interpretation_**)
* Assessment: AMAS summary
* Filtering tools: AMAS, Trimal
* Removal of long branches with TreeShrink

**_Go further_**
* Concatenation --> species tree (also see two sections below)
* DNA aligned by protein sequence
* Rogue taxon programs

###  Estimating gene trees
Intro:
* Various easy to use maximum likelihood tree programs exist - recommended ones (in order of speed): FastTree, IQTREE, RAxML
    * recommended program options e.g. IQTREE Ultrafastbootstrap
* Virtues of each one: speed, ease of use, documentation

**_Outputs_** (and **_Interpretation_**)
* Newick file format and manipulation of
* Assessment: support values
* Adding taxonomy and visualisation

**_Go further_**

### Estimating the species tree
Intro - choice of program: ASTRAL

**_Outputs_** and **_Interpretation_**
  * Assessment of support values e.g. what do the pp1 scores mean? explain roots - trees are unrooted; Recommended value of confidence = >0.95 (ref)
	Normalised quartet score
  * Visualisation

**_Go further_**

* e.g. concatenation; partitioning data with with RAxL-NG; not as robust a method to ILS as ASTRAL summary method but gives you real branch lengths which might be of interest e.g. long branches that coincide with particular taxonomic levels (or not!) 
* intro to incongruence
* other programs to investigate e.g. ASTRAL-MP, ASTRAL-Pro
* Tanglegrams

### Detailed workflows online
The following links to tutorials and workflows go into further details about processing read data and estimating trees. Some additional computing knowledge required and is discussed in the next section.

* A practical [workflow by Sidonie Bellot](https://github.com/sidonieB/Workflows) - details include:
  * overview of target capture (bait design and making DNA libraries)
  * data quality checks and cleaning
  * use of HybPiper (version 1.3) and tips on running the program plus information on: 
    * formatting reference targets
    * gene assembly strategy 
  * multiple sequence alignment, estimating gene trees 
  * estimating he species tree with ASTRAL-III
  
* [PhyloFrame](https://github.com/BenKuhnhaeuser/PhyloFrame) by Ben Kuhnhäuser - short list of relevant commands covering the same areas as Sidonie's workflow above
* [Training and bioinformatics resources](https://www.genomicsforaustralianplants.com/gap-bioinformatics-resources/) from the [GAP phylogenomics project](https://www.genomicsforaustralianplants.com/phylogenomics)
  * links to their phylogenomic workflows
  * links to a file contaiing recommendations for data analysis to estimate a species tree
  * links to their bioinformatics webinars and workshops (with materials to try out)

* [Kew internal training course in phylogenomics (November 2019)](https://github.com/baileyp1/PhylogenomicsTraining_Nov2019)
  * teaches the steps required to estimate a species tree
  * includes summary of basic Linux commands, data transfer to and from computers, example of running analsyses with the Slurm job scheduler
  
* PAFTOL Explorer workflow 

### References
*** 

## Computing requirements and software
It is very likely that phylogenomic analysis will require use of high performance computing (HPC) due to the hundreds of genes used, unless the number of samples being compared is very small e.g. under 20). Therefore some computing expertise for HPC is required.

The links below will get you started on various topics that will also enable you to get started with bioinformatics analyses in general. 
* [Kew Bioinformatics documentation](https://rbg-kew-bioinformatics-utils.readthedocs.io/en/latest/)
  * includes information on getting connected to the KewHPC cluster
  * provides brief instructions on installing or setting up software
  * contains an overview of running analyses via the Slurm job scheduler
  

* [Crop Diversity HPC documentation](https://help.cropdiversity.ac.uk/index.html)
  * Kew employees can work on this cluster too
  * includes information on getting connected 
  * links to a Linux command line tutorial
  * installation of software is done via Bioconda (easy setup instructions provided)
  * Good overview of how to run your analysis via the Slurm job scheduler
  * Maximum number of cpu's per user is limited to 256 (@March 2024)

* [Course materials](https://github.com/prog4biol) from [Programming for Biology](https://programmingforbiology.org/), Cold Spring Harbour
  * comprehensive introductions to Unix, Git and Python

* A short Linux command line and Slurm primer from the course [Methodological Advances in Reticulate Evolution](https://gtiley.github.io/RBG-Networks/activities/introduction/) (held at RGBKew, November 2023). Includes introduction to writing scripts in Bash, Python and Perl.

### Courses
* [https://bioinfotraining.bio.cam.ac.uk/](Bioinformatics Training at University of Cambridge):
  * Link to courses: https://bioinfotraining.bio.cam.ac.uk/
  * [Upcoming courses](https://training.cam.ac.uk/bioinformatics/event-timetable)
  * [Introduction to Phylogenetics](https://training.cam.ac.uk/bioinformatics/course/bioinfo-phylng)


The rest of this section summarizes useful commands for the following  computing topics:

* [Linux command line](#Linux-command-line)
* [Slurm job scheduler](#Slurm-job-scheduler)
* [Installing software](#Installing-software)
* [Python](#Python)
* [Jupyter notebook](#Jupyter-notebook)
* [Java](#Java)
* [R](#R)
* [GitHub](#GitHub)

### Linux command line
* Minimum commands - minimum commands required to take control of the command line
* Link to one or two more primers

### Slurm

* https://github.com/sidonieB/Workflows/blob/main/Slurm_cheat_sheet.md

* Example command for:
* sbatch
* sbatch -J jobName -p long -c 1 -n 1  --mem=5000  -o jobName.log  -e jobName.err  --wrap  " [ cmd here - need to backslash these chars: `, ", $ ] " 
**_sinfo_**
```
sinfo -o "%16P %.5a %.10l %8p %.6D %.6t %N %m"
```


watch 'squeue -o "%.22i %.13P %.25j %.8u %.8T %.10M %.9l %.6D %.R %.C %.m %.p" ' --> can't make into an alias! mysqueue  # watch -n 20 - updates every 20 secs
squeue -u $USER -o "%.22i %.13P %.25j %.8u %.8T %.10M %.9l %.6D %.R %.C %.m %.p" --> now an alias: mysqueue
squeue -o "%.22i %.13P %.25j %.8u %.8T %.10M %.9l %.6D %.R %.C %.m %.p" | grep RUNNING | awk '{sum+=$10} END {print sum}'
scontrol update arraytaskthrottle=1 job=133452
scontrol update NumCPUs=25  job=8368    	       - to update the number of cpus
scontrol update MinMemoryNode=250000  job=8368    - to change RAM (MB)
scontrol update TimeLimit=UNLIMITED  job=8368    - to change time limit: 2-00:00:00, UNLIMITED.    
	Other variables: Partition
sacct -S 093023-09:00 --format=jobid,jobname%-25,start%16,end%16,Partition%13,elapsed,cputime,ncpus%3,ntasks%4=3,NodeList,AveVMSize,MaxRss%12,user%7,state,ExitCode | grep batch | grep [jobId]1226030\|1227326 | sort -k11n [for sorted RAM]	For sorting time taken column to get a median value: | sort -k5 (no n)
srun --cpus-per-task=1 --mem-per-cpu=2G --partition=himem --nodelist=n21-64-2048-buck --pty bash   # With --nodelist, logs into a specific node for checking running jobs,
												    # otherwise a node will be assigned for working on the command line	 

### Installing software
* Organising software 
* Installers 
* Conda
  * Installing HybPiper2 on a bad day (connection slow and dropping)

### Python
* Running a Python script - if you hzve to run a script with python in front

### Jupiter notebook

### Java
 * Java versions and JRE/JDE 
 * Running a Java script - setting memory 
 * 
### R

### GitHub

***

## Skeleton workflow summary
This section is a very concise summary of the commands required for a complete analysis. It takes the example data set from HybPiper and works through read preparation, HybPiper gene recovery, gene alignment with MAFFT, gene tree estimation with IQTREE2 and ASTRAL tree for estimating the species tree.

under the same heading as in the Workflow outline provided above.

* Suggest to follow HybPiper2 tutorial
* then detail from the gene alignment step
    [yet to outline]


## Contributors
* Paul Bailey
* Sidonie Bellot
* Ben Kuhnhaeuser

## Guide to contributors
* Need to think how the document(s) can be modified. Is it best to transfer agreed tracked changes from e.g. a Google doc?
  * Can edit online and leave a commit message with your name - there's even an extended message box to leave further info
* The idea is the the content should be very succinct and to the point
* Maybe contributors should meet occasionally to assess structure and agree new content
* If the document grows significantly or new topics are included, could break out into several files
* Might be good to relay experiences we have had w.r.t. some statistics, values that might be hard to find from reading tutorials and literature e.;g. maximum expected gene recovery form a sample in base pairs with Angiosperms353 reference targets (±260kbp); guide for amount of cpu and memory to use
* Open door sessions (?)







---
<span style="font-size:small;">Copyright © 2024 The Board of Trustees of the Royal Botanic Gardens, Kew</span>



