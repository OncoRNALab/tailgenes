This repository contains data and scripts used to generate numbers and figures for the paper by Morlion et al.: *"Patient-specific alterations in blood plasma cfRNA profiles enable accurate classification of cancer patients and controls"* currently on [medRxiv](https://doi.org/10.1101/2023.05.24.23290388)

The `input` folder contains annotation and count data, used as input for data analysis:
- *SupplTable1_sample_annotation.txt*: pan-cancer, three-cancer and lymphoma cohort sample annotation (plasma samples)
- *bladdercancer_sample_annotation.txt*: bladder cancer cohort sample annotation (urine samples)
- *\*_counts.txt*: raw counts (STAR+HTseq) for the respective sample cohort

The `data` folder contains files that are made using the scripts in the `data_analysis` folder:
- Differential abundance & GSEA files (generated by `differentialabundance.R` script):
  - folder *pancancer_GSEA* & *threecancer_GSEA* contain the fold change ranked gene lists per cancer vs control comparison in the respective cohorts - used as input for gene set enrichment analyses
  - *differentialabundance_\*.txt*: tables with differentially abundant genes (|log2(fold change)|>1 and adjusted p>0.05) per cancer-control comparison (cancertype) in the respective cohort \*
  - *\*_normcounts(_all).txt*: DESeq2 library size normalized counts for the respective sample cohort
- Tail gene analyses (generated by `tailgenes_*.R` scripts):
  - *\*_biomarkertail_list.txt*: list of biomarker tail genes per set for cohort \*
  - *\*_tailgenes.txt*: list of tail genes per sample of cohort \* with respective z-score (based on all controls except sample itself) and normalized counts
  - overview_tailgenes.txt: table containing all tail genes with the number of samples for which they are tail gene, direction, and identify as biomarker tail gene

The `figures` folder contains plots that are made using the scripts in the `data_analysis` folder:
- *\*diffabundance_\*.pdf*: figures generated by `differentialabundance.R` script
- *\*_PCA.pdf*: PCA figures generated by `differentialabundance.R` script
- *threecancer_(biomarker)tail_\*.pdf* / *threecancer_(biomarker)tail_\*.png*: figures generated by `tailgenes_threecancer.R` script of respective cohort
- *lymphoma_(biomarker)tail_\*.pdf* / *lymphoma_(biomarker)tail_\*.png*: figures generated by `tailgenes_lymphoma.R` script of respective cohort
- *bladdercancer_(biomarker)tail_\*.pdf* / *bladdercancer_(biomarker)tail_\*.png*: figures generated by `tailgenes_bladdercancer.R` script of respective cohort
