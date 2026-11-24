## Table 2 — Sample Metadata

Contains 192 samples and 38 columns. Each row describes one sample.

| Column | Description | Example |
|---|---|---|
| `ID` | Sample identifier used to match samples with Table 4. | IA13 |
| `Group` | Sample type combined with sampling time. | Individual - 1st time point |
| `Sample_type` | Sample category. Collection details need confirmation. | Individual, Pen |
| `Time` | Sampling stage. Exact timing needs confirmation. | 1st time point |
| `AMR_seq_pool` | Sequencing pool label for AMR data. | Pool 3 |
| `microbiome_seq_pool` | Sequencing pool label for microbiome data. | Pool 1 |
| `Group_num` | Numeric grouping identifier; exact meaning needs confirmation. | 5 |
| `Pair_label` | Pairing label; exact pairing rules need confirmation. | Individual_5 |
| `Pair_ID` | Numeric pairing identifier; exact meaning needs confirmation. | 5 |
| `Feedlot` | Feedlot code. | 42 |
| `Feedlot_categories` | Text label corresponding to the feedlot code. | Feedlot_42 |
| `PEN.ID_num` | Pen-related identifier; coding scheme needs confirmation. | 420118 |
| `AMR_raw_paired_reads` | Sequencing count labelled as raw paired reads. | 6885106 |
| `AMR_QC_paired_reads` | Sequencing count labelled as quality-controlled paired reads. | 6770930 |
| `AMR_filter_removed` | Count removed during filtering; criteria need confirmation. | 2631898 |
| `AMR_filter_proportion` | Filtering proportion; denominator needs confirmation. | 0.38225962 |
| `AMR_nonhost_paired_reads` | Sequencing count labelled as non-host paired reads. | 4253208 |
| `Parenteral_ADD`, `Feed_ADD`, `Total_ADD` | Numeric ADD measures by administration route and overall. Meaning and units need confirmation. | — |
| Other `*_ADD` columns | ADD measures organised by drug category and administration route. Definitions need confirmation. | — |
| `DOF` | Numeric field; meaning and units need confirmation. | 78 |
| `DOF_cat` | Category code associated with DOF; boundaries need confirmation. | 3 |
| `resistome_raw_mapped_reads` | Count labelled as raw reads mapped to the resistome. | 198122 |
| `resistome_CSS_counts` | Resistome count summary labelled CSS; calculation needs confirmation. | 11703.80435 |
| `AMR_class_Richness` | Richness measure for AMR classes; counting criteria need confirmation. | 14 |
| `AMR_mech_Richness` | Richness measure for AMR mechanisms; counting criteria need confirmation. | 33 |
| `AMR_class_Shannon` | Shannon diversity measure for AMR classes. | 1.584569033 |
| `AMR_mech_Shannon` | Shannon diversity measure for AMR mechanisms. | 2.503078592 |


## Table 4 — Resistome Count Matrix

Contains 1,422 gene-reference rows and 192 sample columns,
plus the first column containing gene-reference identifiers.

- **Rows:** Gene-reference entries.
- **Columns:** Sample identifiers, such as PA49, IA30, and PE48.
- **Cells:** Recorded counts for each gene-reference entry in each sample.
  Exact counting units need confirmation.
- **First column:** Unnamed column containing identifiers and annotations
  separated by the pipe symbol (`|`).
- **Connection to Table 2:** All 192 sample column names match values in
  Table 2's ID column.

### Example gene-reference entry

`MEG_1000|Drugs|Aminoglycosides|Aminoglycoside_O-nucleotidyltransferases|ANT6`

This entry includes a reference identifier and several annotation labels.
Their formal definitions should be checked against the source documentation.

| Gene-reference entry | Final annotation | Count in PA49 |
|---|---|---|
| MEG_1000 | ANT6 | 427 |
| MEG_1001 | ANT6 | 157 |
| MEG_1002 | ANT6 | 25 |

Different gene-reference entries can share the same final annotation.
These rows should not be assumed to be duplicates.

## Questions to Clarify

1. What do the sample-ID prefixes mean?
2. What do Group_num, Pair_label, and Pair_ID represent?
   Which identify repeated samples from the same animal or pen?
3. How were Individual and Pen samples collected?
4. What exact dates or study stages do the three time points represent?
5. What does ADD mean, and what are its units and calculation method?
6. What do DOF and DOF_cat mean, and how are the categories defined?
7. What does MLS mean in the ADD column names?
8. What does CSS mean, and how was resistome_CSS_counts calculated?
9. Which filtering steps were used, and what denominator was used for
   AMR_filter_proportion?
10. Which database defines the MEG identifiers and annotation fields?
11. Are Table 4 values raw read counts, paired-read counts, or processed
    counts? How should zeros be interpreted?
12. How were the richness and Shannon diversity measures calculated?

## File Notes

- Both CSV files begin with a descriptive title row.
- The second row contains the actual column headers.
- Missing values should remain missing rather than being replaced with zero.