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

Step five: FastQ splitter v.1.1.5 on Exome_reads_QCfiltered
Output: Exome_Reads_R1_QCfiltered & Exome_Reads_R2_QCfiltered

Step six: Map with BWA-MEM v0.7.17.2 on Exome_reads_R1_QCfiltered & Exome_reads_R2_QCfiltered
Output: Exome_reads_QCfiltered_mapped

Step seven: SAMTools Flagstat v2.0.4 on Exome_reads_QCfiltered_mapped

Step eight: Map with BWA-MEM v0.7.17.2 on Exome_reads_R1 & Exome_reads_R2
Map with BWA-MEM aligns the reads to the reference genome GRCh37 / h19 / b37
Output: Exome_reads_mapped

Step nine: SAMTools Flagstat v2.0.4 on Exome_reads_mapped

Step ten: FreeBayes v1.3.6 on Exome_reads_QCfiltered_mapped
Output: FreeBayes_variants

Step eleven: bcftools filter v1.15.1 on FreeBayes_variants
          Restrict to region: UCSC R132 genes
Output: VCF_forVEP

Step twelve: bcftools norm on VCF_forVEP
Output: normalisedVCF

Step thirteen: VCFfilter on normalisedVCF_forVEP
              Filter: DP (read depth at the locus) > 10
              Filter: AO (count of observations at alt haplotype) > 5
              Filter: AF (% of observations at alt haplotype) > 0.15
Output: normalised_filtered_VCF

Step fourteen: Annotate and filter variants on VEP
            Input: normalised_filtered_VCF
            Filter: MAF >0.01 in 1k genomes excluded
Output: Variants_VEP

Step fifteen: Filter on Variants_VEP
           Filter: AF >0.01 gnomAD excluded

Step sixteen: Upload normalised_filtered_VCF to Mutation Distiller
Output: Variants_MutationDistiller
A list of 3 variants none of which appear to be disease-causing

These 3 variants are extracted from Variant_VEP list
