# Tomato-P-Recovery


## Overview

This repository contains the R code and data associated with the following manuscript:

Dixon M M, Afkairin A, Davis J G, Chitwood-Brown J, Buchanan C M, Ippolito J A, Manter D K, Vivanco J M. Tomato domestication rather than subsequent breeding events reduces microbial associations related to phosphorus recovery  

To address methods to enhance sustainable use of phosphate rock, we elucidate the different phosphorus (P) recovery methods among wild, traditional, and modern tomatoes. We use information from biomass, shoot P uptake, and rhizosphere microbiome composition of tomatoes. Code are available to reproduce the results and figures in the manuscript. Data are publicly available. 


## File descriptions

1. "Biomass_PSF.Rmd" includes code to analyze differences in relative root and shoot biomass accumulation. It also includes the analysis for the P stress factor. 
	- Data inputs:  
		- "Dry_Biomass.csv": Raw dry shoot and root biomass values.       
	- Data outputs:  
		- "Figure1.pdf": Phosphorus deficiency effects on plant growth. 
		- Results corresponding to figure 1

2. "Plant_P.Rmd" includes code to determine differences in shoot P uptake and in difference between the shoot P uptake of fertilized and unfertilized tomato.  
	- Data inputs:  
		- "Plant_P.csv": Phosphorus concentration (from ICP-AES) and P uptake values.  
	- Outputs: 
		- "Figure2.pdf" Plant phosphorus (P) uptake (shoot mg P) in tomato across a domestication gradient
		- Results corresponding to figure 2

3. "Olsen_P.R" includes code to determine differences in bulk soil Olsen P concentrations. 
	- Data inputs:  
		- "Olsen_P.csv": Bulk soil Olsen P concentration values.  
	- Outputs:  
		- "Figure3.pdf" Bulk soil Olsen phosphorus concentration (mg/kg) in tomato across a domestication gradient. 
		- Results corresponding to figure 3
		
4. "Microbiome_Read_In_Data.R" includes code to convert ".log" demultiplex files to excel worksheets. It also includes codes to convert EMU files for indivial sequencing runs and compiles them into one phyloseq object. 
  - Function inputs:
    - "Microbiome_Functions.R": Includes custom functions that allow for conversion from EMU to phyloseq ojects.
	- Data inputs:  
		- "demultiplex_plateA.log": Includes sequence reads for plate A.  
		- "demultiplex_plateB.log": Includes sequence reads for plate B.  
		- "demultiplex_plateC.log": Includes sequence reads for plate C.  
		- "EMU_Relative_Abundance_plateA.csv": Taxonomic relative abundance information for plate A.
		- "EMU_Relative_Abundance_plateB.csv": Taxonomic relative abundance information for plate B.
		- "EMU_Relative_Abundance_plateC.csv": Taxonomic relative abundance information for plate C.
	- Outputs:  
		- "demultiplex_plateA.xlsx" Sequence reads for plate A. 
		- "demultiplex_plateB.xlsx" Sequence reads for plate B. 
		- "demultiplex_plateC.xlsx" Sequence reads for plate C.
		- "Phyloseq.Plate.A.RDS" Phyloseq object that includes sequence reads and relative abundance information for plate A.
				- "Phyloseq.Plate.B.RDS" Phyloseq object that includes sequence reads and relative abundance information for plate B.
		- "Phyloseq.Plate.C.RDS" Phyloseq object that includes sequence reads and relative abundance information for plate C.
		- "Phyloseq.RelativeAbundance.RDS" merged phyloseq object that combines "Phyloseq.Plate.A.RDS", "Phyloseq.Plate.B.RDS", "Phyloseq.Plate.C.RDS"
		- "Phyloseq.Count.Data.RDS" A phyloseq object that includes count data for microbial abundance, combined for all plates.

4. "dbRDA.R" includes code to assess rhizosphere community structure for samples. 
	- Data inputs:  
		- "Phyloseq.RelativeAbundance.RDS": merged phyloseq object showing relative abundance files (culled from code in "Microbiome_Read_In_Data")
	- Outputs:  
		- "SuppFigure1.pdf.pdf" Distance-based redundancy analysis (db-RDA) showing clustering based on Bray-Curtis dissimilarity of the bacterial community structure in the tomato rhizosphere. 
		- Results corresponding to Supplemental figure 1
		- "Figure4.pdf" Distance-based redundancy analysis (db-RDA) showing clustering based on Bray-Curtis dissimilarity of the bacterial community structure in the rhizosphere of different tomato domestication groups
		- Results corresponding to figure 4
		
5. "Differential_Abundance.R" includes code to determine different bacterial species that change in abundance between treatments.
	- Data inputs:  
		- "Phyloseq.Count.Data.RDS": phyloseq object showing bacterial abundance count data (culled from code in "Microbiome_Read_In_Data")
	- Outputs:  
		- "Figure5.pdf.pdf" Differential abundance (DA) analysis showing the log fold change in bacteria abundance between different domestication and varietal groups. 
		- Results corresponding to Figure 5

6. "P_Cycling_Bacterial_Abundance.Rmd" includes code to analyze the relative abundance of P-decomposing and P-cycling bacteria.
  - Data inputs:
		- "Phyloseq.RelativeAbundance.RDS": merged phyloseq object showing relative abundance files (culled from code in "Microbiome_Read_In_Data")
		- "EMU_database.GIBBs.KO.PICRUST2.xlsx": Shows information from PICRUST database that shows functional abundance of mapped bacteria.
	- Outputs:  
	  - "Figure6" Phosphorus (P) cycling bacteria relative abundance in unfertilized soil. 
	  - Results corresponding to figure 6.
	  - "SuppFigure2" Phosphorus (P) cycling bacteria relative abundance in fertilized soil. 
	  - Results corresponding to supplemental figure 2.