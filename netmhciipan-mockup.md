# Brainstorming: Integrating context and inverted peptide binders within Galaxy

## Objectives of this document:
* Documenting ideas for integrating peptide context encoding and prediction of inverted peptide binders within Galaxy
* Practice for using Markdown language and GitHub

## Tools/Services:
* IEDB-API: http://tools.iedb.org/main/tools-api/
* Galaxy tools:
   - NetMHCIIpan tool: in development on MSI instance
   - UniProt: API service
   - Query Tabular
 
## Required User Inputs:
* MHC molecules/HLA alleles
  - Two options: 1) select from dropdown menu, 2) use tabular file from history.)
* Peptides of interest
  - Three options: FASTA (from history), tabular (from history), manually entered
  - Here, we are looking at microbial peptides
 
## Where are we starting from?

This is what the [NetMHCIIpan website looks like](https://services.healthtech.dtu.dk/services/NetMHCIIpan-4.3/).

Here is the website interface broken down into the components that we are most interested in: [simple-web-interface]([mockup images/netmhciipan-web-mockup.png](/../main/mockup%20images/netmhciipan-web-mockup.png))
