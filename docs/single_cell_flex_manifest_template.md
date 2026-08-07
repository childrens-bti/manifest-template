# Single Cell 10x Flex Manifest Readme

This template is for 10x Genomics Flex / Fixed RNA Profiling gene expression submissions. For multiplexed pools, represent the manifest in long format: one row per Cell Ranger sample, probe barcode, and physical data file. A pooled FASTQ may therefore appear on multiple rows, once for each `cellranger_sample_id` / `probe_barcode_id` assignment. Cell Ranger names this config field `probe_barcode_ids`, but this manifest intentionally stores one `probe_barcode_id` per row; if a sample uses multiple probe barcodes, expand those assignments across rows rather than storing a delimited list.

| Column Name | Required | Explanation | Allowed Values | Data Type | Example Entry | BTI Derived |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| participant_id | True | Unique identifier for the participant from whom the sample was collected | | string | P_5P2QIUH2 | True |
| event_id | True | Unique identifier for the clinical event associated with the participant; formerly sample_id | | string | S_0000012 | True |
| aliquot_id | True | Unique identifier for a specific aliquot | | string | AL_0000025_T_10xFlexGEX | True |
| external_participant_id | False | External, user-provided identifier for the participant from whom the sample was collected | | string | PID1899 | |
| cohort_participant_id | False | Participant identifier as used within a specific cohort/study; interchangeable with external_participant_id when the two differ | | string | COH-PT1899 | |
| external_event_id | False | External, user-provided identifier for events linked to the same participant; formerly external_sample_id | | string | 7316-11566 | |
| external_aliquot_id | False | External, user-provided identifier linked to a specific aliquot | | string | 1549608_T_FLEX | |
| organism | True | Binomial name of organism with full genus name | "Homo sapiens", "Mus musculus" | string | Homo sapiens | |
| host_organism | False | Host organism binomial name when the sequenced sample is a xenograft | "Mus musculus" | string | Mus musculus | True |
| cell_entity | False | The type of single cell entity | | string | Whole Cell | |
| sample_type | True | Description of the kind of tissue collected with respect to disease status | "Tumor", "Normal", "Virus-infected", "Unknown", "Not Reported" | string | Tumor | |
| tumor_descriptor | True | Descriptor of tumor status or clinical tumor context for the sample; must be NA for normal samples | "Deceased", "Initial CNS Tumor", "Metastatic", "Post-treatment", "Primary Tumor", "Progressive", "Progressive Disease Post-Mortem", "Recurrence", "Relapse", "Residual", "Second Malignancy", "Unknown", "NA" | string | Primary Tumor | |
| composition | True | Tissue type the collected sample comes from | "Bone Marrow", "Buffy Coat", "Derived Cell Line", "Not Available", "Not Reported", "Patient Derived Xenograft", "Xenograft", "Patient Derived Organoid", "Peripheral Blood Mononuclear Cells", "Peripheral Whole Blood", "Saliva", "Solid Tissue", "Umbilical Cord Blood", "Patient-Derived T Cells", "Modified T Cells", "Patient-Derived Primary Cells", "iPSC-Derived Organoid", "Cerebrospinal Fluid", "Embryonic Stem Cell Derived Cell Line" | string | Solid Tissue | |
| bio_replicate | False | Label identifying the biological replicate this sample represents | | string | Rep1 | |
| dose_1 | False | Dose for treatment_1 in a simultaneous combination treatment | | string | 10 nM | |
| dose_2 | False | Dose for treatment_2 in a simultaneous combination treatment | | string | 20 nM | |
| treatment_1 | False | First component of a simultaneous combination treatment administered or applied to the sample | | string | temozolomide | |
| treatment_2 | False | Second component of a simultaneous combination treatment administered or applied to the sample | | string | radiation | |
| cell_line_composition | False | Culture media used for the cell line, for a Derived Cell Line composition | | string | DMEM/F12 | |
| cell_line_passage | False | Numeric passage number for the cell line, for a Derived Cell Line composition | | integer | 12 | |
| timepoint | False | Timepoint associated with the treatment, collection, or experiment | | string | 24h | |
| parental_model_id | False | Identifier for the parental model. Required for model-derived samples | | string | CNMC-XD760 | |
| model_id | False | Identifier for the submitted model, including genetically modified cell lines or other model derivatives | | string | CNMC-XD760-mCherry-Luciferase | |
| cellranger_sample_id | True | Cell Ranger multi `sample_id` for this biological sample in the Flex pool | | string | FLEX_SAMPLE_001 | |
| probe_barcode_id | True | One 10x probe barcode assigned to this biological sample in the Cell Ranger multi samples section. If Cell Ranger lists multiple probe barcodes for one sample, represent each sample/probe barcode assignment as separate manifest rows rather than storing a delimited list | | string | BC001 | |
| library_pool_id | True | Identifier for the pooled 10x Flex library or FASTQ pool shared by one or more Cell Ranger samples | | string | FLEX_POOL_01 | |
| local_dir_path | False | SMB directory path on the L Drive for the source data | | string | smb://cnmc.org/cri/Lab/CancerImmunology-BTI | |
| aws_s3_path | False | S3 URI for the submitted data location | | string | s3://bucket/prefix | |
| sequencing_batch | False | Sequencing batch identifier | | string | 30-XXXXXXXX | |
| file_name | True | Name of the file. In pooled Flex data, the same file may appear once per Cell Ranger sample assignment | | string | FLEX_POOL_01_S1_L001_R1_001.fastq.gz | |
| file_format | True | Format of the file | "FASTQ", "BAM", "BAI", "CRAM", "CRAI", "GVCF", "VCF", "TBI", "MAF", "PDF", "HTML", "DCM", "IDAT", "SVS", "GPR", "CNS", "TXT", "PNG", "CSV", "PED", "SEG", "TAR", "TSV", "mzML", "raw" | string | FASTQ | |
| file_size | True | Reported file size in bytes | | integer | 529600 | |
| file_hash_type | True | Hash algorithm used to generate file hash | "MD5", "SHA1", "SHA256", "SHA512", "ETag" | string | MD5 | |
| file_hash_value | True | Full hash value of the file | | string | 938c2cc0dcc05f2b68c4287040cfcf71 | |
| sequencing_center | False | Name of the center generating sequencing data | | string | Harvard Med School | |
| platform | True | Name of the platform used to obtain data | "Complete Genomics", "Illumina", "Ion Torrent", "LS454", "SOLiD", "ONT", "DNBSEQ", "Other" | string | Illumina | |
| instrument_model | False | Specific model of sequencing instrument used | | string | NovaSeq 6000 | |
| experimental_strategy | True | The sequencing strategy used to generate the data file | "10x Flex GEX" | string | 10x Flex GEX | |
| end_bias | True | The end of the cDNA molecule that is preferentially sequenced | "3'-end", "5'-end", "Full-length" | string | 3'-end | |
| library_type | True | Library modality | "GEX" | string | GEX | |
| library_selection | True | Library selection method | "Affinity Enrichment", "Hybrid Selection", "miRNA Size Fractionation", "PCR", "Poly-T Enrichment", "Random", "rRNA Depletion", "Other" | string | Hybrid Selection | |
| library_strand | True | Library strandedness | "Stranded", "Unstranded", "First Stranded", "Second Stranded", "Not Applicable" | string | Not Applicable | |
| library_construction | True | Library construction method including version | | string | 10x Flex | |
| feature_type | True | 10x feature type represented by the library | "gex" | string | gex | |
| probe_set | True | 10x Flex transcriptome probe set name and version used for alignment/counting. Use a stable probe set name/version rather than a local machine-specific path | | string | Chromium_Mouse_Transcriptome_Probe_Set_v2.0.0_GRCm39-2024-A | |
| probe_spike_in | True | Were custom probes spiked into the standard 10x Flex probe set? | "True", "False" | boolean | False | |
| probe_spike_in_description | False | Description of custom spike-in probes when `probe_spike_in` is True. Use NA when no custom probes were spiked in | | string | CD123/B7H3 CAR construct spike-in probes | |
| total_reads | False | Total number of reads that align to the reference | | integer | 525600 | |
| UMI_barcode_read | True | The type of read that contains the UMI barcode | "index1", "index2", "read1", "read2", "Not Applicable" | string | read1 | |
| UMI_barcode_offset | True | Offset in sequence of the UMI barcode | | integer | 12 | |
| UMI_barcode_size | True | Length of the UMI barcode sequence | | integer | 12 | |
| cell_barcode_read | True | The type of read that contains the cell barcode | "index1", "index2", "read1", "read2", "Not Applicable" | string | read1 | |
| cell_barcode_offset | True | Offset in sequence of the cell barcode | | integer | 0 | |
| cell_barcode_size | True | Length of the cell barcode sequence | | integer | 16 | |
| cDNA_read | True | The type of read that contains the cDNA read | "index1", "index2", "read1", "read2", "Not Applicable" | string | read2 | |
| cDNA_read_offset | True | Offset in sequence of the cDNA read | | integer | 0 | |
| is_paired_end | True | If FASTQ/BAM files, are the reads paired end? | "True", "False", "NA" | boolean/string | True | |
| read_pair_number | False | Denotes whether a submitted FASTQ file contains forward (R1) or reverse (R2) reads for paired-end sequencing. Required when inputs are FASTQ files | "R1", "R2", "NA" | string | R1 | |
| flow_cell_barcode | False | Flow cell barcode. Required when inputs are FASTQ files | | string | H0164ALXX | |
| lane_number | False | Physical sequencing lane number. Required when inputs are FASTQ files | | string | 1 | |
| is_adapter_trimmed | False | Were adapters trimmed from sequencing data? Required when inputs are FASTQ files | "True", "False" | boolean | False | |
| adapter_sequencing | False | Base sequence of the sequencing adapter. Required when adapters were not trimmed | | string | AGATCGGAAGAGCGTCGTGTAGGGAAAGAGTGT | |
| target_cell_number | False | Target number of cells to recover for the assay | | integer | 10000 | |
| reference_genome | True | Reference genome version | | string | GRCh38 | |
| FFPE | True | Is the sample preserved in FFPE? | "True", "False" | boolean | False | |
| PI_name | True | Principal Investigator of the project | | string | Fonseca | True |
| project | True | Short name of the project | | string | RBT | True |
