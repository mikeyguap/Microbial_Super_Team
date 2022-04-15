# Lab Notebook 2/11/22

## This command tells me what files are in this directory
ls
gen711_lab.code-workspace       mgospodarczyk_labnotebook.md    shell_data

## Shows where the folder is on the computer
pwd

## This clears the terminal
clear

## Change directory
cd Desktop/gen711_lab  

## manual page
man ls
ls -lstrh

## change
cd untrimmed_fastq/

head

## to move out one dir, use:
cd ../

# Old notes above
# Lab 3 

## Shortcut to home dir
cd ~
 
 ## reveals hidden files in wd
ls -a 

cd .hidden
cat youfoundit.txt

cd untrimmed_fastq

## * this does this
ls *.fastq
## only return fast q with 977
ls *977.fastq

## history
history

history | grep ls
 
 ## do this in the untrimmed.fastq
grep 'ATAT' SRR097977.fastq
grep 'ATAT' SRR097977.fastq | grep 'AAAG' 


## Word Count
wc SRR097977.fastq

wc -l SRR097977.fastq

grep 'ATAT' SRR097977.fastq | wc -l
36

##
Control + C = cancel

## DoubleGreep 
grep 'ATAT' SRR097977.fastq | grep 'AAAAG' | wc -l
2

# Lab 4 Notes

## get to the sra_metadata directory using an Absolute path
cd /Users/michaelgospodarczyk/Desktop/gen711_lab/shell_data/sra_metadata

## use a relative path to navigate to the untrimmed_fastq directory

## new command nano: creates a new text file or opens a file in writing

nano newfile.txt  ##create a new file with that name
nano  ##creates a file that you need to name

## new command less : opens files for reading 
less newfile.txt ##opens a file for reading, press q to exit

cat newfile.txt ##print the whole file to the screen

head newfile.txt ##head command prints the first 10 lines

nano newfile.txt ##add more text to newfile.txt using nano

## new command - mkdir : creates a new directory/folder
## creates a new directory named tmp_files
mkdir tmp_file
mkdir ../sra_metadata/tmp_file

## new command - mv: moves files
## move the newfile.text to the tmp_files directory - can do absolute or relative path
mv newfile.txt tmp_files
cd tmp_file

## review cat, grep, wc, and pipes
# first take a look at fastq files
# should we use the less cat or head command
head SRR097977.fastq
cat SRR097977.fastq
less SRR097977.fastq

## figure out how many different reads we have in one fastq file
grep ## command file
grep "@" SRR097977.fastq
grep "@" SRR097977.fastq | wc -l
## 257 reads in fastq file

grep "@" SRR098026.fastq
grep "@" SRR098026.fastq | wc -l
## 274 reads in fastq file

## we can also put this info into a new file
grep "@" SRR097977.fastq | wc -l > fastq_count.txt
grep "@" SRR098026.fastq | wc -l >> fastq_count.txt

## navigate to gen711
cd gen711_lab

## create a new directory named fastq_files
mkdir fastq_file

## new command - cp: copies files  // do everything in the gen711 folder without going back and forth
cp shell_data/untrimmed_fastq/*.fastq fastq_files

cd /Users/michaelgospodarczyk/Desktop/gen711_lab/shell_data/untrimmed_fastq/tmp_file

## new command - rm: deletes files
rm newfile.txt

cd ../
 
ls -l
## add output 
-rw-r--r--@ 1 michaelgospodarczyk  staff     7 Feb 27 17:38 dummy_file.txt
drwxr-xr-x@ 2 michaelgospodarczyk  staff    64 Feb 27 18:25 fastq_file
-rw-r--r--  1 michaelgospodarczyk  staff    43 Feb 11 17:36 gen711_lab.code-workspace
-rw-r--r--@ 1 michaelgospodarczyk  staff  2075 Feb 27 18:13 mgospodarczyk_labnotebook.md
-rw-r--r--@ 1 michaelgospodarczyk  staff     8 Feb 27 17:37 newfile.txt
drwxr-xr-x@ 6 michaelgospodarczyk  staff   192 Feb 27 14:14 shell_data

## Lab 5

## Commands to review
ls- what is in this cd
cd - change directory
pwd - where you are at currently (print working directory)
mv - move files 
cp - copies files 
cat - print to command line
grep - search for a string match
wc - word count
mkdir - create a new directory with a name 
rm - delete file

### absolute paths:
- Very usefil for getting to your folder no matter where you are 
cd /Users/michaelgospodarczyk/Desktop/gen711_lab

### relative paths:
- get you where you want to go from directory that you are currently in

## special characters:
- Globs: "*" ( wildcards) is use to match
- Pipes '|' (bar) send the output of a command to another command

### Programs:
- nano
- less

# For the practical: Please put 'cd /absolute/path/to/gen711' at the top of your notes pages
cd /Users/michaelgospodarczyk/Desktop/gen711_lab

## Practice practical

### Change your working directory to your gen711 folder with an absolute path
cd /Users/michaelgospodarczyk/Desktop/gen711_lab

### Change your working directory to the 'shell data' folder
cd shell_data

### Use grep to search for a bad read ( any read with 7 uncalled bases in a row )
grep 'NNNNNNN' SRR098026.fastq

### Use the 'B' option to get line above each match
grep -B1 'NNNNNNN' SRR098026.fastq

### How many lines below each grep line belong to a read?
2

### Use the 'A' and 'B' options with grep to return the read and info lines for each match
grep -A2 -B1 'NNNNNNN' SRR098026.fastq

### Redirect the bad reads in SRR098026.fastq to a file called bad_reads.fastq
grep -A2 -B1 'NNNNNNN' SRR098026.fastq > bad_reads.fastq

### Determine how many lines are in this file
wc -l bad_reads.fastq

### Redirect the bad reads for both fastqs into bad_reads.txt at the same time
grep -A2 -B1 'NNNNNNN' *fastq > bad_reads.fastq

### Determine how many bad read lines are in each of the fastq lines, and compare that with the number of lines in bad_reads.fastq
grep '@' bad_reads.fastq | wc -l
274
wc -l bad_reads.fastq
1492
### Have a look in the file to find out what is wrong
less bad_reads.fastq

### Use a reverse grep to remove the lines that
grep -v '-- '  bad_reads.fastq > newbad_reads.fastq
less newbad_reads.fastq

### Add your name to the bottom of the bad_reads.fastq
ls > list.txt
cat list.txt

- use this 
pwd >> list.txt

### Add your name to the top of the bad_reads.fastq


### Make a script that makes a file of bad reads


### change the permissions of the file and run the script


### add your name to the end of new bad reads file


### Run md5sum on scripted_bad_reads.txt and write the output to my_md5sum.txt

#!/bin/bash 

bwa sample.fastq reference.fasta > sample.alignment.sam

gatk sample.alignment.sam reference.fasta

## control c to get out of getting stuck in terminal with nothing


-----------
Exam 2

## Microbiome: the collective microbial community
# ASV; amplicon sequence variant

Marker gene analysis (150 - 300bp)
- Cheap
- High throughpu
- Limited to a single amplicon
- Low resolution
- No functional information

Library prep
- DNA extractions
- PCR

Sequencing
Raw reads go into software



# OTU; operational taxonmic unity

Metagenomics (100/150) bp
- More expensive
- More intensive analysis
- Full genome
- Functional potential

Library Prep
- DNA extractions
- Usually no random amplification

Sequencing
Assembly
Binning - which scaffolds in your total assembly came from the same microbial community
                - Nucleotide composition
                - Phylogenetic
                - Read depth/ coverage
                - Coverage patterns
            
Barcodes allow us to identify unique PCR products within our sample

Anaconda and QIIME2 (Quantitative insights into microbial ecology) software programs used needef for microbial community analysis
- PCR amplicon analysis (16s,18s,ITS)

QIIME2 Pipeline
Raw reads - import QIIME - remove primers - denoising, clustering etc. - mergre feature table and rep sequences - Assign taxonomy -> filter feature table - build phylogeny - alpha rarefaction - nomralization - statistical analysis

Importing reads into QIIME2
    What kind of data do you have
    - Qaulity reads 

Demultiplexing
- maps sequences to the samples they're associated with and removes barecodes

Primers and adapters need to be removed for correct assignment of ASV and OTU
    ways to remove
    - Cutadapt
    - Trim in DADA2
    - For ITS use ITSXpress

Quality Filtering
- DADA2, Deblur (conservative estimate)
both need to trim sequences based on quality scores

Decision cont. ASV (99% similar) or cluster them into OTU (97% similarity)
ASV's have higher resolution, more reproducible and allow comparisons across datasets

Taxonomy
- what amplicon to use?
    bacteria and archea - 16s
    fungi - ITS
    Eukaryotes - 18as
    "barcode regions"

Alpha rarefaction: make sure enough sequence coverage for each sample and not more observed ASV with increasing sequence depth
Calculates species richness based on a random collection of sequences

Normalization: Rarefy- subsampling data to a specific sequencing depth

ASV: two different samples
OTU: basically same sample- good enough

----
module load anaconda/colsa
source activate qiime2-2020.2

# what are importable formats?
qiime tools import --show-imoportable-formats
qiime tools import --show-imoportable-types

# downloading reads onto server
wget <link>

--type Text
--input-path PATH
--help

# demultiplex step
qiime demux emp-single 00i-seqs emp-single-end-sequence


curl -sL \
  "https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh" > \
  "Miniconda3.sh"

bash Miniconda3.sh

conda update conda

conda install wget


-----------------------------------------------------------------------------------------------------
#### Project

We are going to obtain metabarcode data sampled from two bodies of water (the Oyster River and the Great Bay) and will use the 16s ribosomal RNA sequences to identify the species’ composition in the two communities and how they differ.

Get data from Dr. Miller → download publicly available data of known 16s sequences and their species  → use Qiime2 to align our data to those data and identify the species present in each community and their abundances → compare the composition of the communities

Partners: Michael Gospodarczyk, Ella, Rebecca

# Installing a conda environment

## Test your conda installation

conda -v 

## Add the channels to look for progams on the web
conda config --add channels default
conda config --add channels bioconda
conda config --add channels conda-forge

# environment
conda create -n Microbial_Super_Team python bwa fastqc

## Might give people errors
conda activate Microbial_Super_Team

# download contents of qiime2
wget https://data.qiime2.org/distro/core/qiime2-2022.2-py38-osx-conda.yml
conda env create -n  Microbial_Super_Team_Qiime2 --file qiime2-2022.2-py38-osx-conda.yml

# activate new environment
conda activate Microbial_Super_Team_Qiime2
