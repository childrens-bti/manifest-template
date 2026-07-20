# RNAseq, MiRNAseq, and TIRTL-Seq Manifest Readme

For TIRTL-seq, one completed manifest represents one plate. Each FASTQ has one row, and paired R1/R2 files from the same well use the same `well_name`. Bioassay assignment is performed after manifest creation and produces the pipeline-ready TSV with one `Bioassay_ID` repeated across every row in the plate.

| Column Name | Required | Explanation | Allowed Values | Data Type | Example Entry | BTI Derived |
| ---- | ---- | ---- | ---- | ---- | ---- |  ---- |
| participant_id | True | Unique identifier for the participant from whom the sample was collected | | string | PT1899 | True |
| event_id | True | Unique identifier for the clinical event associated with the participant; formerly sample_id | | string | SM7316-11566 | True |
| aliquot_id | True | Unique identifier for a specific aliquot | | string | AL1549608_T_WGS | True |
| external_participant_id | False | External, user-provided (non-unique) identifier for participants from whom the sample was collected | | string | PID1899 | |
| cohort_participant_id | False | Participant identifier as used within a specific cohort/study; interchangeable with external_participant_id when the two differ | | string | COH-PT1899 | |
| external_event_id | False | External, user-provided (non-unique) identifier for events linked to the same participant; formerly external_sample_id | | string | 7316-11566 | |
| external_aliquot_id | False | External, user-provided identifier linked to a specific aliquot (if leveraged for multiple assays, comprised of aliquot_id + T/N + assay performed) | | string | 1549608_T_WGS | |
| sample_type | True | Text term that represents a description of the kind of tissue collected with respect to disease status | "Tumor", "Normal", "Virus-infected", "Unknown", "Not Reported" | string | Normal | |
| tumor_descriptor | True | Descriptor of tumor status or clinical tumor context for the sample; must be NA for normal samples | "Deceased", "Initial CNS Tumor", "Metastatic", "Post-treatment", "Primary Tumor", "Progressive", "Progressive Disease Post-Mortem", "Recurrence", "Relapse", "Residual", "Second Malignancy", "Unknown", "NA" | string | NA | |
| composition | True | Tissue type the collected sample comes from | "Bone Marrow", "Buffy Coat", "Derived Cell Line", "Not Available", "Not Reported", "Patient Derived Xenograft", "Xenograft", "Patient Derived Organoid", "Peripheral Blood Mononuclear Cells", "Peripheral Whole Blood", "Saliva", "Solid Tissue", "Umbilical Cord Blood", "Patient-Derived T Cells", "Patient-Derived Primary Cells", "iPSC-Derived Organoid", "Cerebrospinal Fluid", "Embryonic Stem Cell Derived Cell Line" |  string | Bone Marrow | |
| bio_replicate | False | Label identifying the biological replicate this sample represents | | string | Rep1 | |
| dose_1 | False | Dose for treatment_1 in a simultaneous combination treatment | | string | 10 nM | |
| dose_2 | False | Dose for treatment_2 in a simultaneous combination treatment | | string | 20 nM | |
| treatment_1 | False | First component of a simultaneous combination treatment administered or applied to the sample | | string | temozolomide | |
| treatment_2 | False | Second component of a simultaneous combination treatment administered or applied to the sample | | string | radiation | |
| cell_line_composition | False | Culture media used for the cell line, for a "Derived Cell Line" composition | | string | DMEM/F12 | |
| cell_line_passage | False | Numeric passage number for the cell line, for a "Derived Cell Line" composition | | integer | 12 | |
| timepoint | False | Timepoint associated with the treatment, collection, or experiment | | string | 24h | |
| parental_model_id | False | Identifier for the parental model. Required for model-derived samples, including cell lines, xenografts, organoids, and other derived cell-line models; use this value for participant_id for model submissions | | string | MODEL-PARENT-001 | |
| model_id | False | Identifier for the submitted model, including genetically modified cell lines or other model derivatives. Required for model-derived samples, including cell lines, xenografts, organoids, and other derived cell-line models | | string | MODEL-GM-001 | |
| local_dir_path | False | SMB directory path on the L Drive for the source data | | string | smb://cnmc.org/cri/Lab/CancerImmunology-BTI | |
| aws_s3_path | False | S3 URI for the submitted data location | | string | s3://bucket/prefix | |
| sequencing_batch | False | Sequencing batch identifier | | string | 30-XXXXXXXX | |
| well_name | TIRTL-Seq only | Plate coordinate for the well represented by the FASTQ. Paired R1/R2 files must share the same value. | Plate coordinates A1 through P24 | string | A1 | |
| file_name | True | Name of the file | | string | NCI-11Plex-13-F12A-z11358.fastq | |
| file_format | True | Format of the file | "FASTQ", "BAM", "BAI", "CRAM", "CRAI", "GVCF", "VCF", "TBI", "MAF", "PDF", "HTML", "DCM", "IDAT", "SVS", "GPR", "CNS", "TXT", "PNG", "CSV", "PED", "SEG", "TAR", "TSV", "mzML", "raw" | string | FASTQ | |
| file_size | True | Reported file size in bytes | | integer | 529600 | |
| file_hash_type | True | Hash algorithm used to generate file hash | "MD5", "SHA1", "SHA256", "SHA512", "ETag" | string | MD5 |
| file_hash_value | True | Full has value of the file | | string | 938c2cc0dcc05f2b68c4287040cfcf71 | |
| sequencing_center | False | Name of the center generating sequencing data | | string | Harvard Med School | |
| platform | True | Name of the platform used to obtain data | "Complete Genomics", "Illumina", "Ion Torrent", "LS454", "SOLiD", "ONT", "DNBSEQ", "PacBio SMRT Cell", "Other" | string | Illumina | |
| instrument_model | False | Specific model of sequencing instrument used. | string | Model name of the instrument used for sequencing | NovaSeq 6000 | |
| experimental_strategy | True | The sequencing strategy used to generate the data file. | "RNA-Seq", "miRNA-Seq", "Ribo-Seq", "long-read RNA-Seq", "Flash-Seq", "TIRTL-Seq" | string | RNA-Seq | |
| library_selection | True | Library selection method. | "Affinity Enrichment", "Hybrid Selection", "miRNA Size Fractionation", "PCR", "Poly-T Enrichment", "Random","rRNA Depletion", "Ribosome-protected fragments", "Other" | string | PCT | |
| library_strand | True | Library strandedness. | "Stranded", "Unstranded", "First Stranded", "Second Stranded", "Not Applicable" | string | Stranded | |
| library_prep | True | Library prep method. | "polyA", "totalRNAseq", "Other" | string | polyA | |
| RNA_library | RNA/miRNA only | Library category. For miRNA-Seq, use "small RNA first-stranded". For unstranded polyA libraries, use "poly-A unstranded". Not required for TIRTL-Seq. | "exome capture", "poly-A", "poly-A stranded", "poly-A unstranded", "RPFs", "total RNA stranded", "total RNA unstranded", "small RNA first-stranded" | string | total RNA stranded | True |
| is_paired_end | True | If fastq/bam files, are the reads paired end? | "True", "False" | boolean | True | |
| read_pair_number | False | Denotes whether a submitted FASTQ file contains forward (R1) or reverse (R2) reads for paired-end sequencing. Required when inputs are FASTQ files. | "R1", "R2", "NA" | string | R1 | |
| flow_cell_barcode | False | Flow cell barcode. Wrong or missing information may affect analysis results. Required when inputs are FASTQ files. | | string | H0164ALXX140820 | |
| lane_number | False | The basic machine unit for sequencing. For Illumina machines, this reflects the physical lane number. Wrong or missing information may affect analysis results. Required when inputs are FASTQ files. | | string | 1 | |
| total_reads | False | Total number of reads that align to the reference. | | integer | 525600 | |
| reference_genome | True | Reference genome version. | | string | GRCH38 | |
| FFPE | True | Is the sample preserved in FFPE | "True", "False" | boolean | False | |
| PI_name | True | Principal Investigator of the project | | string | Fonseca | True |
| project | True | Short name of the project | | string | impact trial | True |
| organism | True | Binomial name of organism with full genus name | "Homo sapiens", "Mus musculus" | string | Homo sapiens | |
| host_organism | False | Host organism binomial name when the sequenced sample is a xenograft. Required when compisition is "Patient Derived Xenograft" or "Xenograft" | "Mus musculus" | string | Mus musculus | True |
