# nf-core/fetchngs Workflow on Gitpod

This guide will walk you through setting up and running the `nf-core/fetchngs` Nextflow workflow on Gitpod using the `sratools` download method.

## Prerequisites

1. **Gitpod Account**: Make sure you have an account on [Gitpod](https://www.gitpod.io/).
2. **Fork the Repository**: Fork the [nf-core/fetchngs](https://github.com/nf-core/fetchngs) repository to your GitHub account.

## Setup

1. **Launch Gitpod**: Open your forked repository on GitHub and click the Gitpod button to launch a new workspace.

2. **Verify Nextflow Installation**: Ensure Nextflow is installed and working. Run the following command in the Gitpod terminal:
   ```sh
   nextflow info
   ```
   You should see output similar to:
   ```
   Version: 24.04.2 build 5914
   Created: 29-05-2024 06:19 UTC
   System: Linux 6.1.89-060189-generic
   Runtime: Groovy 4.0.21 on OpenJDK 64-Bit Server VM 17.0.11-internal+0-adhoc..src
   Encoding: UTF-8 (UTF-8)
   ```

## Running the Workflow

1. **Create the Input File**: Create an `ids.csv` file with the database IDs. Each line represents a database ID.

   ```sh
   echo -e "SRR9984183\nSRR13191702\nERR1160846\nERR1109373\nDRR028935\nDRR026872" > ids.csv
   ```

2. **Run the Workflow**: Execute the `fetchngs` workflow using Nextflow with the `sratools` download method.
   ```sh
   nextflow run nf-core/fetchngs -profile docker --input ids.csv --outdir output --download_method sratools
   ```

## Verifying the Output

1. **Check the Output Directory**: Verify that the output files have been downloaded and processed correctly.

   ```sh
   ls output
   ```

2. **Review Logs**: Optionally, review the logs for any warnings or important messages.
   ```sh
   find work -name '.command.log' -exec cat {} \;
   ```

## Citations

The nf-core framework for community-curated bioinformatics pipelines.

Philip Ewels, Alexander Peltzer, Sven Fillinger, Harshil Patel, Johannes Alneberg, Andreas Wilm, Maxime Ulysse Garcia, Paolo Di Tommaso & Sven Nahnsen.

Nat Biotechnol. 2020 Feb 13. doi: [10.1038/s41587-020-0439-x](https://doi.org/10.1038/s41587-020-0439-x).

## Conclusion

By following these steps, you should be able to successfully run the `nf-core/fetchngs` workflow on Gitpod using the `sratools` download method. Ensure you review the outputs and logs to verify that the workflow has completed as expected.

## Credits

nf-core/fetchngs was originally written by Harshil Patel (@drpatelh) from Seqera Labs, Spain and Jose Espinosa-Carrasco (@JoseEspinosa) from The Comparative Bioinformatics Group at The Centre for Genomic Regulation, Spain. Support for download of sequencing reads without FTP links via sra-tools was added by Moritz E. Beber (@Midnighter) from Unseen Bio ApS, Denmark.
