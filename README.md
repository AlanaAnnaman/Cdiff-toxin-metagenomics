# Metagenomic Analysis of Large Clostridial Toxin Homologs in *Clostridioides difficile*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform](https://img.shields.io/badge/Platform-Linux-lightgrey.svg)](https://github.com/username/cdiff-toxin-metagenomics)

## Overview

This study investigates the prevalence and genetic diversity of non-A/B Large Clostridial Toxin (LCT) homologs, such as TcsL and Tcnα, in clinical *Clostridioides difficile* isolates using shotgun metagenomics. While *C. difficile* infection (CDI) is primarily attributed to toxins A (TcdA) and B (TcdB), recent genomic evidence suggests the pathogen may harbor additional toxin homologs that contribute to disease variability.

## Key Findings

- Successfully developed a robust metagenomic pipeline for clinical stool sample analysis
- Achieved >99.8% microbial purity in 5/6 analyzed samples after host decontamination
- **Detected 17 differentially abundant KEGG orthologs** between CDI+ and CDI- groups:
  - **15 ribosomal proteins enriched in CDI+ patients** (indicating translational stress)
  - **2 ribosomal proteins enriched in CDI- patients** (K02968, K02911)
  - Most significant finding: K02970 (LDA score: 4.61, p = 0.046) and K02968 (LDA score: 4.73, p = 0.050)
- Established methodological framework for large-scale toxin homolog screening

### Sequencing Quality and Decontamination
- One sample (HC375) was excluded due to low read count
- Sample HC370 showed higher human DNA contamination (24.12%) but was retained for analysis
- Average of 799,725 reads per sample after quality control

### Functional Gene Diversity
- **KEGG ortholog richness**: Significantly reduced in CDI+ patients (p = 0.0495)
- **Pielou's evenness**: No significant difference between groups (p = 0.2752)

### Beta Diversity Analysis
- Principal coordinates analysis showed visual separation between groups
- PC1 explained 31.38% of variance, PC2 explained 27.01%
- PERMANOVA p = 0.100 (likely due to small sample size)

### Differential Abundance Analysis
LEfSe analysis identified 17 significantly different KEGG orthologs with the following key findings:
- **15 ribosomal proteins enriched in CDI+ patients** (indicating translational stress)
- **2 ribosomal proteins enriched in CDI- patients** (K02968, K02911)

## Research Impact

This work addresses a critical gap in CDI pathogenesis by:
- Moving beyond the TcdA/TcdB-centric paradigm
- Providing the first systematic survey methodology for the full LCT repertoire
- Establishing bioinformatics infrastructure for clinical toxin screening
- Contributing to next-generation therapeutic target identification

## Repository Structure

```
├── manuscript/           # Research paper and supplementary materials
├── scripts/             # Bioinformatics pipeline scripts
│   ├── 01_preprocessing/
│   ├── 02_decontamination/
│   ├── 03_functional_analysis/
│   └── 04_statistical_analysis/
├── data/                # Sample metadata and data availability info
├── results/             # Key outputs and statistical results
├── docs/                # Additional documentation
└── requirements.txt     # Software dependencies
```

## Methodology

### Sample Processing
- **Samples**: Clinical stool samples (n=7 preliminary analysis)
  - CDI+ samples: 4 (HC370, HC374, HC375, HC376)
  - CDI- samples: 3 (KR00448, KR00449, KR00450)
- **DNA Extraction**: ZymoBioMICS DNA Miniprep kit
- **Sequencing**: Aviti Element platform (2 x 150 bp paired-end)
- **Average Reads**: 799,725 ± 27,848 per sample

### Bioinformatics Pipeline

#### 1. Quality Control and Preprocessing
```bash
# fastp v0.23.2 for adapter trimming and quality filtering
fastp -i ${input_R1} -I ${input_R2} \
      -o ${output_R1} -O ${output_R2} \
      -t ${trim_R1} -T ${trim_R2} \
      --html ${sample}_fastp.html
```

#### 2. Host Sequence Removal
```bash
# Kraken2 v2.1.2 against GRCh38 reference
kraken2 --db ${human_db} \
        --paired ${clean_R1} ${clean_R2} \
        --unclassified-out ${sample}_clean#.fastq \
        --report ${sample}_kraken2_report.txt
```

#### 3. Functional Profiling
```bash
# HUMAnN 3.0 with KEGG annotation
humann --input ${concat_reads} \
       --output ${humann_output} \
       --protein-database ${uniref90} \
       --nucleotide-database ${chocophlan}
```

#### 4. Statistical Analysis
```r
# Alpha diversity (Shannon index, Pielou's evenness)
# Beta diversity (Bray-Curtis, PERMANOVA)
# Differential abundance (LEfSe analysis)
```

## Technical Requirements

### Software Dependencies
- fastp v0.23.2
- Kraken2 v2.1.2
- HUMAnN 3.0
- R v4.3.1
- Python 3.8+

### R Packages
```r
install.packages(c("ggpubr", "tidyverse", "RColorBrewer", 
                   "knitr", "rmarkdown", "vegan"))
if (!requireNamespace("devtools", quietly = TRUE)){
    install.packages("devtools")
}
devtools::install_github("jbisanz/qiime2R")
```

### Database Requirements
- GRCh38 human reference genome
- KEGG ortholog database
- UniRef90 protein database
- ChocoPhlAn nucleotide database

## Key Results Summary

### Microbiome Composition
- High abundance of metabolic enzymes (L-lactate dehydrogenase, glycerol-3-phosphate dehydrogenase)
- Evidence of anaerobic fermentation conducive to *C. difficile* proliferation
- Active *C. difficile* genes detected in CDI+ samples (K00604, K00613, K01478)

### Clinical Implications
- Establishes methodological foundation for large-scale toxin screening
- Provides evidence for functional microbiome disruption in CDI
- Supports development of toxin-targeted therapeutics

## Future Directions

1. **Scale-up Analysis**: Expand to full cohort (n=100) for definitive prevalence assessment
2. **Targeted Screening**: Develop specific primers for known LCT homologs
3. **Strain-level Analysis**: Investigate toxin diversity within *C. difficile* populations
4. **Clinical Correlation**: Associate toxin profiles with disease severity metrics

## Data Availability

Due to patient privacy considerations, raw sequencing data cannot be publicly shared. However, processed functional profiles and statistical outputs are available upon reasonable request to qualified researchers.

## Citation

If you use this methodology or find these results useful, please cite:

```
Annamanthadoo, A. (2025). Beyond A and B: Investigating the Prevalence and 
Diversity of Large Clostridial Toxin Homologs in Clostridioides difficile. 
```



**Alana Annamanthadoo**  
*Master of Science in Bioinformatics*  


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Institutional Review Board, University of Michigan
- Bioinformatics community for open-source tools and databases

---

*For questions about methodology, data access, or collaboration opportunities, please open an issue or contact [your.email@example.com].*

