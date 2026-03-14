# Homozygosity Mapping

A lightweight browser-based tool for identifying protein-coding genes within genomic regions of interest. Designed as a starting point for homozygosity mapping workflows.

## What it does

- Enter one or more GRCh38 genomic regions (e.g. `chr3:45000000-52000000`)
- Fetches protein-coding genes from the [Ensembl REST API](https://rest.ensembl.org)
- Displays results in a sortable table with gene name, Ensembl ID, coordinates, strand, and description
- Ensembl IDs link directly to the Ensembl gene summary page
- Multiple regions get individual tabs plus a merged, deduplicated **ALL** tab
- Export results as TSV for downstream analysis

## Usage

1. Open the app at `https://yourusername.github.io/homozygosity-mapping`
1. Enter one GRCh38 region per line in the text box:
   
   ```
   chr3:45000000-52000000
   chr7:117000000-117400000
   ```
1. Press **QUERY** (or Ctrl+Enter / Cmd+Enter)

## Input format

|Format          |Example                 |
|----------------|------------------------|
|`chrN:start-end`|`chr3:45000000-52000000`|
|`N:start-end`   |`3:45000000-52000000`   |

## Deployment

This is a single static `index.html` file — no server or dependencies required. Hosted via [GitHub Pages](https://pages.github.com/).

## Data source

Genes are retrieved in real time from the [Ensembl REST API](https://rest.ensembl.org/documentation/info/overlap_region):

```
GET /overlap/region/human/{region}?feature=gene
```

Only `protein_coding` biotype genes are shown. Genome assembly: **GRCh38**.

## Planned features

- OMIM disease gene filter (stub present in UI)
- Additional biotype filters (lncRNA, pseudogene, etc.)
- Batch export across all regions

## License

MIT
