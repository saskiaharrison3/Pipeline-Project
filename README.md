# Pipeline-Project
Inputs: Exome_reads_R1 & Exome_reads_R2
Reference genome: GRCh37

Step one: FASTQ joiner on Exome reads R1 & Exome reads R2

Step two: FastQC on Exome_reads

Step three: Map with BWA-MEM on Exome_reads
            

Step four: SAMTools Flagstat on HumanExom_17A-I-X01_Mapped

Step five: 
