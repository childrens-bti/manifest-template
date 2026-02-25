# Proteomics Manifest Readme

| Column Name | Required | Explanation | Allowed Values | Data Type | Example Entry |
| ---- | ---- | ---- | ---- | ---- | ---- |
| external_patient_id | False | Non-unique identifier for patients from whom the sample was collected | | string | P007 |
| external_sample_id | True | Non-unique identifier for samples linked to the same clinical event | | string | 8182-86886 |
| external_aliquot_id | True | Unique id linked to a specific aliquot (if leveraged for multiple assays, comprised of aliquot_id + T/N + assay performed) | | string | 54774975_T_Prot |
| sample_type | True | Text term that represents a description of the kind of tissue collected with respect to disease status | "Tumor", "Normal", "Unknown", "Not Reported" | string | Normal |
| composition | True | Tissue type collected sample comes from | "Bone Marrow", "Buffy Coat", "Derived Cell Line", "Not Available", "Not Reported", "Patient Derived Xenograft", "Patient Derived Organoid", "Peripheral Whole Blood", "Saliva", "Solid Tissue", "Umbilical Cord Blood", "Patient-Derived T Cells", "iPSC-Derived Organoid", "Cerebrospinal Fluid", "Embryonic Stem Cell Derived Cell Line" |  string | Bone Marrow |
| proteomics_experiment | True | The type of omics experiment that the sample was subject to. This will be a proteomics-based data, by default, but this should specify the type of proteomics data. | "Proteome", "Ubiquitylome", "Phosphoproteome", "Acetylome", "Glycoproteome", "Metabolome", "Lipidome" | string | Metabolome |
| file_name | True | Name of the file | | string | NCI-11Plex-13-F12A-z11358.mzML |
| file_format | True | Format of the file | "FASTQ", "BAM", "BAI", "CRAM", "CRAI", "GVCF", "VCF", "TBI", "MAF", "PDF", "HTML", "DCM", "IDAT", "SVS", "GPR", "CNS", "TXT", "PNG", "CSV", "PED", "SEG", "TAR", "TSV", "mzML", "raw" | string | mzML |
| file_size | True | Reported file size in bytes | | integer | 235000 |
| file_hash_type | True | Hash algorithm used to generate file hash | "MD5", "SHA1", "SHA256", "SHA512", "ETag" | string | MD5 |
| file_hash_value | True | Full has value of the file | | string | 938c2cc0dcc05f2b68c4287040cfcf71 |
| sequencing_center | True | Name of the center generating sequencing data | | string | Harvard Med School |
| platform | True | Name of the platform used to obtain data | | string | Orbitrap Fusion Lumos |
| experimental_strategy | True | Name of the type of experiment being performed | | string | Proteomics |
| acquisition_type | True | Data acquisition type | | string | DDA |
| ion_fragmentation | True | Reporter ion MS level | | string | MS2 |
| enrichment_approach | True | Enrichment method used for phospho, ubiquitin, acetyl, or other enrichment | | string | metabolome |
| quantification_technique | True | Approach used for peptide quantification | | string | Stable isotopic labeling |
| quantification_labeling_method | True | Method used for labeling or NA if label-free | | string | L-Lysine SILAC |
| quantification_label_id | True | Specific label used or NA if label-free | | string | 127N |
| chromatography_approach | True | Column type used for liquid chromatography | | string | C18 |
| fractionation_approach | True | Method used to fractionate sample. | | string | reverse-phase HPLC |
| fraction_number | True | Number of fractions generated for sample. | | integer | 12 |
| PI_name | True | Principal Investigator of the project | | string | Fonseca |
| project | True | Short name of the project | | string | impact trial |
| organism | True | Binomial name of organism with full genus name | "Homo sapiens", "Mus musculus" | string | Homo sapiens |
