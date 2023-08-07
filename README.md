# Rocket-miR

### Introduction:

Rocket-miR is an accessible, point-and-click R Shiny web application designed to stimulate the development of new miRNA-based antimicrobial drug candidates. The application was inspired by prior research demonstrating that eukaryotic miRNAs are capable of regulating virulence genes and pathways in microbial pathogens ([Koeppen et al., 2021](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8285967/); [Cai et al., 2018](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6442475/); [Liu et al., 2016](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4847146/)).

Rocket-miR relies on the bioinformatics algorithm [IntaRNA](https://github.com/BackofenLab/IntaRNA), which predicts the strength of molecular interactions between RNA molecules. The algorithm was applied to predict the potential for interaction between 630 human miRNAs (the set of mature human miRNAs in the [miRGeneDB](https://mirgenedb.org/) Database) and all proteins in 24 human pathogens - including the [ESKAPE pathogens](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6452778/) and a range of pathogens that commonly afflict individuals with the common genetic illness cystic fibrosis (CF). The full set of pathogens included in the application are listed in Supported_Species.csv, within the 'Application Data' folder of this repository.

In the application, users can predict which miRNAs are best suited in general to target individual species, what miRNAs are most likely to target specific biological pathways, how certain miRNAs are predicted to perform across a group of species, and more. To learn more and try the application for yourself, you can access it via the application link below. 

### Requirements:

You can access the published version of Rocket-miR online at the following link: http://scangeo.dartmouth.edu/RocketmiR/

To run the R Shiny application on your own computer in Rstudio, download the contents of the repository as a zip file using the green ‘Code’ button at the top right of this web page. 

In order to get the app working, you will first need to set up the application data files (containing miRNA target predictions and gene-pathway annotations for each pathogen). You can do so by working through the ‘Data_Setup.Rmd’ script step-by-step. Once the data is generated, you can run the app.R file in RStudio and the app will launch on your computer. 

### Referencing Rocket-miR:

If you use Rocket-miR to advance your own research, please cite the following publication: 

*Placeholder: Reference will be available as soon as the associated manuscript is submitted…*

For now, you can cite our pre-print, hosted in biorxiv under the title: [Rocket-miR, a Translational Launchpad for miRNA-based Antimicrobial Drug Development]([url](https://www.biorxiv.org/content/10.1101/2023.06.22.546111v1#:~:text=The%20Rocket%2DmiR%20application%20predicts,to%20test%20the%20application's%20predictions.))

If you have any questions about the application or its source code - or would like to apply the Rocket-miR framework to new species and/or new small RNA molecules - please reach out to neff [dot] sam1 [at] gmail [dot] com

### Directory Contents

Application Code:

- Initial_Data_Processing.Rmd: Creates Inta-RNA target prediction energy tables for each microbial species in the application.
- Data_Setup.Rmd: Combines energy tables with associated gene/pathway annotations and prepares the .Rdata files that run in the application.
- app.R: Main application code file. This is what runs when the application is executed in RStudio or on the web server, drawing on the .RData files produced by Data_Setup.Rmd.

Application Data:

- Annotation_Data Folder: Annotation files that enable annotation mapping of genes (e.g., Entrez ID —> Uniprot ID) for the microbial species included in the application. 
- Energy_Tables Folder: Includes all the energy tables (one for each microbial species) generated by Initial_Data_Processing.Rmd.
- Raw_Data Folder: Includes the query miRNA sequences and cDNA sequence targets for each species. These files were used as input for the IntaRNA algorithm. The output of the IntaRNA algorithm was fed into Initial_Data_Processing.Rmd to generate the energy tables. The outputs were not included in the directory due to their large file size, but the IntaRNA command line prompts are included for each species so that the process of generating the output data can be replicated and/or repurposed for new species.
- Supported_Species.csv: Associated metadata for all microbial species included in the application.
- human_mature_miRNA.txt: All miRNA sequences used in the application.

To run the application on your own computer, you can use the energy tables and other files included in the Application Data folder. In RStudio, execute the Data_Setup.Rmd script in full to generate the .Rdata files. Once the. Rdata files are generated, you can execute app.R and run the application in RStudio or in your web browser. 

Rocket-miR Expansion:

The Rocket-miR expansion folder contains IntaRNA predictions for additional microbial strains. Anyone is welcome to contribute additional predictions to the repository. If you would like to contribute...

- Read the IntaRNA Prediction guide which outlines all the essential steps of making new predictions [IntaRNA Prediction Guide](https://docs.google.com/document/d/1sxUSO6hEWznG-G6ytl4HQuzbiNAj5yxOqsZHtavOr24/edit?usp=sharing)
- Reach out to neff [dot] sam1 [at] gmail [dot] com about making the results of these predictions publicly available in this repository and/or if you have any questions. 

Each new strain will have its own folder within Rocket-miR expansion containing the target prediction energy table, an HTML file with target prediction analysis outputs, and a short informational text file with the strain name and a link to the NCBI assembly page containing the strain's cDNA sequences. The IntaRNA Prediction Guide explains how to generate both the energy table and the HTML file given the cDNA sequence data. 
  
