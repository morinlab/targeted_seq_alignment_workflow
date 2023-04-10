# Targeted sequencing alignment workflow
Snakemake workflow for processing targeted paired-end Illumina sequencing data.


## Configuration
1. Download the workflow: `git clone https://github.com/morinlab/targeted_seq_alignment_workflow`.
2. Edit the sample file under `config/samplelist.tsv` with your samples of interest.
  - This will be a 3-column config file containing `sample_id`, `path_to_R1_fastq`, `path_to_R2_fastq`.
  - Use "#" to comment out lines.
3. Edit the workflow config file under `config/cappseq_normal_config.yaml` for your project's parameters.
4. Create a conda environment containing `snakemake` version 7 or newer, and activate that environment.
5. Run the workflow using `snakemake --use-conda -c <number_of_threads>`


## Workflow
This workflow performs the following steps:
1. Processes FASTQ files using FASTP to remove trailing Illumina adapters and sequencer-specific artifacts.
2. Align reads against the reference genome using BWA.
3. Mark duplicate reads using Picard MarkDuplicates.


The following Quality Control metrics are calculated:
  - Duplicate rate (Picard MarkDuplicates).
  - Capture efficiency (Picard CollectHsMetrics).
  - Target-region coverage (Picard CollectHsMetrics).
  - Oxidative artifacts (Picard CollectOxoGMetrics).
  - Fragment size (Picard CollectInsertSizeMetrics).
  - General read/contamination metrics (FASTQC).


## Results
  - Final processed BAM files can be found under `99-final/`.
  - Final QC report can be found under `Q9-multiqc`.
