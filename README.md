# Pipeline-Project
Inputs: Exome_reads_R1 & Exome_reads_R2
Reference genome: GRCh37
BED file: UCSC R132 genes

Step one: FASTQ joiner v2.0.1.1 on Exome_reads_R1 & Exome_reads_R2
FastQ joiner joins the two fastq files to create a single file to run a fastQC report on
Output: Exome_reads

Step two: FastQC v0.73 on Exome_reads
FastQC produces quality metrics for the sequencing reads

Step three: Filter by quality v1.0.2 on Exome_reads 
            Quality cut-off: 20 
            Percent of bases in sequence that must have quality equal to / higher than cut-off value: 90
Output: Exome_Reads_QCfiltered

Step four: FastQC v0.73 on Exome_reads_QCfiltered

Step five: FastQ splitter on Exome_reads_QCfiltered
Output: Exome_Reads_R1_QCfiltered & Exome_Reads_R2_QCfiltered

Step six: Map with BWA-MEM v0.7.17.2 on Exome_reads_R1_QCfiltered & Exome_reads_R2_QCfiltered
Output: Exome_reads_QCfiltered_mapped

Step seven: SAMTools Flagstat v2.0.4 on Exome_reads_QCfiltered_mapped

Step eight: Map with BWA-MEM v0.7.17.2 on Exome_reads_R1 & Exome_reads_R2
Map with BWA-MEM aligns the reads to the reference genome GRCh37 / h19 / b37
Output: Exome_reads_mapped

Step four: SAMTools Flagstat v2.0.4 on Exome_reads_mapped

Step five: FreeBayes v1.3.6 on Exome_reads_QCfiltered_mapped
Output: FreeBayes_variants

Step six: bcftools filter v1.15.1 on FreeBayes_variants
          Restrict to region: UCSC R132 genes
Output: VCF

Step seven: bcftools norm on VCF_forVEP
Output: normalisedVCF

Step eight: VCFfilter on normalisedVCF_forVEP
Output: normalised_filtered_VCF

Step eight: Annotate and filter variants on VEP
            Input: normalised_filtered_VCF
            Filter: MAF >0.02 excluded
Output: Variants_VEP
A list of ~20 variants none of the variants appear to be disease-causing

Step nine: Upload normalised_filtered_VCF to Mutation Distiller
Output: Variants_MutationDistiller
A list of 3 variants none of which appear to be disease-causing
