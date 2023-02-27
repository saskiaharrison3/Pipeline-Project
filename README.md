# Pipeline-Project
Inputs: Exome_reads_R1 & Exome_reads_R2

Step one: Trimmomatic on Exome_reads_R1 & Exome_reads_R2
          Reads: Paired-end
          To perform: sliding window
          Number of bases to average across: 4
          Average quality required: 20

Step two: FastQ joiner on Trimmomatic_R1_paired & Trimmomatic_R2_paired

Step three: FastQC on Exome_reads_Trimmomatic_Joined

Continue on main branch on line ...
