# Proteomics Manifest Readme

| Column Name | Required | Explanation | Allowed Values | Data Type | Example Entry | BTI Derived |
| ---- | ---- | ---- | ---- | ---- | ---- |  ---- |
| participant_id | True | Unique identifier for the participant from whom the sample was collected | | string | PT007 | True |
| event_id | True | Unique identifier for the clinical event associated with the participant; formerly sample_id | | string | SM8182-86886 | True |
| aliquot_id | True | Unique identifier for a specific aliquot | | string | AL54774975_T_Prot | True |
| external_participant_id | False | External, user-provided (non-unique) identifier for participants from whom the sample was collected | | string | P007 | |
| cohort_participant_id | False | Participant identifier as used within a specific cohort/study; interchangeable with external_participant_id when the two differ | | string | COH-PT1899 | |
| external_event_id | False | External, user-provided (non-unique) identifier for events linked to the same participant; formerly external_sample_id | | string | 8182-86886 | |
| external_aliquot_id | False | External, user-provided identifier linked to a specific aliquot (if leveraged for multiple assays, comprised of aliquot_id + T/N + assay performed) | | string | 54774975_T_Prot | |
| sample_type | True | Text term that represents a description of the kind of tissue collected with respect to disease status | "Tumor", "Normal", "Virus-infected", "Unknown", "Not Reported" | string | Normal | |
| tumor_descriptor | True | Descriptor of tumor status or clinical tumor context for the sample; must be NA for normal samples | "Deceased", "Initial CNS Tumor", "Metastatic", "Post-treatment", "Primary Tumor", "Progressive", "Progressive Disease Post-Mortem", "Recurrence", "Relapse", "Residual", "Second Malignancy", "Unknown", "NA" | string | NA | |
| composition | True | Tissue type the collected sample comes from | "Bone Marrow", "Buffy Coat", "Derived Cell Line", "Not Available", "Not Reported", "Patient Derived Xenograft", "Xenograft", "Patient Derived Organoid", "Peripheral Blood Mononuclear Cells", "Peripheral Whole Blood", "Saliva", "Solid Tissue", "Umbilical Cord Blood", "Patient-Derived T Cells", "Patient-Derived Primary Cells", "iPSC-Derived Organoid", "Cerebrospinal Fluid", "Embryonic Stem Cell Derived Cell Line" |  string | Bone Marrow | |
| bio_replicate | False | Label identifying the biological replicate this sample represents | | string | Rep1 | |
| dose_1 | False | Dose for treatment_1 in a simultaneous combination treatment | | string | 10 nM | |
| dose_2 | False | Dose for treatment_2 in a simultaneous combination treatment | | string | 20 nM | |
| treatment_1 | False | First component of a simultaneous combination treatment administered or applied to the sample | | string | temozolomide | |
| treatment_2 | False | Second component of a simultaneous combination treatment administered or applied to the sample | | string | radiation | |
| cell_line_composition | False | Culture media used for the cell line. Required when composition is "Derived Cell Line" | | string | DMEM/F12 | |
| cell_line_passage | False | Numeric passage number for the cell line. Required when composition is "Derived Cell Line" | | integer | 12 | |
| timepoint | False | Timepoint associated with the treatment, collection, or experiment | | string | 24h | |
| parental_model_id | False | Identifier for the parental model. Required for model-derived samples, including cell lines, xenografts, organoids, and other derived cell-line models; use this value for participant_id for model submissions | | string | MODEL-PARENT-001 | |
| model_id | False | Identifier for the submitted model, including genetically modified cell lines or other model derivatives. Required for model-derived samples, including cell lines, xenografts, organoids, and other derived cell-line models | | string | MODEL-GM-001 | |
| local_dir_path | False | SMB directory path on the L Drive for the source data | | string | smb://cnmc.org/cri/Lab/CancerImmunology-BTI | |
| aws_s3_path | False | S3 URI for the submitted data location | | string | s3://bucket/prefix | |
| sequencing_batch | False | Sequencing batch identifier | | string | 30-XXXXXXXX | |
| proteomics_experiment | True | The type of omics experiment that the sample was subject to. This will be a proteomics-based data, by default, but this should specify the type of proteomics data. | "Proteome", "Ubiquitylome", "Phosphoproteome", "Acetylome", "Glycoproteome", "Metabolome", "Lipidome" | string | Metabolome | |
| file_name | True | Name of the file | | string | NCI-11Plex-13-F12A-z11358.mzML | |
| file_format | True | Format of the file | "FASTQ", "BAM", "BAI", "CRAM", "CRAI", "GVCF", "VCF", "TBI", "MAF", "PDF", "HTML", "DCM", "IDAT", "SVS", "GPR", "CNS", "TXT", "PNG", "CSV", "PED", "SEG", "TAR", "TSV", "mzML", "raw" | string | mzML | |
| file_size | True | Reported file size in bytes | | integer | 235000 | |
| file_hash_type | True | Hash algorithm used to generate file hash | "MD5", "SHA1", "SHA256", "SHA512", "ETag" | string | MD5 | |
| file_hash_value | True | Full has value of the file | | string | 938c2cc0dcc05f2b68c4287040cfcf71 | |
| sequencing_center | False | Name of the center generating sequencing data | | string | Harvard Med School | |
| platform | True | Name of the platform used to obtain data | | string | Orbitrap Fusion Lumos | |
| experimental_strategy | True | Name of the type of experiment being performed | | string | Proteomics | |
| acquisition_type | True | Data acquisition type | | string | DDA | |
| ion_fragmentation | True | Reporter ion MS level | | string | MS2 | |
| enrichment_approach | True | Enrichment method used for phospho, ubiquitin, acetyl, or other enrichment | | string | metabolome | |
| quantification_technique | True | Approach used for peptide quantification | | string | Stable isotopic labeling | |
| quantification_labeling_method | True | Method used for labeling or NA if label-free | | string | L-Lysine SILAC | |
| quantification_label_id | True | Specific label used or NA if label-free | | string | 127N | |
| chromatography_approach | True | Column type used for liquid chromatography | | string | C18 | |
| fractionation_approach | True | Method used to fractionate sample. | | string | reverse-phase HPLC | |
| fraction_number | True | Number of fractions generated for sample. | | integer | 12 | |
| PI_name | True | Principal Investigator of the project | | string | Fonseca | True |
| project | True | Short name of the project | | string | impact trial | True |
| organism | True | Binomial name of organism with full genus name | "Homo sapiens", "Mus musculus" | string | Homo sapiens | |
| host_organism | False | Host organism binomial name when the sequenced sample is a xenograft. Required when compisition is "Patient Derived Xenograft" or "Xenograft" | "Mus musculus" | string | Mus musculus | True |
