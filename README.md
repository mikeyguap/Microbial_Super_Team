# Microbial_Super_Team

(Just general ideas so far)

## Background

We were interested in identifying species compostion from Oyster Beds and Mud Flats (Great Bay, NH) and how their compostion of organisms differ within the same body of water. 

## Methods

(general add alot more)
Microbial samples were collected from Oyster Beds and Mud Flats in the Great Bay, NH. The collected samples were sequenced with paired end reads. output fastq files of the sequenced reads were imported into Qiime and demultiplexed. Demultiplexted reads were then placed inside Imported_Reads.qza. Imported_Reads.qza was then run through dada2 to denoise the reads and merge the forward and reverse reads. The quality visualization plot was then made and viewed in qiime2view to determine the cutoff for quality. The rarification table was then made and we used that to determine the sampling depth that we would be rarifying at. We shose 2400 because the sample with the lowest feature count had 2416 and we wanted to make sure that none of the samples were thrown out. We then extracted the reference reads from the silva database that would be used for the taxonomy assignment step. We then trained the qiime feature classifier using the silva reference sequences to classify the microbes in our samples taxonomically. our sequences (rep-seqs.qza) were then run through the trained classifier in order to classify the taxa in our samples taxonomically which output our taxonomy file (silva_taxonomy.qza). 
(any more?)
An issue that we ran into were identifying the correct pipeline to reach results in vscode using Conda environment and Qiime2. Collectively, it was difficult to input and process that same code across different computers, in which outputed errors and disturbances in the terminal.


## Findings

To add a plot from the 'figs' folder, there needs to be a line in this document that looks like this:

![plot](figures/plotfile.png)

## References (If Any)
