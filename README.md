# Pipeline-Project
Inputs: HumanExom_17A-I-X01_R1 & HumanExom_17A-I-X01_R2

Step one: FASTQ joiner on HumanExom_17A-I-X01_R1 & HumanExom_17A-I-X01_R2

Step two: FastQC on HumanExom_17A-I-X01_Joined

Step three: Map with BWA-MEM on HumanExom_17A-I-X01_Joined

Step three: SAMTools Flagstat on HumanExom_17A-I-X01_Mapped

Step four: 
