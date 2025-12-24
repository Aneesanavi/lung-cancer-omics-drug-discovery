# 🧬 Omics-Driven Drug Repurposing for Lung Cancer

## Repository Overview
This repository presents a complete **omics-to-drug discovery pipeline** for lung cancer.  
The project starts from **multi-omics biomarker discovery** and systematically translates those biomarkers into **early-stage drug repurposing hypotheses** using public biomedical knowledge bases.

The focus is on **biological realism and interpretability**, reflecting how translational drug discovery is performed in industry rather than forcing artificial gene–drug overlap.

---

## Scientific Motivation
In real-world drug discovery:
- Genes most strongly associated with disease are often **not directly druggable**
- Drugs typically target **signaling nodes within disease-relevant pathways**
- Pathway-level reasoning is essential for translational success

This project explicitly models that reality.

---

## Pipeline Summary (End-to-End)

### Step 1: Multi-Omics Biomarker Input
The pipeline begins with a curated set of **lung cancer biomarkers** derived from integrated:
- Transcriptomic (RNA-level) analysis
- Proteomic (protein-level) analysis

Only genes showing consistent tumor–normal dysregulation across omics layers were retained, resulting in **92 candidate biomarkers**.

---

### Step 2: Disease Association Scoring (Open Targets)
Each of the 92 candidate genes was evaluated for disease relevance using the **Open Targets Platform** for:
- Lung carcinoma (EFO_0001071)

For each gene:
- Gene symbols were mapped to Ensembl IDs
- Genetic and biological evidence linking the gene to lung cancer was retrieved
- An **Open Targets disease association score** was assigned

This step identified several strong disease drivers, particularly genes involved in:
- Hypoxia signaling
- Endothelial differentiation
- Tumor microenvironment regulation

---

### Step 3: Druggability Mapping (ChEMBL)
In parallel, all 92 genes were evaluated for **pharmacological feasibility** using **ChEMBL**.

For each gene:
- Potential molecular targets were searched
- Curated **drug–target mechanisms of action** were retrieved
- Drugs were annotated with:
  - Mechanism of action
  - Direct vs indirect target interaction
  - Clinical development phase (max_phase)

This step yielded **44 target–drug mechanism mappings**.

---

### Step 4: Observed Biological Split
At this stage, the analysis revealed a biologically meaningful separation:

#### Disease-associated driver genes
- High Open Targets disease scores
- Often transcription factors, hypoxia regulators, or lineage markers
- Limited or no direct drug mechanisms

#### Druggable signaling targets
- Lower genetic association scores
- Established drug mechanisms
- Frequently surface receptors or signaling proteins

This split reflects a common translational challenge in oncology drug discovery.

---

### Step 5: Integration Strategy
Rather than requiring direct overlap between:
- High disease association genes **and**
- Direct drug targets

the pipeline integrates information at the **pathway and signaling level**.

Each candidate drug was prioritized using a **composite, interpretable score** combining:
- Clinical readiness (drug development phase)
- Mechanistic confidence (direct interaction)
- Disease relevance (Open Targets score, when available)

This avoids discarding valid biology and mirrors industry-standard prioritization logic.

---

## Results

### Target and Drug Coverage Summary

| Category | Count |
|--------|------|
| Biomarker-derived genes evaluated | 92 |
| Genes with Open Targets scores | 92 |
| Target–drug mechanism mappings | 44 |
| Genes with no curated drug targets | 58 |
| Targets without known drug mechanisms | 22 |

---

### Biological Themes Identified
The highest-confidence druggable targets clustered around:
- Angiogenesis and endothelial signaling
- Vascular tone and permeability
- Tumor microenvironment regulation

Representative druggable targets included:
- TEK (TIE2)
- ACVRL1 (ALK1)
- CALCRL / RAMP family
- S1PR1
- EDNRB

These targets align with lung cancer biology despite not always being the strongest genetic drivers.

---

## Interpretation
This project demonstrates that **successful drug discovery does not require disease drivers and drug targets to be the same gene**.

Instead:
- Disease drivers define *what biology matters*
- Druggable nodes define *where intervention is feasible*
- Pathway-level integration bridges the two

The resulting drug repurposing hypotheses are **biologically plausible, clinically informed, and defensible**.

---

## Key Takeaways
- Multi-omics integration strengthens confidence in disease biology
- Genetic association and druggability must be treated as complementary signals
- Pathway-level reasoning is essential for translational success
- Honest handling of non-overlap produces more realistic drug discovery outputs

---

## Technologies Used
- Python (pandas, numpy, requests)
- Open Targets GraphQL API
- ChEMBL REST API
- Jupyter / Google Colab

---

## Disclaimer
This project is intended for **research and hypothesis generation only**.  
Results are based on public datasets and knowledge bases and do not constitute clinical recommendations.
