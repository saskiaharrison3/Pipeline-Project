# Pipeline-Project
Inputs: Exome_reads_R1 & Exome_reads_R2
Reference genome: GRCh37
BED file: UCSC R132 genes

Step one: FASTQ joiner on Exome_reads_R1 & Exome_reads_R2

Step two: FastQC on Exome_reads

Step three: Map with BWA-MEM on Exome_reads_R1 & Exome_reads_R2

Step four: SAMTools Flagstat on Exome_reads_Mapped

Step five: FreeBayes on Exome_reads_Mapped

Step six: bcftools on FreeBayes_variants
          Restrict to region: UCSC R132 genes

Step seven: Annotate and filter variants on VEP
            Filter: MAF 2%
