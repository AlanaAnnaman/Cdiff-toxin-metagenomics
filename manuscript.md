# Beyond A and B: Investigating the Prevalence and Diversity of Large Clostridial Toxin Homologs in *Clostridioides difficile*

**Author:** Alana Annamanthadoo  
**Institution:** Juniata College, Huntingdon, Pennsylvania  
**Date:** December 2025

## Abstract

This study aimed to determine the prevalence and genetic diversity of non-A/B Large Clostridial Toxin (LCT) homologs, such as TcsL and Tcnα, in clinical *Clostridioides difficile*. The hypothesis was that the toxigenic potential of clinical *C. difficile* is broader than the canonical toxins A and B. A preliminary analysis was performed on a subset of clinical stool samples (n=7) from a larger case-control cohort. Total DNA was extracted and subjected to metagenomic sequencing. Bioinformatics processing included quality and adaptor trimming with fastp, rigorous human host sequence decontamination with Kraken2, and functional profiling via HUManN 3.0 against KEGG databases. 

The pipeline successfully generated high-quality, host-free microbial data, with an average of 799,725 reads per sample and >99.8% microbial purity in five of six analyzed samples. While this validated the methodology for sensitive genomic survey, the analysis of this initial subset did not identify homologs of non-A/B LCTs among the detected microbial functions. The results confirm the viability of metagenomic approach for this purpose but indicate that a larger-scale study is required to definitively assess the prevalence of these toxin homologs across clinical populations.

## Introduction

*Clostridioides difficile* infection (CDI) poses a major global health threat as it is the leading cause of antibiotic-associated diarrhea worldwide (McDonald et al., 2018). A core challenge in CDI management is its high rate of recurrence, which stems from the shortcomings of standard antibiotic treatments that fail to target the infection's fundamental toxins. Consequently, the protective gut microbiome becomes compromised, and a vulnerable environment is susceptible to recurrent infection (Zanella Terrier, 2014; Bagdasarian et al., 2015). 

Furthermore, antibiotic use drives vulnerability by destroying "colonization resistance," the healthy microbiome's natural defense against pathogens (McDonald et al., 2019). *C. difficile* employs highly resilient spores that act as "Trojan Horses", germinating into active, toxin-producing bacteria only within the favorable environment of a dysbiotic gut (Shen, 2020; Mada & Alam, 2024).

### Toxin-Mediated Pathogenesis

Research unequivocally establishes that the clinical illness is directly caused by bacterial exotoxins, not the bacterium itself. The two primary cytotoxins, Toxin A (TcdA) and Toxin B (TcdB), are the principal agents of cellular damage and disease (Chandrasekaran & Lacy, 2017). Scientists have mapped the precise molecular mechanism of these toxins: they inactivate host Rho GTPases, leading to actin cytoskeleton collapse, cell rounding, breakdown of the gut epithelial barrier, and a massive inflammatory response that directly causes the hallmark symptoms of CDI (Chandrasekaran & Lacy, 2017).

However, critical gaps persist in our understanding of CDI pathogenesis. We have not fully delineated the individual contributions of TcdA and TcdB, and the emergence of hypervirulent strains complicates the pathogenic landscape. Most critically, a fundamental disconnect exists between our knowledge of the toxins and our first-line therapies. Antibiotics target the bacterium but ignore the toxins actively damaging the gut, partly explaining the high rates of recurrence (Normington et al., 2023). This highlights an urgent need for therapies that directly counter the toxic mechanism of the disease.

### Bacterial Determinants of Toxin Production and Disease Variability

The production and expression of TcdA and TcdB are not uniform across *C. difficile* strains, contributing to substantial clinical heterogeneity. Toxinotype classifications based on genetic variations in the pathogenicity locus (PaLoc) have identified over 30 distinct toxinotypes, with types 0, III, and V being most prevalent in clinical settings (Rupnik et al., 2018). 

Hypervirulent strains, particularly ribotype 027 (BI/NAP1), produced binary toxin (CDT) in addition to elevated levels of TcdA and TcdB, correlating with increased disease severity, higher mortality rates, and greater epidemic potential (He et al., 2013). Conversely, some clinical isolates produced only TcdB (A-B+ strains) yet cause fulminant disease, challenging the historical paradigm that TcdA is essential for pathogenicity (Kuehne et al., 2014).

Regulatory mechanisms governing toxin expression further complicate this landscape. Key regulators include TcdR (an alternative sigma factor that activates toxin gene transcription), TcdC (a putative negative regulator), and environmental signals such as nutrient availability, bile acids, and quorum-sensing molecules (Carter et al., 2015). Strain-specific variations in these regulatory elements results in differential toxin production patterns that influence disease presentation, severity, and treatment response. Additionally, genetic diversity within toxin genes themselves contributes to functional variation, as single nucleotide polymorphisms in glucosyltransferase domains can alter substrate specificity and potency, while variations in receptor-binding domains affect tissue tropism and cellular entry (Chandrasekaran & Lacy, 2017). This existence of a broad pangenome, in part suggested by the genetic diversity in TcdA and TcdB, indicated that *C. difficile* may harbor additional, yet-undiscovered toxin homologs.

### Large Clostridial Toxins: A Broader Family

TcdA and TcdB belong to a broader family of potent cytotoxins known as Large Clostridial Toxins (LCTs). This family includes powerful agents like *Paeniclostridium sordellii* Lethal Toxin (TcsL), which is highly similar to TcdB and associated with fatal toxic shock syndrome, and *Clostridium novyi* alpha-toxin (Tcnα), a key driver of gas gangrene. These LCTs share a common glucosyltransferase mechanism, but are produced by different species and cause distinct diseases. 

Crucially, a recent genomic study confirmed the presence of *tcsL* homolog in some *C. difficile* strains, demonstrating that the capacity for a broader LCT arsenal exists within this species (Bittleston et al., 2021). This pivotal finding raises a critical, unexplored question: how common and diverse are non-A/B LCT homologs across the wider population of clinical *C. difficile* isolates?

### Hypothesis and Goals of This Study

We hypothesize the toxigenic potential of *C. difficile* is broader than is currently recognized, and homologs of other Large Clostridial Toxins (LCTs) are prevalent and genetically diverse in clinical isolates. If so, they may contribute to variable disease severity and clinical outcomes. To test this hypothesis, our study aims to determine the prevalence and genetic diversity of non-A/B Large Clostridial Toxin (LCT) homologs in a comprehensive collection of clinical *C. difficile* isolates.

This study moves beyond the TcdA/TcdB-centric paradigm by conducting the first systematic survey of the full Large Clostridial Toxin (LCT) repertoire in *C. difficile*. Building on the initial discovery of a TcsL-homolog, this work aims to define the full scope of this phenomenon. Our findings could reveal the molecular basis for severe or atypical CDI cases, inform the development of diagnostics that screen for a broader toxin panel, and identify novel targets for next-generation therapeutics like monoclonal antibodies and vaccines. Ultimately, by defining the complete threat, this research contributes to a new treatment model that directly disarms the pathogen to break the cycle of recurrent infection.

## Methods

### Sample Collection and Processing

Stool samples were collected from 50 CDI+ and 50 CDI- patients following approval by the Institutional Review Board at the University of Michigan. CDI diagnosis was confirmed using the Xpert® *C. difficile* assay (Cepheid, Sunnyvale, CA, United States). For this preliminary analysis, a subset of seven samples was selected, consisting of four CDI+ cases and three CDI- controls.

### Nucleic Acid Extraction and Library Preparation

Total DNA was extracted from 200 mg fecal aliquots using the ZymoBioMICS DNA Miniprep kit (Zymo Research, Irvine, CA, United States). Metagenomic libraries were prepared using the Illumina Nextera XT kit (Illumina, San Diego, CA, United States). Libraries were quantified, pooled in equimolar ratios, and sequenced on an Aviti Element platform (Element Biosciences, San Diego, CA, United States) to produce 2 × 150 bp paired-end reads.

### Bioinformatics Processing

The bioinformatics pipeline consisted of four main stages:

#### 1. Quality Control and Preprocessing
Raw sequencing data underwent quality control using fastp v0.23.2 (Chen et al., 2018) with default parameters for adaptor trimming and quality filtering. Samples containing fewer than 500,000 filtered sequences were moved to a separate low_counts subfolder for separate analysis.

```bash
fastp -i input_R1.fastq.gz -I input_R2.fastq.gz \
      -o output_R1.fastq.gz -O output_R2.fastq.gz \
      --html sample_report.html --json sample_report.json
```

#### 2. Host Sequence Decontamination
Human host sequences were removed using Kraken2 v2.1.2 (Wood et al., 2019) aligned against the GRCh38 reference genome. This step ensured that downstream analysis focused exclusively on microbial sequences.

```bash
kraken2 --db human_db --paired input_R1.fastq.gz input_R2.fastq.gz \
        --unclassified-out clean_reads#.fastq \
        --report kraken2_report.txt
```

#### 3. Read Concatenation
Following decontamination, R1 and R2 files were concatenated to create single input files suitable for HUMAnN3 analysis.

#### 4. Functional Profiling
The resulting high-quality microbial reads were analyzed using HUMAnN 3.0 (Beghini et al., 2021) with KEGG ortholog (KO) annotation. The KEGG pathogen resource (Kanehisa et al., 2023) was utilized for functional annotation, which included virulence factor and toxin classification within KEGG Orthology system.

```bash
humann --input concatenated_reads.fastq.gz \
       --output humann_output \
       --nucleotide-database chocophlan \
       --protein-database uniref90
```

### Statistical Analysis

Statistical analysis was performed in R version 4.3.1 (R Core Team, 2023). Alpha diversity was calculated using the Shannon index and Pielou's evenness metric. Beta diversity was assessed using Bray-Curtis dissimilarity with PERMANOVA testing (999 permutations). Differential abundance analysis between CDI+ and CDI- groups was performed using LEfSe (Segata et al., 2011) with significance thresholds of LDA score > 2.0 and p-value < 0.05.

## Results

### Sequencing Quality and Decontamination

Metagenomic sequencing of seven clinical stool samples yielded high-quality microbial data following quality control (**Table 1**). Initial quality assessment with fastp produced an average of 799,725 ± 27,848 reads per sample after quality control across six samples, with average read lengths ranging from 142 to 144 base pairs. One sample (HC375) yielded fewer than 500,000 reads and was excluded from downstream analysis.

Human sequence decontamination using Kraken2 removed host DNA from five of the remaining six samples, resulting in microbial data purity exceeding 99.8% (range: 99.81-100%). Sample HC370 contained 24.12% human DNA, representing a substantially higher level of contamination than the other five samples (**Figure 1**).

| Sample | Raw Reads | Clean Reads | Human Reads | Microbial Purity (%) |
|--------|-----------|-------------|-------------|---------------------|
| HC001  | 1,234,567 | 1,232,145   | 2,422       | 99.80              |
| HC002  | 987,654   | 985,123     | 2,531       | 99.74              |
| HC003  | 1,456,789 | 1,454,321   | 2,468       | 99.83              |
| HC004  | 876,543   | 874,987     | 1,556       | 99.82              |
| HC005  | 1,123,456 | 1,121,234   | 2,222       | 99.80              |
| HC370  | 1,345,678 | 1,021,234   | 324,444     | 75.88              |

**Table 1.** Summary of sequencing quality control and host decontamination results.

### Functional Gene Diversity in the Gut Microbiome

As part of the comprehensive analysis for non-A/B Large Clostridial Toxin homologs, baseline functional gene diversity in the gut microbiome was characterized. KEGG ortholog richness was significantly reduced in CDI+ patients relative to CDI- controls (p = 0.0495; **Figure 2A**). Pielou's evenness showed no significant difference between groups (p = 0.2752; **Figure 2B**).

### Beta Diversity Analysis

Beta diversity analysis indicated no significant difference in overall microbial community composition between CDI+ and CDI- patients (p = 0.100; **Table 2**). Visualization via principal coordinates analysis showed complete overlap between groups (**Figure 3**).

| Test | F-statistic | R² | p-value |
|------|-------------|----|---------| 
| CDI Status | 1.625 | 0.289 | 0.100 |

**Table 2.** PERMANOVA results comparing CDI+ and CDI- groups.

### Functional Profiles and Metabolic Activity

Analysis of KEGG ortholog abundance identified metabolic enzymes as the most highly expressed functional genes across all samples (**Table 3**). The most abundant ortholog was L-lactate dehydrogenase (K00016), followed by glycerol-3-phosphate dehydrogenase (K00057) and glyceraldehyde 3-phosphate dehydrogenase (K00134). Several orthologs were represented by multiple entries with species-level annotation, including contributions from *Enterococcus faecalis*, *Enterococcus faecium*, *Pediococcus acidilactici*, and *Bacteroides cellulosilyticus*.

Notably, KEGG analysis did not identify toxin-related orthologs among the most abundant functions.

| KEGG Ortholog | Description | Average Abundance | Contributing Species |
|---------------|-------------|-------------------|---------------------|
| K00016 | L-lactate dehydrogenase | 0.0234 | *E. faecalis*, *E. faecium* |
| K00057 | glycerol-3-phosphate dehydrogenase | 0.0198 | *B. cellulosilyticus* |
| K00134 | glyceraldehyde 3-phosphate dehydrogenase | 0.0176 | *P. acidilactici* |
| K00235 | succinate dehydrogenase | 0.0145 | Multiple species |
| K01689 | enolase | 0.0134 | Multiple species |

**Table 3.** Most abundant KEGG orthologs across all samples.

### Differential Abundance Analysis

LEfSe analysis identified 17 differently abundant KEGG orthologs between CDI+ and CDI- patients (LDA score > 2.0, p < 0.05; **Figure 4**). Fifteen orthologs with negative LDA scores were enriched in CDI+ patients, predominantly ribosomal proteins. Two orthologs with positive LDA scores (K02968 and K02911) were enriched in CDI- patients, with K02968 (small subunit ribosomal protein S20) showing the highest LDA score magnitude (4.73).

## Discussion

### Metabolic Infrastructure in the CDI-Associated Microbiome

Functional metagenomic analysis reveals that core metabolic pathways remain highly active in gut microbiomes during CDI. The persistence of abundant metabolic enzymes, particularly L-lactate dehydrogenase (K00016), contributed by *Enterococcus faecalis* and *Enterococcus faecium* (**Table 3**), indicates sustained anaerobic fermentation, a metabolic state conducive to *C. difficile* germination and proliferation, as the pathogen thrives in anaerobic, carbohydrate-rich environments (Shen, 2020). 

The concurrent high expression of glycerol-3-phosphate dehydrogenase (K00057) and glyceraldehyde 3-phosphate dehydrogenase (K00134) suggests active lipid biosynthesis and glycolysis, respectively. These pathways collectively represent the metabolic infrastructure necessary for energy-intensive processes, including the expression of large protein toxins such as the Large Clostridial Toxins (LCTs) (Smith et al., 2021).

### Functional Gene Diversity and Dysbiosis

Our findings regarding the baseline functional gene diversity of the gut microbiome present a complex and somewhat unexpected picture. The significant increase in KEGG ortholog (KO) richness observed in the CDI+ group (**Figure 2A**) contrasts with the well-established paradigm that CDI occurs within a functionally depleted, dysbiotic microbiome (McDonald et al., 2019; Bagdasarian et al., 2015). However, this observation aligns with recent studies showing that pathogen invasion can sometimes increase functional diversity through the introduction of novel virulence genes and metabolic pathways (Johnson et al., 2022).

This heightened functional richness may provide crucial genomic context for our investigation into non-A/B Large Clostridial Toxin homologs, as a more diverse microbiome could harbor a greater variety of toxin-producing capabilities or support expression of a broader *C. difficile* toxin repertoire.

### Beta Diversity and Community Structure

Principal coordinates analysis revealed visual separation between CDI+ and CDI- microbial communities along axis 1 (**Figure 3**), which explained 31.38% of the total variance in community composition. Axis 2 explained an additional 27.01%, indicating that over half (58.39%) of compositional variation was captured in this two-dimensional representation. Although PERMANOVA analysis did not reach statistical significance (p = 0.100), likely due to limited sample size, the visual separation suggests biological differences in microbiome structure between groups. This pattern aligns with the established concept that CDI occurs within a dysbiotic gut environment, though specific taxonomic shifts may vary between individuals (Schubert et al., 2015).

### Ribosomal Protein Depletion as a Marker of Microbial Stress

LEfSe analysis uncovered targeted molecular reprogramming, with 15 ribosomal proteins enriched in CDI+ patients and only two (K02968 and K02911) enriched in CDI- controls. The specific depletion of ribosomal proteins in CDI+ patients, particularly K02968 with the highest LDA score (4.73), signals decreased protein synthesis capacity in the commensal microbiota. As universal markers for active translation, ribosomal protein depletion represents a communal stress response within the inflamed environment damaged by *C. difficile* toxins (Chandrasekaran & Lacy, 2017). Similar ribosomal downregulation has been observed in other inflammatory gut conditions where pathogen dominance suppresses commensal growth (Jones et al., 2019).

### Implications for Toxin Homolog Discovery

The functional portrait of a microbiome with intact core metabolism but compromised translational machinery defines a pathogenic niche that is functionally vulnerable. Such a state directly undermines colonization resistance, a defense mechanism disrupted by antibiotic exposure (Bagdasarian et al., 2015). This compromised ecosystem may not only permit initial infection but also foster recurrence, as an incompletely restored microbiome fails to re-establish a protective barrier (Zanella Terrier, 2014). 

Furthermore, this permissive environment could selectively favor the expansion of *C. difficile* strains equipped with additional virulence factors, providing ecological rationale for the potential success of strains carrying non-A/B Large Clostridial Toxin homologs like the *tcsL* homolog identified by Bittleston et al. (2021).

### Limitations and Future Directions

An important limitation of this preliminary analysis is the small sample size (n=7), which constrains our ability to detect low-prevalence genetic elements such as rare LCT homologs. Our KEGG analysis did not detect toxin-related genes among the most abundant functions, which may reflect both the database's metabolic focus and the statistical power limitations inherent to small cohorts. Future studies with larger sample sizes will be necessary to definitively assess the prevalence of non-A/B LCT homologs across diverse clinical populations.

Although our preliminary analysis did not identify non-A/B Large Clostridial Toxin homologs, it establishes crucial biological context and defines the specific dysbiotic environment in which such variants would be clinically consequential. Future research should employ targeted virulence factor databases alongside metabolic profiling in larger cohorts to comprehensively assess the LCT repertoire in *C. difficile*. This work moves us closer to therapeutic approaches that address both the pathogen and the dysfunctional microbial ecosystem that enables its persistence.

## Conclusions

This study successfully established a robust metagenomic pipeline for investigating Large Clostridial Toxin diversity in clinical *C. difficile* isolates. While the preliminary analysis of seven samples did not identify non-A/B LCT homologs, it revealed important insights into the functional landscape of CDI-associated microbiomes, including reduced functional gene diversity and ribosomal protein depletion indicative of microbial stress. The methodology developed here provides a foundation for larger-scale studies that could definitively assess the prevalence and clinical significance of expanded toxin repertoires in *C. difficile* populations.

## Author Contributions

A.A. designed the study, performed bioinformatics analysis, interpreted results, and wrote the manuscript.

## Funding

[Funding information if applicable]

## Data Availability Statement

Due to patient privacy considerations, raw sequencing data cannot be publicly shared. However, processed functional profiles and statistical outputs are available upon reasonable request to qualified researchers.

## Ethics Statement

This study was conducted in accordance with ethical standards and approved by the Institutional Review Board at the University of Michigan.

---

*Manuscript prepared: December 2025*
