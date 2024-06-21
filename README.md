# CryptoGat201RNASeq

Cryptococcus neoformans RNA-seq Gat201 experiment in RPMI and RPMI + Serum media.

This repository is supplementary data, specifically RNA-seq dataset 2 data and analysis, accompanying the bioRxiv preprint:

> A trade-off between proliferation and defense in the fungal pathogen Cryptococcus at alkaline pH is controlled by the transcription factor GAT201.
> Elizabeth S. Hughes, Laura R. Tuck, Zhenzhen He, Elizabeth R. Ballou, Edward W.J. Wallace.
> bioRxiv preprint, 2024
> https://doi.org/10.1101/2023.06.14.543486

Analysis by Liz Hughes (liz.hughes@ed.ac.uk) and Edward Wallace (Edward.Wallace@ed.ac.uk), February 2021 through June 2024.

Data was created by Liz Hughes, December 2020.
Raw data and gene counts are available in [NCBI Gene Expression Omnibus GSE217345](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE217345).

# Contents

* src - scripts for nearly-raw data processing, including main script quantseqfwd.nf
* quantseqfwd_EH_050221 - results of quantseqfwd.nf
* quantseqfwd_test_output - practice run on subsampled data. Only useful for troubleshooting
* data_external - external data from published papers used for analysis
* Rmarkdown - scripts for more results-oriented data analysis and figures
* input_annotation - Cryptococcus genome annotation used for read alignment and counting.
* input_experiment - other input files including sample sheet
* results - output data and results


## How we made the subsampled data

It is strongly recommended to do a test run on small yet real data - subsampled data - before running on a large dataset.
An example of subsampling fastq files is:

```
gzip -dkc EH_050221_Data/1_S1_R1_001.fastq.gz \
  | head -n 400000 | gzip > EH_050221_Data_subsample/1_S1_R1_001_init100000.fastq.gz

gzip -dkc EH_050221_Data/2_S44_R1_001.fastq.gz \
  | head -n 400000 | gzip > EH_050221_Data_subsample/2_S44_R1_001_init100000.fastq.gz
```


## How to run the pipeline

First edit the parameters in `src/quantseqfwd.nf` so that

* `params.input_fq_dir` points to an input directory containing all of your fastq files 
* `params.output_dir` points to the output directory where you would like all the outputs stored.

Then run the command:

```
nextflow run src/quantseqfwd.nf -with-dag flowchart.png -with-report nextflow_report.html
```

The options `-with-dag` and `-with-report` are just to tell you a little more about the output, they are not strictly needed in order to run.

