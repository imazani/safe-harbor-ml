# safe-harbor-ml

Predict epigenetically stable genomic loci ("safe harbors") for transgene integration using public epigenomic data.

## Project Motivation and Rationale

Genome engineering workflows often rely on a small number of empirically identified “safe harbor” loci genomic regions that support stable transgene expression without disrupting endogenous gene regulation. While these loci (e.g., AAVS1, CCR5) are widely used, they were discovered experimentally rather than through a systematic, genome-wide approach.

A defining characteristic of safe harbor loci is their regulatory stability: they tend to reside in chromatin environments that are insulated from strong regulatory activity and remain relatively stable across cell types. Public epigenomic resources such as ENCODE provide genome-wide measurements of chromatin accessibility, histone modifications, and regulatory states that reflect this functional context.

This project tests the hypothesis that known safe harbor loci occupy a distinct epigenetic feature space that can be learned by an interpretable machine learning model. By engineering epigenomic and genomic-context features from public datasets and training supervised models to distinguish known safe harbors from matched genomic control regions, this work aims to:

1. Assess whether epigenetic features are predictive of safe harbor–like behavior.
2. Identify which regulatory signals most strongly characterize these loci.
3. Generate a ranked set of candidate genomic regions that resemble known safe harbors, suitable for downstream experimental prioritization.

This work does not claim to identify clinically validated integration sites, but instead provides a computational framework for hypothesis generation and experimental design in genome engineering.

### Labeling note: "safe harbor" exits on a specturm
In practice, genomic “safe harbor” behavior exists on a spectrum rather than a strict binary: integration outcomes can vary by cell type, lineage, chromatin remodeling, and assay context. To reduce label noise in this initial study, the positive class is restricted to a small set of canonical, high-confidence loci commonly used in genome engineering. The pipeline is designed to support future extensions such as tiered positives (high- vs moderate-confidence) and cell-type–specific scoring. 

## Environment
- Python 3.11
- Conda env: `safeharbor`

Create env:
```bash
conda env create -f environment.yml
conda activate safeharbor
pip install -e .

