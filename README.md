# Data Manifest Templates

![License](https://img.shields.io/badge/license-BSD--2--Clause-blue.svg)

**Central repository for data manifest templates and their validation rules**, maintained by the Brain Tumor Institute (BTI) Bioinformatics Core @ Children's National Hospital.

This repository defines the required structure, fields, and allowed values for each supported data manifest so that submissions can be generated and validated consistently across projects and tools.

The validation framework builds upon rules originally established at Children's Hospital of Philadelphia Center for Data-Driven Discovery in Biomedicine and used in [their CLI](https://github.com/d3b-center/d3b-dff-cli), with further extensions and enhancements introduced here.

---

## Contents

- [Repository Structure](#repository-structure)
- [Supported Manifest Types](#supported-manifest-types)
- [Validation Rules](#validation-rules)
- [Shared Field Conventions](#shared-field-conventions)
- [Excel Workbooks](#excel-workbooks)
- [Using This Repo](#using-this-repo)
- [License](#license)

## Repository Structure

| Path | Description |
|---|---|
| [`validation_json/`](validation_json/) | The validation schema (`validation_rules_schema.json`) that defines required fields, types, allowed values, and cross-field dependencies for every manifest type. |
| [`manifest_templates/`](manifest_templates/) | Blank CSV templates — one per manifest type — with the exact column headers expected by the validator. |
| [`docs/`](docs/) | Human-readable, per-manifest field documentation: what each column means, whether it's required, allowed values, data type, and an example entry. |
| [`excel_templates/`](excel_templates/) | Auto-generated `.xlsx` workbook per manifest type, combining the docs table and CSV template into one file for lab use (see [Excel Workbooks](#excel-workbooks) below). |

## Supported Manifest Types

| Manifest | Template | Field Documentation |
|---|---|---|
| WGS / WXS / Targeted Panel | [CSV](manifest_templates/wgs_wxs_panel_manifest_template.csv) | [Docs](docs/wgs_wxs_panel_manifest_template.md) |
| RNAseq / miRNAseq | [CSV](manifest_templates/rnaseq_mirnaseq_manifest_template.csv) | [Docs](docs/rnaseq_mirnaseq_manifest_template.md) |
| Single Cell — 10x Flex | [CSV](manifest_templates/single_cell_flex_manifest_template.csv) | [Docs](docs/single_cell_flex_manifest_template.md) |
| Single Cell — CITE-Seq / BCR / TCR | [CSV](manifest_templates/single_cell_citeseq_bcrtcr_manifest_template.csv) | [Docs](docs/single_cell_citeseq_bcrtcr_manifest_template.md) |
| Single Cell — Spatial | [CSV](manifest_templates/single_cell_spatial_manifest_template.csv) | [Docs](docs/single_cell_spatial_manifest_template.md) |
| Methylation | [CSV](manifest_templates/methylation_manifest_template.csv) | [Docs](docs/methylation_manifest_template.md) |
| Proteomics | [CSV](manifest_templates/proteomics_manifest_template.csv) | [Docs](docs/proteomics_manifest_template.md) |

## Validation Rules

All validation logic lives in [`validation_json/validation_rules_schema.json`](validation_json/validation_rules_schema.json). Rules are organized as:

- **`common_rules`** — fields shared across every manifest type (identifiers, file metadata, organism, etc.)
- **Type-specific rule sets** (`DNAseq_rules`, `RNAseq_rules`, `single_cell_rules`, `pacbio_longread_rules`, `methylation_rules`, `proteomics_rules`) — fields and constraints unique to that assay type, including conditional requirements (`dependencies`) based on values like `experimental_strategy` or `file_format`.

## Shared Field Conventions

- **Event identifiers:** `event_id` replaces the former `sample_id` field, and `external_event_id` replaces the former `external_sample_id` field.
- **Internal ID nomenclature:** `participant_id`, `event_id`, and `aliquot_id` are assigned automatically by the [data-modeling](https://github.com/childrens-bti/data-modeling) id-bank pipeline, not hand-authored. `participant_id` is `P_` + 8 random alphanumeric characters; `event_id` is `S_` + a 7-digit zero-padded sequential number; `aliquot_id` is `AL_` + a 7-digit zero-padded sequential number, optionally suffixed `_T`/`_N` (from `sample_type`) plus an assay abbreviation (e.g. `RNA`, `WGS`, `Ribo`, `Methyl`, `Prot`, `CITE`, `scRNA`) when the submission didn't supply its own `external_aliquot_id` — this keeps the same physical aliquot's outputs distinguishable across multiple assay-specific manifests. `external_participant_id`, `cohort_participant_id`, `external_event_id`, and `external_aliquot_id` are free-form, submitter-provided values and follow no fixed pattern.
- **Tumor descriptor:** `tumor_descriptor` is required for every manifest. Normal samples must use `NA`; other allowed sample types may use an allowed tumor descriptor or `NA` where appropriate.
- **Treatment fields:** `treatment_1` and `treatment_2` describe simultaneous combination-treatment components. `dose_1` and `dose_2` are the corresponding doses for those treatment components.
- **Cell-line fields:** `cell_line_composition` records the culture media and `cell_line_passage` is a numeric passage number. Both are optional, including when `composition` is `Derived Cell Line`, because this curation data may not be available for every sample.
- **Model identifiers:** `parental_model_id` and `model_id` are required for model-derived samples such as cell lines, xenografts, organoids, and other derived cell-line models.
- **File platform:** `file_platform` indicates the source platform where files are stored and from where they are harmonized and is required for every manifest. Allowed values: `bti_aws` (BTI AWS S3 internal storage), `cgc` (Cancer Genomics Cloud), `kids_first` (Kids First DRC), `sra` (Sequence Read Archive), `synapse` (Synapse platform). Use DRS links from external platforms (cgc, kids_first, sra, synapse) or `bti_aws` for internal S3 storage. When `file_platform` is `bti_aws`, `aws_s3_path` is required; otherwise `aws_s3_path` and `local_dir_path` are optional.
- **Path fields:** `local_dir_path` expects an SMB path under `smb://cnmc.org/cri/Lab/CancerImmunology-BTI` and is optional. `aws_s3_path` expects an S3 URI and is required only when `file_platform` is `bti_aws`.
- **Instrument platform:** `instrument_platform` (formerly `platform`) specifies the sequencing or assay platform (e.g., Illumina, PacBio, ONT). Allowed values vary by manifest type — see type-specific validation rules.
- **File-size thresholds:** file-size cutoffs are strategy-specific custom rules. Do not apply a general cutoff across all data types.

## Excel Workbooks

For lab members who prefer filling out a spreadsheet over a raw CSV, [`excel_templates/`](excel_templates/) contains a generated `.xlsx` workbook per manifest type with two tabs:

1. **Data Dictionary** — the field documentation table from the corresponding `docs/*.md` file.
2. **Manifest Template** — the same column headers as the CSV template, with dropdown validation on any column that has an Allowed Values list (e.g. `sample_type`, `composition`).

These workbooks are generated by [`scripts/generate_manifest_xlsx.py`](scripts/generate_manifest_xlsx.py) and kept in sync automatically by the [`generate-manifest-xlsx`](.github/workflows/generate-manifest-xlsx.yml) GitHub Action: on any push commit touching `docs/` or `manifest_templates/`, the workflow regenerates the workbooks and commits them straight back onto that PR's branch, so the updated `.xlsx` files land in the same PR as the change that caused them — no separate follow-up PR needed.

To regenerate locally: `pip install -r scripts/requirements.txt && python scripts/generate_manifest_xlsx.py`.

## Using This Repo

Any other repository or workflow that consumes these manifests or validation rules should include this repository as a [git submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules) rather than copying files directly, so downstream consumers stay in sync with schema updates:

```bash
git submodule add git@github.com:childrens-bti/manifest-template.git
```

## License

Distributed under the [BSD 2-Clause License](LICENSE).
