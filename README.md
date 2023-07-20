# Chiron: A Charlson Comorbidity Index Calculator

## Overview

This Charlson Comorbidity Index Calculator, named 'Chiron', is a response to the Janssen OHDA programming assignment. It's a user-friendly tool designed for anyone interested in exploring the comorbidity index of different drugs.

In Greek mythology, Chiron was the wisest and justest of all the centaurs, known for his knowledge and skill with medicine. The name reflects the purpose of this application and its aim to provide insights into comorbidities related to different drugs.

The calculator uses data from the Eunomia synthetic dataset, which adheres to the Observational Medical Outcomes Partnership (OMOP) Common Data Model. This app identifies drug exposures using RxNorm CUIs obtained from Athena (OHDSI, 2023) and conditions contributing to the CCI using SNOMED CT codes from a validated list (Fortin, Reps, & Ryan, 2022).

Individuals with drug exposures are indexed on their first date of drug exposure, and their age is calculated at this period. To use this calculator, enter the name of the drug in the text box and click 'Calculate CCI'. The app will then calculate the Charlson Comorbidity Index (CCI) for each person exposed to the drug. The CCI is calculated as the sum of weights associated with each condition a person has, plus a weight based on age, according to the methodology defined by Quan et al., 2005.

Included in this repository is an R Markdown file, ohda_assignment.Rmd, that compares results from Warfarin and Acetaminophen and contrives the initial calculate_charlson_index function that takes a list of drug_concept_ids and returns the CCI using SNOMED nomenclature to identify conditions and the weights used by (Quan et al., 2005).

Please note that the search requires the drug name to be at least 4 characters long. If the entered drug name does not match any entries in the Eunomia CDM tables, an error message will be displayed.

This application is intended for demonstrative purposes only.

Containerization via Rocker is in progress.

Currently, an Rstudio connect hosted version of Chiron can be found at:
https://rwill235.shinyapps.io/shinyapp_charlsoncomorbidityindex_calculation/

## Requirements

This project was developed and tested with the following environment:

- Operating System: macOS Big Sur 10.16
- R version 4.3.1 (2023-06-16)

### R Packages
This project depends on the following R packages:

- rsconnect: 0.8.29
- DT: 0.28
- flexdashboard: 0.6.1
- shiny: 1.7.4.1
- RColorBrewer: 1.1-3
- broom: 1.0.5
- coviData: 0.0.0.9001
- Eunomia: 1.0.2
- DatabaseConnector: 6.2.3
- janitor: 2.2.0
- kableExtra: 1.3.4.9000
- lubridate: 1.9.2
- forcats: 1.0.0
- stringr: 1.5.0
- dplyr: 1.1.2
- purrr: 1.0.1
- readr: 2.1.4
- tidyr: 1.3.0
- tibble: 3.2.1
- ggplot2: 3.4.2
- tidyverse: 2.0.0

### Matrix Products
- Default
- BLAS:   /System/Library/Frameworks/Accelerate.framework/Versions/A/Frameworks/vecLib.framework/Versions/A/libBLAS.dylib 
- LAPACK: /Library/Frameworks/R.framework/Versions/4.3-x86_64/Resources/lib/libRlapack.dylib; LAPACK version 3.11.0

Please ensure that you have the appropriate versions of each requirement to avoid any potential issues.

## Installation

This repository contains files for aesthetics such as preamble.tex and color_palletes. R. To knit the R markdown document,  LaTeX or Tidytex is required. For the Shiny app, data is contains in RDS files.

## Usage
Users can enter a drug name as a string into the text box featured on a Shiny app. If a response is less than 4 characters or is not found in the Eunomia data sample, an error will be returned. 