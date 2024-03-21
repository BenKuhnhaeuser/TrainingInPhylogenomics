# Documentation for training in phylogenomics
 
**Please note - this document is under development and only contains  outlines of the sections being prepared**

This repository aims to serve as a starting point for learning how to perform various phylogenomic analyses. The focus is on the estimation of species trees for angiosperm plants (but the methods can be used for other organisms).


The documentation is structured as follows:
* [background](#Background) to performing these analyses
* [workflow outline](#Workflow-outline) to estimate a species tree and discussion of the outputs obtained at each step. Includes links to existing tutorials, including ones compiled by people at Kew
* [brief introductions to some computing subjects](#Computing-requirements-and-software) with links to existing tutorials, including those compiled by people at Kew, and how to run analysis software
* [Skeleton workflow containing useful commands](#Skeleton-workflow-of-useful-commands)


If you would like to [contribute](#Guide-to-contributors) content to this repository please contact an existing contributor at RGB Kew.

***

## Background
[ Proposed topics to include (very short paragraph on each topic)]:
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
      * Various methods but recommend HybPiper (Johnson et al, 2019)
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
* [Kapli et al (2020) Phylogenetic tree building in the genomic age](https://doi.org/10.1038/s41576-020-0233-0) - review
* [Guo et al (2022) Phylogenomics and the flowering plant tree of life](https://doi.org/10.1111/jipb.13415) - review
* [Johnson et al (2019) A universal probe set for targeted sequencing of 353 nuclear genes from any flowering plant designed using k-medoids clustering]( https://doi.org/10.1093/sysbio/syy086)

### Courses
* courses in [Evolution and genomics](https://evomics.org/), Český Krumlov, Czech Republic
* [Phylogenomics and Population Genomics: Inference and Applications](https://www.ub.edu/certfem/ppgcourse/), University of Barcelona - two week course, yearly
***

## Workflow outline for estimating a species tree
This workflow is discussed briefly in six sections below but consists of two major steps:
* **step 1:** assembly of gene sequences from samples
* **step 2** organising sequences into gene sets, aligning the genes and  using the alignments to estimate a species tree

It is assumed that target capture data is being used and available in the form of Illumina short pair end reads in [fastq format](https://en.wikipedia.org/wiki/FASTQ_format). At the end of this section, there are links to existing more detailed documentation on how to run the programs. Following this section there are some details on computing requirements and a section that summarises the commands required for a complete analysis.

###  Example data sets
 * The HybPiper example
 * PAFTOL dataset e.g. one representative sample of all orders in Angiosperms

### Choosing a good sample and gene name

### Sequencing data quality checks
* adaptor trimming
* quality trimming
* trimmomatic tool
* FASTQC

**_Outputs_**     (and **_Interpretation_**)
* Trimmomatic output - expected % retained pair end and single end reads; single can also be used in HybPiper (can be 7% of total reads).
* 
**_Go further_**

### Gene recovery from samples
* HybPiper
* organising sequences into gene sets
* output DNA sequences should be in frame

**_Outputs_**    (and **_Interpretation_**)

**_Go further_**
* Captus software (?)
* Data mining

### Alignment of genes from samples
Intro - Various easy to use alignment programs exist - recommended ones: MAFFT, UPP for large alignments

**_Outputs_** (and **_Interpretation_**)
* Assessment: AMAS summary
* Filtering tools: AMAS, Trimal
* Removal of long branches with TreeShrink
* visualisation of the alignments

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

### Detailed workflows available online
The following links to tutorials and workflows go into the practical details about processing read data and estimating trees. Some additional computing knowledge required and is discussed in the next section.

* A practical [workflow by Sidonie Bellot](https://github.com/sidonieB/Workflows) - details include:
  * overview of target capture (bait design and making DNA libraries)
  * data quality checks and cleaning
  * use of HybPiper (version 1.3) and tips on running the program plus information on: 
    * formatting reference targets
    * gene assembly strategy 
  * multiple sequence alignment, estimating gene trees 
  * estimating he species tree with ASTRAL-III
  
* [PhyloFrame](https://github.com/BenKuhnhaeuser/PhyloFrame) by Ben Kuhnhäuser - short list of relevant commands covering the same areas as Sidonie's workflow above
* [Training and bioinformatics resources](https://www.genomicsforaustralianplants.com/gap-bioinformatics-resources/) from the [GAP phylogenomics project](https://www.genomicsforaustralianplants.com/phylogenomics) - contains:
  * links to their phylogenomic workflows
  * [recommendations](linkhere) on data analysis to estimate a species tree
  * bioinformatics webinars and workshops (with materials to try out)

* [Kew internal training course in phylogenomics (November 2019)](https://github.com/baileyp1/PhylogenomicsTraining_Nov2019)
  * teaches the steps required to estimate a species tree
  * includes summary of basic Linux commands, data transfer to and from computers, an example of running analyses with the Slurm job scheduler
  
* PAFTOL Explorer workflow 

### References
* [Tutorial on ASTRAL by Siavash Mirarab](http://tandy.cs.illinois.edu/astral-tutorial.pdf)
  * slides summarizing the ASTRAL process
  * recommendations on:
    * dealing with low bootstrap support values in gene trees
    * filtering sequences from gene alignments 
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
  * good overview of how to run your analysis via the Slurm job scheduler
  * maximum number of cpu's per user is limited to 256 (@March 2024)

* [Course materials](https://github.com/prog4biol) from [Programming for Biology](https://programmingforbiology.org/), Cold Spring Harbour
  * comprehensive introductions to Unix, Git and Python

* A short Linux command line and Slurm primer from the course [Methodological Advances in Reticulate Evolution](https://gtiley.github.io/RBG-Networks/activities/introduction/) (held at RGBKew, November 2023). Includes introduction to writing scripts in Bash, Python and Perl.
* lots and lots of other documentation and courses are available online
  * e.g. https://app.datacamp.com/ is available to Kew employees. It includes courses on R, Python, SQL, AI 

### Courses
* [Bioinformatics Training](https://bioinfotraining.bio.cam.ac.uk/) at University of Cambridge:
  * Link to courses: https://bioinfotraining.bio.cam.ac.uk/
  * [Upcoming courses](https://training.cam.ac.uk/bioinformatics/event-timetable)
  * [Introduction to Phylogenetics](https://training.cam.ac.uk/bioinformatics/course/bioinfo-phylng)


The rest of this section summarizes handy commands for the following  computing topics, the first three being important for getting started with analyses:

* [Linux command line](#Linux-command-line)
* [Installing software](#Installing-software)
* [Slurm job scheduler](#Slurm-job-scheduler)
* [Python](#Python)
* [Java](#Java)
* [Jupyter notebook](#Jupyter-notebook)
* [R](#R)
* [GitHub](#GitHub)

### Linux command line
* Minimum commands - minimum commands required to take control of the command line
* Link to one or two more primers
* awk

#### Slurm
It is essential to be able to run analysis work (jobs) via the Slurm job scheduler. The links at the top of this computing section contain plenty of instructions on how to use Slurm. The following link describes how to run jobs using relevant examples of target capture data analysis (using HybPiper version 1.3 or HybPiper version 2) and generating gene alignments and phylogenetic trees:
  * https://github.com/sidonieB/Workflows/blob/main/Slurm_cheat_sheet.md

The remainder of this section summarizes useful Slurm example commands that can be copy and pasted onto the command line. Text or values that must be edited before using the command are shown between '<' and '>' characters.

#### sinfo
```bash
sinfo -o "%16P %.5a %.10l %8p %.6D %.6t %N %m" 
```
Output contains useful information you might want to consider before submitting an analysis (job) on a particular partition (queue)
* partition names (*=default)
* whether the partition is available
* time limit for the partition
* priority the job would have in a particular queue
* list of node names in the queue 
* maximum amount of memory (RAM) available in each node

#### sbatch
One way of submitting a job to Slurm using the --wrap flag (useful for practice and testing)
```bash
sbatch -J <jobName> -p long -c 1 -n 1  --mem=5000  -o <jobName>.log  -e <jobName>.err  --wrap  " <your command(s) here> ] " 
```
* By default memory (RAM) is specified in mega bytes (MB)
* Note - if the following characters are used within the command, they need to be used with a backslash character: `  "  $  (i.e.  \'  \"  \$)
  * Variables from outside the script e.g. $variableName must be used without the backslash!

#### squeue
```bash
squeue -o "%.22i %.13P %.25j %.8u %.8T %.10M %.9l %.6D %.R %.C %.m %.p"
```
Output can be used to keep track of queued and running jobs e.g.:
* the unique identifier of your job (JOBID)
* the node on which the job is running (NODELIST)
* the current state of your job (NODELIST(reason))
* the number of cpus (CPUS) you requested
* how much memory (MIN_MEMORY) you requested
* To see your jobs only add: -u $USER

#### scontrol
If using Slurm arrays, to change the number of jobs to run in parallel:
```bash 
scontrol update arraytaskthrottle=10 job=<jobId>
```
To change the amount of RAM for jobs still pending: 
```bash
scontrol update MinMemoryNode=5000  job=<jobId>
```
* By default memory (RAM) is specified in mega bytes (MB)

To change the number of cpus to use for jobs still pending:
```bash
scontrol update NumCPUs=10  job=<jobId>
```
* Note - you may also have to set CPUsPerTask to the value required as well

To change the time limit:
```bash
scontrol update TimeLimit=2-00:00:00  job=<jobId>
```
* TimeLimit example values: UNLIMITED, 1-00:00:00 (day-hours:minutes:seconds)

Other scontrol update variables:
  * Partition

#### sacct
```bash
sacct -S 093023-09:00 --format=jobid,jobname%-25,start%16,end%16,Partition%13,elapsed,cputime,ncpus%3,ntasks%4=3,NodeList,AveVMSize,MaxRss%12,user%7,state,ExitCode  < | grep batch | grep [jobId]1226030\|1227326 | sort -k11n >
```
Output provides a table of information on the outcome of a job:
* -S option (Start) restricts the output to jobs started from the specified date
* the Elapsed field contains the real time the job took
* the MaxRSS field is the maximum amount of RAM your job used. If the value is larger than the amount of RAM specified your job will fail
* the State field shows whether the _last_ command executed in the job completed successfully. Values are: COMPLETED, FAILED,  OUT_OF_ME+, TIMEOUT
* the ExitCode field shows the Linux exit code: 0.0 (successful), 1.0 (failed), >1.0 (some otheer issue)
* final part of the command is useful for large job arrays - | grep batch | grep <jobId> | sort -k11n:
  * restricts output to job of interest
  * 'sort -k11n' sorts the output by the size of memory consumed; replace with sort -k5 to sort the time taken (Elapsed) (sorts correctly up to 9 days only!)

#### scancel
To cancel a job (array):
```bash
scancel <jobId>
```
To cancel all jobs pending for a user:
```bash
scancel -t PENDING -u <username>
```
To cancel a large number of jobs within a range jobId values:
```
scancel {<jobId>..<jobid>}
```
  * ... but you probably should have used a Slurm job array instead

#### srun
```bash
srun --cpus-per-task=1 --mem-per-cpu=2G --partition=himem --pty bash  
```
* logs you directly into a node where you can run jobs interactively
* To see inside a specific node add the nodelist flag
  * e.g. --nodelist=n21-64-2048-buck

### Installing software
* Organising software advise
* Installers
* Conda
  * Installing HybPiper2 on a bad day (connection slow and dropping)

### Python
* Running a Python script - if you hzve to run a script with python in front
* Installing Python modules
* Setting up a Python environment

### Jupiter notebook
* Setting up a script

### Java
 * Java versions and JRE/JDE 
 * Running a Java script - setting memory 
 * 
### R

### GitHub

***

## Skeleton workflow summary
This section is a very concise summary of the commands required  for a complete analysis. It takes the example data set from HybPiper and works through read preparation, HybPiper gene recovery, gene alignment with MAFFT, gene tree estimation with IQTREE2 and ASTRAL tree for estimating the species tree.

* To use the same headings as in the Workflow outline provided above.
* Suggest to follow HybPiper2 tutorial
* then more detail from the gene alignment step onwards
    [yet to outline]


## Contributors
* Paul Bailey
* Sidonie Bellot
* Ben Kuhnhaeuser

### Guide to contributors
* Need to think how the document(s) can be modified. Is it best to transfer agreed tracked changes from e.g. a Google doc?
  * Can edit inGuitHub online and leave a commit message with your name - there's even an extended message box to leave further info - might be sufficient
* The idea is the the content should be very succinct and to the point
* Maybe contributors should meet occasionally to assess structure and agree new content
* If the document grows significantly or new topics are included, could break out into several files
* What other topics could be covered by other people as well as estimating species trees?
* Open door sessions (?)







---
<span style="font-size:small;">Copyright © 2024 The Board of Trustees of the Royal Botanic Gardens, Kew</span>



