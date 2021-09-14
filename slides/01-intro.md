---
author: Colin A. Gross
title: BRAVO 4 VCF
date: 2021-09-13
---

# BRAVO for your VCFs

"Spin up and instance with your VCFs!"

## Spinup Steps
1. Prepare Data: ([Bravo Data Prep](https://github.com/statgen/bravo_data_prep)) ✓
1. Deploy Data: ([Bravo API](https://github.com/statgen/bravo_api)) ✓
1. Deploy API: ([Bravo API](https://github.com/statgen/bravo_api)) ✓
1. Deply UI: ([Bravo Vue UI](https://github.com/grosscol/vue_mpa_prototype)) ◎

## Inputs
- VCFs
- Crams

## Software Dependencies
- Nextflow, python, tabix, samtools, htslib, VEP, BamUtil, Loftee
- Flask, pymongo, mongodb
- Npm, vue-cli

## Data Dependencies

HUGO names, Ensembl Id mapping, OMIM mapping, Gencode gene list, loftee ancestor.fa, loftee conservation files, reference sequence
