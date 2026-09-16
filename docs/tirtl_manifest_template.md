# TIRTL-Seq Manifest Readme

Use this template for TIRTL-Seq submissions. One completed manifest represents one plate when well-level metadata is available. Each FASTQ file has one row; paired R1/R2 files from the same well must use the same `well_name` value when provided. Raw-mode submissions may omit `well_name` and contain only the FASTQ pair. Set `experimental_strategy` to `TIRTL-Seq` for every row.

| Column Name | Required | Explanation | Allowed Values | Data Type | Example Entry | BTI Derived |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| participant_id | True | Unique identifier for the participant from whom the sample was collected | | string | P_5P2QIUH2 | True |
| event_id | True | Unique identifier for the clinical event associated with the participant; formerly sample_id | | string | S_0000012 | True |
| aliquot_id | True | Unique identifier for a specific aliquot | | string | AL_0000025_T_RNA | True |
| external_participant_id | False | External, user-provided, non-unique identifier for the participant | | string | PID1899 | |
| cohort_participant_id | False | Participant identifier as used within a specific cohort or study | | string | COH-PT1899 | |
| external_event_id | False | External, user-provided identifier for the event; formerly external_sample_id | | string | 7316-11566 | |
| external_aliquot_id | False | External, user-provided identifier linked to a specific aliquot | | string | 1549608_T_RNA | |
| sample_type | True | Description of the kind of tissue collected with respect to disease status | "Tumor", "Normal", "Virus-infected", "Unknown", "Not Reported" | string | Normal | |
| tumor_descriptor | True | Descriptor of tumor status or clinical tumor context; use NA for normal samples | "Deceased", "Initial CNS Tumor", "Metastatic", "Post-treatment", "Primary Tumor", "Progressive", "Progressive Disease Post-Mortem", "Recurrence", "Relapse", "Residual", "Second Malignancy", "Unknown", "NA" | string | NA | |
| composition | True | Tissue type the collected sample comes from | "Bone Marrow", "Buffy Coat", "Derived Cell Line", "Not Available", "Not Reported", "Patient Derived Xenograft", "Xenograft", "Patient Derived Organoid", "Peripheral Blood Mononuclear Cells", "Peripheral Whole Blood", "Saliva", "Solid Tissue", "Umbilical Cord Blood", "Patient-Derived T Cells", "Modified T Cells", "Patient-Derived Primary Cells", "iPSC-Derived Organoid", "Cerebrospinal Fluid", "Embryonic Stem Cell Derived Cell Line" | string | Bone Marrow | |
| bio_replicate | False | Label identifying the biological replicate represented by the sample | | string | Rep1 | |
| dose_1 | False | Dose for treatment_1 in a simultaneous combination treatment | | string | 10 nM | |
| dose_2 | False | Dose for treatment_2 in a simultaneous combination treatment | | string | 20 nM | |
| treatment_1 | False | First component of a simultaneous combination treatment | | string | temozolomide | |
| treatment_2 | False | Second component of a simultaneous combination treatment | | string | radiation | |
| cell_line_composition | False | Culture media used for a derived cell line | | string | DMEM/F12 | |
| cell_line_passage | False | Numeric passage number for a derived cell line | | integer | 12 | |
| timepoint | False | Timepoint associated with treatment, collection, or experiment | | string | 24h | |
| parental_model_id | False | Identifier for the parental model; required for model-derived samples | | string | CNMC-XD760 | |
| model_id | False | Identifier for the submitted model; required for model-derived samples | | string | CNMC-XD760-mCherry-Luciferase | |
| local_dir_path | False | SMB path for the source data; required when file_source_platform is local_drive or bti_aws_and_local_drive | | string | smb://cnmc.org/cri/Lab/CancerImmunology-BTI | |
| aws_s3_path | False | S3 URI for the submitted data; required when file_source_platform is bti_aws or bti_aws_and_local_drive | | string | s3://bucket/prefix | |
| file_source_platform | True | Platform where files are stored and from which they are harmonized | "bti_aws", "local_drive", "bti_aws_and_local_drive", "cgc", "kids_first", "sra", "synapse" | string | bti_aws | |
| sequencing_batch | False | Sequencing batch identifier | | string | 30-XXXXXXXX | |
| well_name | False | Optional plate coordinate for the well represented by the FASTQ. Use the zero-padded format A01 through P24. Paired R1/R2 files from the same well must share the same value when provided. Leave blank for raw-mode submissions containing only a FASTQ pair. | Plate coordinates A01 through P24 | string | A01 | |
| file_name | True | Name of the submitted file | | string | NCI-11Plex-13-F12A-z11358.fastq | |
| file_format | True | Format of the submitted file | "FASTQ", "BAM", "BAI", "CRAM", "CRAI", "GVCF", "VCF", "TBI", "MAF", "PDF", "HTML", "DCM", "IDAT", "SVS", "GPR", "CNS", "TXT", "PNG", "CSV", "PED", "SEG", "TAR", "TSV", "mzML", "raw" | string | FASTQ | |
| file_size | True | Reported file size in bytes | | integer | 529600 | |
| file_hash_type | True | Hash algorithm used to generate the file hash | "MD5", "SHA1", "SHA256", "SHA512", "ETag" | string | MD5 | |
| file_hash_value | True | Full hash value of the file | | string | 938c2cc0dcc05f2b68c4287040cfcf71 | |
| sequencing_center | False | Name of the center generating the sequencing data | | string | Harvard Med School | |
| instrument_platform | True | Platform used to obtain the data | "Complete Genomics", "Illumina", "Ion Torrent", "LS454", "SOLiD", "ONT", "DNBSEQ", "PacBio SMRT Cell", "Other" | string | Illumina | |
| instrument_model | False | Specific model of sequencing instrument used | | string | NovaSeq 6000 | |
| experimental_strategy | True | Sequencing strategy used to generate the data file | "TIRTL-Seq" | string | TIRTL-Seq | |
| library_selection | True | Library selection method used for the TIRTL-Seq library | "Affinity Enrichment", "Hybrid Selection", "miRNA Size Fractionation", "PCR", "Poly-T Enrichment", "Random Fragmentation", "rRNA Depletion", "Ribosome-protected fragments", "Other" | string | Other | |
| library_strand | True | Library strandedness; use Not Applicable when strand is not meaningful for the assay | "Stranded", "Unstranded", "First Stranded", "Second Stranded", "Unknown", "Not Applicable" | string | Not Applicable | |
| library_prep | True | Library preparation method | "polyA", "totalRNAseq", "Other" | string | Other | |
| RNA_library | False | RNA library category. This field is optional for TIRTL-Seq and may be left blank when it does not apply | "exome capture", "fragmented", "poly-A", "poly-A stranded", "poly-A unstranded", "RPFs", "total RNA stranded", "total RNA unstranded", "small RNA first-stranded" | string | | |
| is_paired_end | True | Whether FASTQ or BAM reads are paired end | "True", "False" | boolean | True | |
| read_pair_number | False | Whether a FASTQ file contains forward or reverse reads; required for FASTQ files | "R1", "R2", "NA" | string | R1 | |
| flow_cell_barcode | False | Flow cell barcode; required for FASTQ files | | string | H0164ALXX140820 | |
| lane_number | False | Physical sequencing lane number when applicable | | string | 1 | |
| is_adapter_trimmed | False | Whether adapters were trimmed from sequencing data | "True", "False", "Unknown" | boolean/string | False | |
| adapter_sequencing | False | Base sequence of the sequencing adapter when adapters were not trimmed | | string | AGATCGGAAGAGCGTCGTGTAGGGAAAGAGTGT | |
| total_reads | False | Total number of reads that align to the reference | | integer | 525600 | |
| reference_genome | False | Reference genome version; required when file_format is BAM or CRAM | | string | GRCh38 | |
| FFPE | True | Whether the sample is preserved in FFPE | "True", "False" | boolean | False | |
| PI_name | True | Principal Investigator of the project | | string | Fonseca | True |
| project | True | Short name of the project | | string | RBT | True |
| organism | True | Binomial name of the organism | "Homo sapiens", "Mus musculus" | string | Homo sapiens | |
| host_organism | False | Host organism for xenograft samples; required for Patient Derived Xenograft or Xenograft composition | "Mus musculus" | string | Mus musculus | True |
| reported_gender | False | Reported gender; required when organism is Homo sapiens | "Female", "Male", "Not Reported" | string | Not Reported | |
