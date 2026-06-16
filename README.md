# MCAV_FL-DEP_2026_Task_8

Whole-genome sequencing of *Montastraea cavernosa* broodstock and sexually produced juveniles from NSU's land-based coral nursery (SE Florida) for parentage assignment, effective population size estimation, and linking parental genotype to offspring thermal tolerance (CBASS). FL DEP Agreement C5A9EC, Task 8.

---

**PI:** Matias Gomez-Corrales & Ronen Liberman  
**Institution:** Nova Southeastern University (NSU)  
**Funding:** Florida Department of Environmental Protection (DEP) — Coral Reef Restoration, Phase VII (Agreement C5A9EC)  
**Species:** *Montastraea cavernosa*

---

## Sequencing

| Parameter | Details |
|-----------|---------|
| Platform | Illumina NovaSeq X (10B flow cell) |
| Mode | 2×150 bp paired-end |
| Run | 20260610_LH00339_0235_A23KNNCLT3 (June 10, 2026) |
| ICBR project | GE-8936 |
| Libraries | 28 total: 9 juveniles, 13 broodstock colonies, 2 sperm samples, 4 technical replicates |
| BioProject | [PRJNA1478717](https://www.ncbi.nlm.nih.gov/bioproject/PRJNA1478717) |
| SRA Submission | SUB16257907 |
| BioSample accessions | SAMN60904239–SAMN60904266 |
| SRA run accessions | RUN:50613713–RUN:50613740 |

---

## Repository Contents

| File | Description |
|------|-------------|
| `MCAV_DEP_2026_GE-8936_RawData_Transfer.Rmd` | Documents raw FASTQ transfer from ICBR (Globus), rsync to NSU Sphyrna HPC, fastp quality filtering (SLURM array), and Aspera upload to NCBI SRA |
| `MCAV_DEP_2026_GE-8936_Deliverables_Tables.Rmd` | Renders Task 8 deliverable tables and QC figures: per-sample coverage depth, filtered reads, % ≥Q30, and SRA accession table with active NCBI links |

---

## Quality Filtering

Raw reads were processed with **fastp** using:

```
-q 20 -u 20 -n 5 --detect_adapter_for_pe --correction --length_required 50 -w 4
```

Mean coverage after filtering: **23.1×** (range: 16.2×–29.5×) against the *M. cavernosa* reference genome (448.4 Mb; Rippe et al. 2021).

---

## Dependencies

- R ≥ 4.2
- `tidyverse`, `DT`, `knitr`, `kableExtra`

---

## References

- Chen S. et al. (2018). fastp: an ultra-fast all-in-one FASTQ preprocessor. *Bioinformatics* 34(17):i884–i890.
- Korneliussen T.S. et al. (2014). ANGSD: Analysis of Next Generation Sequencing Data. *BMC Bioinformatics* 15:356.
- Rippe J.P. et al. (2021). Environmental specialization and cryptic genetic divergence in two massive coral species from the Florida Keys Reef Tract. *Molecular Ecology*. doi:10.1111/mec.15931.
