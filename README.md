# lung-cancer-omics-drug-discovery
Multi-omics biomarker–driven drug repurposing for lung cancer using Open Targets and ChEMBL with pathway-level integration.
# 🧬 Omics-Driven Drug Repurposing for Lung Cancer

## Overview
This repository demonstrates how **multi-omics biomarker discovery** can be translated into **early-stage drug discovery** using public biomedical knowledge bases. The workflow integrates transcriptomic and proteomic biomarkers with **Open Targets** disease association data and **ChEMBL** drug–target mechanisms to generate biologically grounded **drug repurposing hypotheses** for lung cancer.

Rather than forcing direct gene-to-drug overlap, this project reflects **real-world translational drug discovery**, where disease-driving biology and druggable intervention points are often distinct but connected at the **pathway level**.

---

## 🔬 Visual Pipeline

```mermaid
flowchart LR
    A[Multi-Omics Data<br/>(RNA + Proteomics)]
    B[Integrated Biomarker Discovery]
    C[Candidate Gene Set<br/>(92 biomarkers)]
    D[Open Targets<br/>Disease Association]
    E[ChEMBL<br/>Drug–Target Mapping]
    F[Disease Driver Genes]
    G[Druggable Targets]
    H[Pathway-Level Integration]
    I[Drug Repurposing Prioritization]
    J[Ranked Candidate Drugs]

    A --> B
    B --> C
    C --> D
    C --> E
    D --> F
    E --> G
    F --> H
    G --> H
    H --> I
    I --> J
