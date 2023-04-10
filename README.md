# CAPP-seq normal alignment workflow
Snakemake workflow for processing CAPP-Seq data generated from constitutional/normal DNA.


## Configuration
1. Download the workflow: `git clone https://github.com/morinlab/cappseq_normal_workflow`.
2. Edit the sample file under `config/samplelist.tsv` with your samples of interest.
  - This will be a 3-column config file containing `sample_id`, `path_to_R1_fastq`, `path_to_R2_fastq`.
  - Use "#" to comment out lines.
3. Edit the workflow config file under `config/cappseq_normal_config.yaml` for your project's parameters.
4. Create a conda environment containing `snakemake` version 7 or newer, and activate that environment.
5. Run the workflow using `snakemake --use-conda -c <number_of_threads>`


## Results
  - Final processed BAM files (collapsed and error corrected using UMIs) can be found under `99-final/`.
  - Final QC report can be found under `Q9-multiqc`.
