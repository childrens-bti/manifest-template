# Methylation Manifest Readme

| Column Name | Required | Explanation | Allowed Values | Data Type | Example Entry | BTI Derived |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| external_patient_id | False | Non-unique identifier for patients from whom the sample was collected | | string | PID1899 | |
| external_sample_id | True | Non-unique identifier for samples linked to the same clinical event | | string | 7316-11566 | |
| external_aliquot_id | True | Unique id linked to a specific aliquot (if leveraged for multiple assays, comprised of aliquot_id + T/N + assay performed) | | string | 1549608_T_WGS | |
| sample_type | True | Text term that represents a description of the kind of tissue collected with respect to disease status | "Tumor", "Normal", "Virus-infected", "Unknown", "Not Reported" | string | Normal | |
| composition | True | Tissue type the collected sample comes from | "Bone Marrow", "Buffy Coat", "Derived Cell Line", "Not Available", "Not Reported", "Patient Derived Xenograft", "Xenograft", Patient Derived Organoid", "Peripheral Whole Blood", "Saliva", "Solid Tissue", "Umbilical Cord Blood", "Patient-Derived T Cells", "iPSC-Derived Organoid", "Cerebrospinal Fluid", "Embryonic Stem Cell Derived Cell Line" |  string | Bone Marrow | |
| file_name | True | Name of the file | | string | NCI-11Plex-13-F12A-z11358.fastq | |
| file_format | True | Format of the file | "IDAT"| string | IDAT| |
| file_size | True | Reported file size in bytes | | integer | 529600 | |
| file_hash_type | True | Hash algorithm used to generate file hash | "MD5", "SHA1", "SHA256", "SHA512", "ETag" | string | MD5 | |
| file_hash_value | True | Full has value of the file | | string | 938c2cc0dcc05f2b68c4287040cfcf71 | |
| sequencing_center | True | Name of the center generating sequencing data | | string | Harvard Med School | |
| platform | True | Name of the platform used to obtain data | "Illumina Infinium HumanMethylation450", "Illumina Infinium HumanMethylationEPIC", "Illumina Infinium HumanMethylationEPICv2", "Illumina Infinium HumanMethylation27k", "Roche NimbleGen MethylationSeq", "Agilent SurePrint Methyl-Seq" | string | Illumina | |
| experimental_strategy | True | The sequencing strategy used to generate the data file. | "Methylation", "Methylation Microarray" | string | Methylation | |
| FFPE | True | Is the sample preserved in FFPE | "True", "False" | boolean | False | |
| PI_name | True | Principal Investigator of the project | | string | Fonseca | True |
| project | True | Short name of the project | | string | impact trial | True |
| organism | True | Binomial name of organism with full genus name | "Homo sapiens", "Mus musculus" | string | Homo sapiens | |
| host_organism | False | Host organism binomial name when the sequenced sample is a xenograft. Required when compisition is "Patient Derived Xenograft" or "Xenograft" | "Mus musculus" | string | Mus musculus | True |
