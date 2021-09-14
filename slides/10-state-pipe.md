---
author: Colin A. Gross
title: BRAVO 2021
date: 2021-09-13
---

# Current State: Data Prep
Consolidated and coherent

## ✓ Consolidate data processing scripts

```
workflows/
├── coverage
│   ├── Coverage.nf
│   └── nextflow.config
├── prepare_vcf
│   ├── PrepareVCF.nf
│   └── nextflow.config
└── sequences
    ├── Sequences.nf
    └── nextflow.config
```

## ✓ Document data processing config
```groovy
  // Use wildcard like chr11.*.bcf for list of bcf files.
  chromosome      = "chr11"

  // Required input data
  vcfs            = "data/chr11.subset.bcf"
  // Use *.tsv.gz for list of cadd files.
  cadd_tsvs       = "data/chr11.sites.cadd.tsv.gz"

  // Optional input data
  // Use NO_FILE to indicate the optional samples list is not being used.
  samples         = "NO_FILE"

  // Executeable paths.
  // Use name of exec if in PATH or is symlinked in bin/ of this pipeline
  vep             = "vep"
  counts_exec     = "ComputeAlleleCountsAndHistograms"

  // Scripts use full path or path to symlink in local bin/
  add_cadd_script = "bin/add_cadd_scores.py"
```
## ✓ Document software dependencies

```
## BamUtil
Clone and install from [bamUtil repo](https://github.com/statgen/bamUtil)

## VEP
Installation [instructions](https://useast.ensembl.org/info/docs/tools/vep/script/vep_download.html) on ensembl.org.

## Loftee
Master branch of [LoF plugin](https://github.com/konradjk/loftee) doesn't work for GRCh38
per this [issue](https://github.com/konradjk/loftee/issues/73#issuecomment-733109901)
    ```
    git clone --depth 1 --branch grch38 --single-branch git@github.com:konradjk/loftee.git
    ```
```

## ✓ Document data dependencies

```
#### Genenames: HUGO Gene Nomenclature Commitee (HGNC)
Can be obtained from [genenames custom downloads](https://www.genenames.org/download/custom/)
 
The genenames set from all the chromosomes with the above columns can be obtained using curl.
    ```
    curl 'https://www.genenames.org/cgi-bin/...
    ```
```

and idiosyncracies 
```
Headers need to be rewritten to match expected column names and the results gzipped
    ```
echo -e "symbol\tname\talias_symbol\tprev_symbol\tensembl_gene_id" > hgcn_genenames.txt
tail -n +2 hgcn_custom_result.txt >> hgcn_genenames.txt
gzip hgcn_genenames.txt
    ```
```

## ✓ Update dependencies 
- hstlib, samtools, bamtools, tabix, vcftools
- python packages & scripts
- Nextflow 1.x -> 2.0

