# results_counts

Results consisting of count data and analyses of those.

## quantseqfwd_EH_050221_tidy.txt.gz

Tidy/long-format counts from QuantSeq Gat201 RNA-seq timecourse in Cryptococcus neoformans.
Created by the script `src/normalize_count_analysis.Rmd`.

Columns:
  * Sampleid: id for sequencing sample (disordered here)
  * Code: encodes Strain, Condition, Time
  * Strain: yeast strain, a (KN99a), A (KN99alpha), B (Bahn collection deltaGat201), M (Madhani collection deltaGat201)
  * Gat201: genotype for Gat201, either WT (present) or delta (deletion/disruption)
  * Condition: growth media  Y (YPD), R (RPMI), RS (RPMI + serum)
  * Time: time in minutes from shift to R/RS media. 0 minutes is in YPD
  * BioRep: biological replicate (1 or 2)
  * Geneid: Geneid with systematic Cryptococcus H99 gene name
  * Count: QuantSeq 3'-end counts assigned to gene
  * TPM: Transcripts per million (normalized Count for each sample)
