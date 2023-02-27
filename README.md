# Pipeline-Project
Inputs: Exome_reads_R1 & Exome_reads_R2

Step one: FASTQ joiner on Exome reads R1 & Exome reads R2

Step two: FastQC on Exome_reads_Joined

Step three: Map with BWA-MEM on HumanExom_17A-I-X01_Joined

Step three: SAMTools Flagstat on HumanExom_17A-I-X01_Mapped

Step four: 
