# Pipeline-Project
Inputs: Exome_reads_R1 & Exome_reads_R2

Step one: FASTQ joiner on Exome reads R1 & Exome reads R2

Step two: Trimmomatic on Exome_reads_Joined
          Reads: single end
          To perform: sliding window
          Number of bases to average across: 4
          Average quality required: 20

Step three: FastQC on Exome_reads_TrimmomaticJoined

Continue on main branch on line ...
