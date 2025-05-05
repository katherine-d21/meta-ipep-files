# Tool Snippets for Meta-iPep

## FragPipe log.txt

### FragPipe Parameters:
Non-tryptic, no enzyme (nonspecific-HLA workflow)
Validation: MSBooster+Percolator
All 4 raw files
Input db: 40 organism db (779,931 sequences; includes human+cRAP)
No database splitting
2 var mods (N-term acet, MetOx)
Tolerances: Precursor 15 ppm, Fragment 20 ppm
Mix/max digest peptide length: adjust based on size of input database		

* **Database splitting** default `1` (zero splitting)
  > msfragger.misc.slice-db= `#`

* MSFragger Options > In-silico Digestion Parameters > **Minimum/maximum length/s of peptides to be generated during in-silico digestion**

  > msfragger.digest_max_length=`#`
  > msfragger.digest_min_length=`#`

* MSFragger Options > Variable Modifications: Protein N-terminal acetylation, Oxidation of methionine
  
  > msfragger.table.var-mods=`42.010563,[^,true,1; 15.994915,M,true,3`
 
**NOTE: Enter `Oxidation of M (15.994915...) modaa` in "Select" field. Type/paste `42.0105646837,[^,1` in "Enter" field.

* Validation > PSM Validation > `Run MSBooster and Percolator` (use defaults)

MSBooster:

  > msbooster.predict-rt=true
  > 
  > msbooster.predict-spectra=true
  > 
  > msbooster.run-msbooster=true
  > 
  > msbooster.use-correlated-features=false


Percolator:

> percolator.cmd-opts=--only-psms --no-terminate --post-processing-tdc
> 
> percolator.keep-tsv-files=false
>
> percolator.min-prob=0.5
>
> percolator.run-percolator=true

## PepQuery2 Parameters

Novel pept/prot validation
No enzyme, non-tryptic
Mods: no fixed, 1 var mod (MetOx)
Tolerances: Precursor 15 ppm, Fragment 0.6 Da
Min/max peptide length: adjust based on input peptide length

Example PepQuery2 log file - certain portions deleted for clarity

> PepQuery parameter:
> 
> main.java.pg.DatabaseInput[getEnzymeByIndex:263] - **Use enzyme:NoEnzyme**
> 
> **PepQuery version: 2.0.2**
> 
> PepQuery command line: -s 1 -ms index_dir -db Merged-Human+Isoforms-cRAP-database.fa -t peptide -i /data/dnb11/galaxy_db/files/8/2/8/dataset_828b1ba7-63c4-47b8-b4fe-bc3329e64faa.dat -indexType 2 -fixMod 0 -varMod 2 -e 0 -tol 15 -tolu ppm -fragmentMethod 1 -maxCharge 3 -minCharge 2 -minLength 16 -maxLength 16 -fast -o pepquery_output
> 
> **Fixed modification: 0 = -**
> 
> **Variable modification: 2 = Oxidation of M**
> 
> Max allowed variable modification: 3
> 
> Add AA substitution: false
> 
> **Enzyme: 0 = NoEnzyme**
> 
> Max Missed cleavages: 100
> 
> Precursor mass tolerance: 15.0
> 
> Range of allowed isotope peak errors: 0
> 
> Precursor ion mass tolerance unit: ppm
> 
> Fragment ion mass tolerance: 0.6
> 
> Fragment ion mass tolerance unit: Da
> 
> Scoring algorithm: 1 = Hyperscore
> 
> Min score: 12.0
> 
> Min peaks: 10
> 
> **Min peptide length: 16**
> 
> **Max peptide length: 16**
> 
> Min peptide mass: 500.0
> 
> Max peptide mass: 10000.0
> 
> Random peptide number: 10000
> 
> Fast mode: true
> 
> CPU: 125


# BLASTP Peptide Annotation Summary

## Tabular headers

**Comma-separated:**

> peptide,qlen,taxon_rank,taxon_id,taxon_name,ec_numbers,ec_names,go_terms,go_names,ipr_codes,ipr_names,accession,pident,evalue,salltitles,Protein,ProteinID,Entry_Name,Protein_Desc

**NO commas:**

> peptide	qlen	taxon_rank	taxon_id	taxon_name	ec_numbers	ec_names	go_terms	go_names	ipr_codes	ipr_names	accession	pident	evalue	salltitles	Protein	ProteinID	Entry_Name	Protein_Desc

# NetMHCpan EL and BA output

16 columns:

seq #	peptide	start	end	peptide length	allele	peptide index	median binding percentile	netmhcpan_el core	netmhcpan_el icore	netmhcpan_el score	netmhcpan_el percentile	netmhcpan_ba core	netmhcpan_ba icore	netmhcpan_ba IC50	netmhcpan_ba percentile

seq#,peptide,start,end,peptide_length,allele,peptide_index,median_binding_percentile,MHCI_EL_core,MHCI_EL_icore,MHCI_EL_score,MHCI_EL_percentile,MHCI_BA_core,MHCI_BA_icore,MHCI_BA_IC50,MHCI_BA_percentile

,peptide,,length,,,,,EL_percentile,,BA_IC50,BA_percentile

# NetMHCiipan EL and BA output

14 columns:

seq #	peptide	start	end	peptide length	allele	peptide index	median binding percentile	netmhciipan_el core	netmhciipan_el score	netmhciipan_el percentile	netmhciipan_ba core	netmhciipan_ba IC50	netmhciipan_ba percentile

seq#,peptide,start,end,peptide_length,allele,peptide_index,median_binding_percentile,MHCII_EL_core,MHCII_EL_score,MHCII_EL_percentile,MHCII_BA_core,MHCII_BA_IC50,MHCII_BA_percentile

,peptide,,length,,,,,EL_percentile,BA_IC50,BA_percentile
