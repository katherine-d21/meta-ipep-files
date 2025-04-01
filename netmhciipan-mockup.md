# Integrating context and inverted peptide binders within Galaxy

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
 
## NetMHCIIpan website interface and functionality

This is what the [NetMHCIIpan website looks like](https://services.healthtech.dtu.dk/services/NetMHCIIpan-4.3/).

Here is the website interface broken down into the components that we are most interested in:

![simple-web-interface](images/netmhciipan-web-mockup.png)

As seen in the graphic above, here are the main features/parameters:
* Input peptides as `FASTA` or `tabular`
* Molecule selection by a dropdown menu or manual typing
     - Default: `DRB1_0101`
* Specify peptide length(s)
     - Default: `15`
* Threshold cute-offs for %Rank values
     - Default values for strong, weak binders: `1` `5`
* Encode peptide context
     - Consists of 12 context residues/amino acids: 3 upstream of the N-terminus, 3 from the N-terminus, 3 from the C-terminus, and 3 downstream from the ligand
     - Default: `No`
* Predict binding for inverted peptides to all molecules
     - Default: `Peptide inversion only predicted for HLA-DP molecules`
* Include binding affinity (BA) predictions
     - Default: `only eluted ligand (EL) likelihood`

## Current state of the Galaxy tool implementation

Here is the current MSI tool interface:

![msi-tool-interface](images/MSI-screenshot.png)


