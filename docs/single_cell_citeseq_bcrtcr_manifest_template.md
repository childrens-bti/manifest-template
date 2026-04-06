# Single Cell CITE-SEQ BCR/TCR Manifest Readme

| Column Name | Required | Explanation | Allowed Values | Data Type | Example Entry | BTI Derived |
| ---- | ---- | ---- | ---- | ---- | ---- |  ---- |
| external_patient_id | False | Non-unique identifier for patients from whom the sample was collected | | string | PID1899 | |
| external_sample_id | True | Non-unique identifier for samples linked to the same clinical event | | string | 7316-11566 | |
| external_aliquot_id | True | Unique id linked to a specific aliquot (if leveraged for multiple assays, comprised of aliquot_id + T/N + assay performed) | | string | 1549608_T_WGS | |
| organism | True | Binomial name of organism with full genus name | "Homo sapiens", "Mus musculus" | string | Homo sapiens | |
| host_organism | False | Host organism binomial name when the sequenced sample is a xenograft. Required when compisition is "Patient Derived Xenograft" or "Xenograft" | "Mus musculus" | string | Mus musculus | True |
cell_entity
| sample_type | True | Text term that represents a description of the kind of tissue collected with respect to disease status | "Tumor", "Normal", "Unknown", "Not Reported" | string | Normal | |
| composition | True | Tissue type the collected sample comes from | "Bone Marrow", "Buffy Coat", "Derived Cell Line", "Not Available", "Not Reported", "Patient Derived Xenograft", "Xenograft", Patient Derived Organoid", "Peripheral Whole Blood", "Saliva", "Solid Tissue", "Umbilical Cord Blood", "Patient-Derived T Cells", "iPSC-Derived Organoid", "Cerebrospinal Fluid", "Embryonic Stem Cell Derived Cell Line" |  string | Bone Marrow | |
| file_name | True | Name of the file | | string | NCI-11Plex-13-F12A-z11358.fastq | |
| file_format | True | Format of the file | "FASTQ", "BAM", "BAI", "CRAM", "CRAI", "GVCF", "VCF", "TBI", "MAF", "PDF", "HTML", "DCM", "IDAT", "SVS", "GPR", "CNS", "TXT", "PNG", "CSV", "PED", "SEG", "TAR", "TSV", "mzML", "raw" | string | FASTQ | |
| file_size | True | Reported file size in bytes | | integer | 529600 | |
| file_hash_type | True | Hash algorithm used to generate file hash | "MD5", "SHA1", "SHA256", "SHA512", "ETag" | string | MD5 |
| file_hash_value | True | Full has value of the file | | string | 938c2cc0dcc05f2b68c4287040cfcf71 | |
| sequencing_center | True | Name of the center generating sequencing data | | string | Harvard Med School | |
| platform | True | Name of the platform used to obtain data | "Complete Genomics", "Illumina", "Ion Torrent", "LS454", "SOLiD", "ONT", "DNBSEQ", "Other" | string | Illumina | |
| instrument_model | True | Specific model of sequencing instrument used. | string | Model name of the instrument used for sequencing | NovaSeq 6000 | |
| experimental_strategy | True | The sequencing strategy used to generate the data file. | "CITE-Seq", "scTCR-Seq", "scBCR-Seq" | string | CITE-Seq | |
end_bias
library_type
| library_selection | True | Library selection method. | "Affinity Enrichment", "Hybrid Selection", "miRNA Size Fractionation", "PCR", "Poly-T Enrichment", "Random","rRNA Depletion", "Ribosome-protected fragments", "Other" | string | PCT | |
| library_strand | True | Library strandedness. | "Stranded", "Unstranded", "First Stranded", "Second Stranded", "Not Applicable" | string | Stranded | |
| library_construction | True | The library construction method including version. | | string | 10X V3 | |
feature_type
chain_type
total_reads
| UMI_barcode_read | True | The type of read that contains the UMI barcode. | "index1", "index2", "read1", "read2", "Not Applicable" | string | index1 | |
| UMI_barcode_offset | True | The offset in sequence of the UMI barcode. | | integer | 16 | |
| UMI_barcode_size | True | The length of the UMI barcode sequence. | | integer | 10 | |
| cell_barcode_read | | True | The type of read that contains the cell barcode. | "index1", "index2", "read1", "read2", "Not Applicable" | string | read2 | |
| cell_barcode_offset | True | The offset in sequence of the cell barcode. | | integer | 16 | |
| cell_barcode_size | True | The length of the cell barcode sequence. | | integer | 10 | |
| cDNA_read | True | The type of read that contains the cDNA read. | "index1", "index2", "read1", "read2", "Not Applicable" | string | read1 | |
| cDNA_read_offset | True | The offset in sequence of the cDNA read. | | integer | 0 | |
| is_paired_end | True | If fastq/bam files, are the reads paired end? | "True", "False" | boolean | True | |
| read_pair_number | False | Denotes whether a submitted FASTQ file contains forward (R1) or reverse (R2) reads for paired-end sequencing. Required when inputs are FASTQ files. | "R1", "R1", "Not Applicaable" | string | R1 | |
| flow_cell_barcode | False | Flow cell barcode. Wrong or missing information may affect analysis results. Required when inputs are FASTQ files. | | string | H0164ALXX140820 | |
| lane_number | False | The basic machine unit for sequencing. For Illumina machines, this reflects the physical lane number. Wrong or missing information may affect analysis results. Required when inputs are FASTQ files. | | string | 1 | |
| is_adapter_trimmed | False | Were adapters trimmed from sequencing data? Required when inputs are FASTQ files. | "True", "False" | boolean | True | |
| adapter_sequencing | False | Base sequence of the sequencing adapter. Required when adapters were not trimmed. | | string | GCAT | |
| reference_genome | True | Reference genome version. | | string | GRCH38 | |
| FFPE | True | Is the sample preserved in FFPE | "True", "False" | boolean | False | |
| PI_name | True | Principal Investigator of the project | | string | Fonseca | True |
| project | True | Short name of the project | | string | impact trial | True |
