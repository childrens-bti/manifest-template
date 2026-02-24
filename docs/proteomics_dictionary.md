# Proteomics Manifest Readme

| Column Name | Required | Explanation | Allowed Values |
| ---- | ---- | ---- | ---- |
| external_patient_id | False | Non-unique identifier for patients from whom the sample was collected | |
| external_sample_id | True | Non-unique identifier for samples linked to the same clinical event | |
| external_aliquot_id | True | Unique id linked to a specific aliquot (if leveraged for multiple assays, comprised of aliquot_id + T/N + assay performed) | |
| sample_type | True | Text term that represents a description of the kind of tissue collected with respect to disease status | "Tumor", "Normal", "Unknown", "Not Reported" |
| composition | True | Tissue type collected sample comes from | "Bone Marrow", "Buffy Coat", "Derived Cell Line", "Not Available", "Not Reported", "Patient Derived Xenograft", "Patient Derived Organoid", "Peripheral Whole Blood", "Saliva", "Solid Tissue", "Umbilical Cord Blood", "Patient-Derived T Cells", "iPSC-Derived Organoid", "Cerebrospinal Fluid", "Embryonic Stem Cell Derived Cell Line" |
| proteomics_experiment_type | True | The type of omics experiment that the sample was subject to. This will be a proteomics-based data, by default, but this should specify the type of proteomics data. | "Proteome", "Ubiquitylome", "Phosphoproteome", "Acetylome", "Glycoproteome", "Metabolome", "Lipidome" |
| file_name | True | Name of the file | |
| file_format | True | Format of the file | "FASTQ", "BAM", "BAI", "CRAM", "CRAI", "GVCF", "VCF", "TBI", "MAF", "PDF", "HTML", "DCM", "IDAT", "SVS", "GPR", "CNS", "TXT", "PNG", "CSV", "PED", "SEG", "TAR", "TSV", "mzML", "raw" |
| file_size | True | Reported file size in bytes | |
| file_hash_type | True | Hash algorithm used to generate file hash | "MD5", "SHA1", "SHA256", "SHA512", "ETag" |
| file_hash_value | True | Full has value of the file | |
| sequencing_center | True | Name of the center generating sequencing data | |
| platform | True | Name of the platform used to obtain data | |
| acquisition_type | True | Data acquisition type | |
| ion_fragmentation | True | Reporter ion MS level | |
| enrichment_approach | True | Enrichment method used for phospho, ubiquitin, acetyl, or other enrichment | |
| quantification_technique | True | Approach used for peptide quantification | |
| quantification_labeling_method | True | Method used for labeling or NA if label-free | |
| quantification_label_id | True | Specific label used or NA if label-free | |
| chromatography_approach | True | Column type used for liquid chromatography | |
| fractionation_approach | True | Method used to fractionate sample. | |
| fraction_number | True | Number of fractions generated for sample. | |
| PI_name | True | Principal Investigator of the project | |
| project | True | Short name of the project | |
| organism | True | Binomial name of organism with full genus name | "Homo sapiens", "Mus musculus" |
