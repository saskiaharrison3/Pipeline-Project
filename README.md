# Pipeline-Project
Inputs: Exome_reads_R1 & Exome_reads_R2
Reference genome: GRCh37
BED file: UCSC R132 genes

Step one: FASTQ joiner v2.0.1.1 on Exome_reads_R1 & Exome_reads_R2
# FastQ joiner joins the two fastq files to create a single file to run a fastQC report on #

Step two: FastQC v0.73 on Exome_reads
# FastQC produces quality metrics for the sequencing reads #

Step three: Map with BWA-MEM on Exome_reads_R1 & Exome_reads_R2
# Map with BWA-MEM aligns the reads to the reference genome GRCh37 / h19 / b37 #

Step four: SAMTools Flagstat on Exome_reads_Mapped

Step five: FreeBayes on Exome_reads_Mapped

Step six: bcftools on FreeBayes_variants
          Restrict to region: UCSC R132 genes

Step seven: Annotate and filter variants on VEP
            Filter: MAF 2%
