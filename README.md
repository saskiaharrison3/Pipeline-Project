# Pipeline-Project
Inputs: Exome_reads_R1 & Exome_reads_R2
Reference genome: GRCh37
BED file: UCSC R132 genes

Step one: FASTQ joiner on Exome_reads_R1 & Exome_reads_R2

Step two: FastQC on Exome_reads

Step three: filter by quality on Exome_reads
            Quality cut-off: 20
            Percent of bases in sequence that must have quality equal to / higher than cut-off value: 90
            
Step four: FastQC on Exome_reads after filter by quality

Step five: FastQ splitter on Exome_reads after filter by quality

Step six: Map with BWA-MEM on Exome_reads_R1 & Exome_reads_R2 after filter by quality

Step seven: SAMTools Flagstat on Exome_reads_Mapped

Step eight: FreeBayes on Exome_reads_Mapped

Step nine: bcftools on FreeBayes_variants
          Restrict to region: UCSC R132 genes

Step ten: Annotate and filter variants on VEP
            Filter: MAF 2%
