# CryptoGat201RNASeq_draft
Cryptococcus neoformans RNA-seq Gat201 strains 2021.

Data created by Liz Hughes, December 2020. 
Analysis started by Edward Wallace, February 2021

# Contents

* src - scripts for data processing
* input_annotation - Cryptococcus genome annotation used for read alignment and counting.
* input_experiment - other input files including sample sheet
* results - output data and results

## How we made the subsampled data

```
gzip -dkc EH_050221_Data/1_S1_R1_001.fastq.gz \
  | head -n 400000 | gzip > EH_050221_Data_subsample/1_S1_R1_001_init100000.fastq.gz

gzip -dkc EH_050221_Data/2_S44_R1_001.fastq.gz \
  | head -n 400000 | gzip > EH_050221_Data_subsample/2_S44_R1_001_init100000.fastq.gz
```

## How to run the pipeline

```
nextflow run src/quantseqfwd.nf -with-dag flowchart.png -with-report quantseqfwd_report.html
```
