# Repurposing Datasets 
## Table of Contents
- [Drug-Target Interaction Datasets](#DTI datasets)
    - [BindingDB](#bindingdb)
    - [ChEMBL](#chembl)
    - [DrugTargetCommons (DTC)](#dtc)
    - [DrugCentral](#drugcentral)
    - [PubChem](#pubchem)
    - [DGIdb](#dgi)
    - [GtopDB](#gtop)
    - [Probes & Drugs Portal](#p&d)
- [Drug-Target Interaction GUIs](#DTI GUIs)
    - [SwissTargetPrediction](#swiss)
    - [ChemicalChecker](#chemicalchecker)

## Drug-Target Interaction Datasets <a name="DTI datasets"></a>
### BindingDB <a name="bidingdb"></a>
Comprehensive resource of quantitative bio-activity data in terms of IC50, EC50, Kd and Ki assays. This dataset has 193 columns, which most of those are addressing the protein in other datasets (e.g. PubChem, ChEMBL, UniProt, etc.)
Some of the most important attributes are:
- Ligand SMILES
- Number of protein chains in target
- Kd, Ki, IC50 or EC50 (bio-activity)
- BindingDB Target Chain  Sequence
- Ligand InChI
- PubChem CID
- UniProt (SwissProt) Primary ID of Target Chain
#### data type
- contains quantitative bioactivity data for drug–target binding affinity
#### statistics
- Compounds: >0.7M
- Targets: >7.2K
- Interaction: >1.2M
#### additional notes
- Download the data [here](https://www.bindingdb.org/bind/chemsearch/marvin/SDFdownload.jsp?all_download=yes). The name of this file is BindingDB_All_20xxmx.tsv.zip (e.g. BindingDB_All_2022m9.tsv.zip)
- There is a function in DeepPurpose that preprocess the downloaded data.
--- 
### ChEMBL <a name="chembl"></a>
Most compressive manually-curated bio-activity data from HTS of compound activities. Retrieving the data need the knowledge of SQL and writing queries. The most important entities of dataset are as following:
- activity
- assay
- binding_site
- chembl_id_lookup
- drug
- drug_indication
- molecule
- protein_class
- similarity
- source
- target
#### data type
- contains quantitative bioactivity data for drug–target binding affinity
- contains both active and inactive drug–target pairs
#### statistics
- Compounds: >1.9M
- Targets: >12K
- Interaction: >15.5M
#### additional notes
- This [github page](https://github.com/chembl/notebooks/blob/main/ChEMBL_webresource_client_examples.ipynb) provides an easier form of retrieving the data from ChEMBL.
---
### DrugTargetCommons (DTC) <a name="dtc"></a>
Manually curated bioactivity data along with protein classification into superfamilies, clinical phase and adverse effects as well as disease indications. The dataset contains Compound ID and Standard Inchikey which helps connecting it to other datasets. Here is the list of some important features from this dataset:
- compound_id
- standard_inchi_key
- compound_name
- target_id
- pubmed_id
- standard_value
- ep_action_mode
#### data type
- contains quantitative bioactivity data for drug–target binding affinity
- contains both active and inactive drug–target pairs
#### statistics
- Compounds: >1.6M
- Targets: >13K
- Interaction: >14.8M
#### aditional notes
- For download, go this [link](http://drugtargetcommons.fimm.fi/).
- The compund ID contains "CHEMBL" string for all compounds, so I guess this can easily connect to [ChEMBL dataset](https://git.rxcorp.com/u1130932/repurposing_datasets/-/blob/main/README.md#chembl). 
---
### DrugCentral <a name="drugcentral"></a>
Provides information on active chemical entities and drug mode of action. There are 20 attributes in this dataset, and some of the most important ones are as following:
- drug_name
- target_name
- target_class
- act_value
- act_type
- action_type
#### data type
- contains only active drugs for the targets
- contains quantitative bioactivity data for drug–target binding affinity
#### statistics
- Compounds: >4.5K
- Targets: >11K
- Interaction: >15K
#### aditional notes
- The tabular drug-target interaction data can be downloaded [here](https://drugcentral.org/download).
- The website contains data related to approved drugs, their chemical structure, SMILES and InChI files, etc. 
---
### PubChem <a name="pubchem"></a>
Provides information on chemical structures, identifiers, chemical and physical properties, biological activities, patents, health, safety, and toxicity data. This dataset is the largest public dataset which is provided by NIH. But the download process requires the user to search a word first (e.g. Covid19) and then it allows the user to download the data. Even after narrowing down the search with a keyword, the download process is not straightfoward. I think it requires writing quesries and data wrangling. 
#### data type
- contains only active drugs for the targets
- contains quantitative bioactivity data for drug–target binding affinity
#### statistics
- Compounds: >95M
- Targets: >58K
- Interaction: >264.8M
---
### DGIdb <a name="dgi"></a>
Drug–target interactions mined from > 30 trusted sources, including DrugBank, PharmGKB, Chembl, Drug Target Commons, Therapeutic Target Database ([paper](https://academic.oup.com/nar/article/49/D1/D1144/6006193)). This is a datasets which contains only the names of drugs and the genes that interact with each other. The most important columns are:
- gene_name
- drug_name
- interaction_types
- interaction_group_score
#### data type
- contains only active drugs for the targets
#### statistics
- Compounds: >10K
- Targets: >50K
- Interaction: >20K
#### aditional notes
- Download the data [here](https://www.dgidb.org/downloads).
---
### GtopDB <a name="gtop"></a>
Contains quantitative bioactivity data for approved drugs and investigational compounds.
#### data type
- contains quantitative bioactivity data for drug–target binding affinity
#### statistics
- Compounds: >10K
- Targets: >3K
- Interaction: >32K
#### aditional notes
- Download the data [here](https://www.guidetopharmacology.org/download.jsp). 
- The targets in this dataset are not provided in sequence format. So, there should be a way to map those targets to a desired representation. Aparently, [SynPharm](https://pubs.acs.org/doi/pdf/10.1021/acsomega.8b00659) is one way to do that. They provide nice tables on their [website](https://synpharm.guidetopharmacology.org/) which can be used to map targets (and even ligands) to any representation. Another way to do this is through the RefSeq IDs provided by NCBI. The current preprocessing code uses the latter method which is based on the downloaded _RefSeq Proteins_ data from [this link](https://www.ncbi.nlm.nih.gov/projects/genome/guide/human/index.shtml).
#### Probes & Drugs Portal <a name="p&d"></a>
A public resource joining together focused libraries of bioactive compounds (e.g. probes, drugs, specific inhibitor sets).
#### data type
- contains quantitative bioactivity data for drug–target binding affinity
#### statistics
- Compounds: >67K
- Targets: >8.7K
- Interaction: >0.96M
#### aditional notes
- The data can be downloaded [here](https://www.probes-drugs.org/compounds/standardized).
- This is a relatively large dataset with lots of useful information, especially to build a knowledge graph. 166906 entries of compound-target relationship with sources and pathways from different resources such as Reactome. The data is already preprocessed and there is no need to a heavy trim. 
---
---
---
## Drug-Target Interaction GUIs <a name="DTI GUIs"></a>
### SwissTargetPrediction <a name="swiss"></a>
Contains information on predicted targets of drugs based on similarity principle through reverse screening. This is an application and it is freely available [here](http://www.swisstargetprediction.ch/). But there is no dataset associated to it. Apparently, they are using ChEMBL data to make predictions regarding a new small molecule.
### ChemicalChecker <a name="chemicalchecker"></a>
Provides processed, harmonized and integrated bioactivity data. [The Chemical Checker](https://chemicalchecker.org/) is a resource of chemical and biological small molecule similarities. Molecules are compared from multiple viewpoints relevant to the drug discovery pipeline, from the chemical properties to the clinical outcomes. The backbone of most 



