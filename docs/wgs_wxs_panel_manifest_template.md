# WGS WXS Panel Manifest Readme

| Column Name | Required | Explanation | Allowed Values | Data Type | Example Entry | BTI Derived |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| participant_id | True | Unique identifier for the participant from whom the sample was collected | | string | PT1899 | True |
| sample_id | True | Unique identifier for the sample linked to the same clinical event | | string | SM7316-11566 | True |
| aliquot_id | True | Unique identifier for a specific aliquot | | string | AL1549608_T_WGS | True |
| external_participant_id | False | External, user-provided (non-unique) identifier for participants from whom the sample was collected | | string | PID1899 | |
| cohort_participant_id | False | Participant identifier as used within a specific cohort/study; interchangeable with external_participant_id when the two differ | | string | COH-PT1899 | |
| external_sample_id | False | External, user-provided (non-unique) identifier for samples linked to the same clinical event | | string | 7316-11566 | |
| external_aliquot_id | False | External, user-provided identifier linked to a specific aliquot (if leveraged for multiple assays, comprised of aliquot_id + T/N + assay performed) | | string | 1549608_T_WGS | |
| sample_type | True | Text term that represents a description of the kind of tissue collected with respect to disease status | "Tumor", "Normal", "Virus-infected", "Unknown", "Not Reported" | string | Normal | |
| composition | True | Tissue type the collected sample comes from | "Bone Marrow", "Buffy Coat", "Derived Cell Line", "Not Available", "Not Reported", "Patient Derived Xenograft", "Xenograft", "Patient Derived Organoid", "Peripheral Blood Mononuclear Cells", "Peripheral Whole Blood", "Saliva", "Solid Tissue", "Umbilical Cord Blood", "Patient-Derived T Cells", "Patient-Derived Primary Cells", "iPSC-Derived Organoid", "Cerebrospinal Fluid", "Embryonic Stem Cell Derived Cell Line" |  string | Bone Marrow | |
| bio_replicate | False | Label identifying the biological replicate this sample represents | | string | Rep1 | |
| file_name | True | Name of the file | | string | NCI-11Plex-13-F12A-z11358.fastq | |
| file_format | True | Format of the file | "FASTQ", "BAM", "BAI", "CRAM", "CRAI", "GVCF", "VCF", "TBI", "MAF", "PDF", "HTML", "DCM", "IDAT", "SVS", "GPR", "CNS", "TXT", "PNG", "CSV", "PED", "SEG", "TAR", "TSV", "mzML", "raw" | string | FASTQ | |
| file_size | True | Reported file size in bytes | | integer | 529600 | |
| file_hash_type | True | Hash algorithm used to generate file hash | "MD5", "SHA1", "SHA256", "SHA512", "ETag" | string | MD5 | |
| file_hash_value | True | Full has value of the file | | string | 938c2cc0dcc05f2b68c4287040cfcf71 | |
| sequencing_center | True | Name of the center generating sequencing data | | string | Harvard Med School | |
| platform | True | Name of the platform used to obtain data | "Complete Genomics", "Illumina", "Ion Torrent", "LS454", "SOLiD", "ONT", "DNBSEQ", "Other" | string | Illumina | |
| instrument_model | False | Specific model of sequencing instrument used. | string | Model name of the instrument used for sequencing | NovaSeq 6000 | |
| experimental_strategy | True | The sequencing strategy used to generate the data file. | "WGS", "WXS", "Targeted Sequencing" | string | WGS | |
| target_capture_kit_name | False | Description that can uniquely identify a target capture kit. Required for WXS and Targeted Sequencing. | | string | | |
| target_capture_kit_link | False | Full download link for the bed file corresponding to the target panel or capture kit used for sequence enrichment. | | string | | |
| bed_filename | False | Name of the capture kit bed file. Required for WXS and Targeted Sequencing. | | string | | |
| is_paired_end | True | If fastq/bam files, are the reads paired end? | "True", "False" | boolean | True | |
| read_pair_number | False | Denotes whether a submitted FASTQ file contains forward (R1) or reverse (R2) reads for paired-end sequencing. Required when inputs are FASTQ files. | "R1", "R1", "Not Applicaable" | string | R1 | |
| flow_cell_barcode | False | Flow cell barcode. Wrong or missing information may affect analysis results. Required when inputs are FASTQ files. | | string | H0164ALXX140820 | |
| lane_number | False | The basic machine unit for sequencing. For Illumina machines, this reflects the physical lane number. Wrong or missing information may affect analysis results. Required when inputs are FASTQ files. | | string | 1 | |
| total_reads | True | Total number of reads that align to the reference. | | integer | 525600 | |
| mean_coverage | False | Mean coverage for whole genome sequencing, or mean target coverage for whole exome and targeted sequencing, collected from Picard Tools. | | integer | 60 | |
| reference_genome | True | Reference genome version. | | string | GRCH38 | |
| FFPE | True | Is the sample preserved in FFPE | "True", "False" | boolean | False | |
| PI_name | True | Principal Investigator of the project | | string | Fonseca | True |
| project | True | Short name of the project | | string | impact trial | True |
| organism | True | Binomial name of organism with full genus name | "Homo sapiens", "Mus musculus" | string | Homo sapiens | |
