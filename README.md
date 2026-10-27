# MyFirstPipeline

BPSM group ICA by **Next-gen Bioinformaticians**.

An RNA-seq pipeline written in bash and awk for the *Trypanosoma congolense* RNAi knock-down dataset on the MSc server.

## Contents

| File | Description |
| --- | --- |
| `Next-gen_Bioinformaticians.MyFirstPipeline.tar.gz.cpt` | ccrypt-encrypted archive containing the pipeline script (`pipeline.sh`) and the full git log (`all_the_things_I_did`) |

The decryption key is given in the PDF submitted on Learn.

## Usage (on the MSc server)

```bash
git clone https://github.com/Loue-7/MyFirstPipeline.git
cd MyFirstPipeline
ccrypt -d Next-gen_Bioinformaticians.MyFirstPipeline.tar.gz.cpt
tar xzvf Next-gen_Bioinformaticians.MyFirstPipeline.tar.gz
bash pipeline.sh
```

All results are written to `./pipeline_output`. Input data are read from `/localdisk/data/BPSM/MyFirstPipeline/`, so nothing needs to be copied.

## Pipeline steps

1. Quality check with `fastqc`
2. Summary of FastQC flags and read counts
3. Alignment with `bowtie2`, sorted and indexed BAM with `samtools`; samples with an alignment rate below 80% are excluded
4. Read counts per gene with `bedtools multicov`
5. Mean counts per group, with gene descriptions
6. Group-wise comparisons generated from the sample sheet
7. Fold changes sorted by |log2FC|, with gene descriptions
