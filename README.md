# Ebola_Variant_Analysis
Analysis of Ebola variants from 1972-2014

The purpose of this project was to generate a makefile that can be used for variant calling analysis. To test the script, we evaluated Ebola variants
from 1972-2014, reproducing findings regarding the variations occurring in the Ebola virus genome as reported in "Genomic surveillance elucidates Ebola virus origin," originally published in Nature (2014). However, this makefile can be adjusted to any sequence dataset stored with an SRR run id.

### To Run this Program:

- the makefile must be downloaded to the local system
- the bioinfo miniconda environment must be installed and set up, which can be accessed at biostarshandbook.com
- open the terminal and use the following recipe at the command line:

### Recipe:

```
# create a new directory for the analysis
mkdir -p work

# switch to directory
cd work

# activate bioinfo environment (contains all exec files)
conda activate bioinfo

# Obtain the makefile
curl -s http://data.biostarhandbook.com/make/snpcall.mk > Makefile

# Run the makefile
make
```
The following will be printed to the screen:

```
USAGE:

  make vcf  # generates vcf file

  make clean  # removes test data
  make realclean  # removes all intermediate files
  make data  # downloads full dataset

DEFAULTS:

   ACC=AF086833  SRR=SRR1553425  CPU=4  LIMIT=100000
```

From here, choose generate a vcf file

```
make vcf
```

The programs will run for a minute or two depending on computer speed, and will provide detailed updates on progress
Once finished, the makefile will have produced the following:

- The viral sequence files as FASTA.
- The viral annotation files as GFF.
- Sequencing data in FASTQ format obtained from the Short Read Archive (SRA)
- Quality controlled sequenced data with trimmed and quality filtered reads using trimmomatic.
- An alignment BAM file generated with the bwa short read aligner, filtered, sorted, and indexed with samtools.
- A VCF file generated with bcftools lists the variants of the 2014 data relative to 1972 strain.
- An annotated VCF file generated with snpEff that describes the effect each variant has on the protein-coding regions.An HTML file that reports the various variants and their effects on the genome.


