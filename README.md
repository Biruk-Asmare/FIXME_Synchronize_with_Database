# FIXME: Synchronize with Database - An Empirical Study of Data Access Self-Admitted Technical Debt

## Replication package
This repository contains the dataset and analysis scripts used to answer the research questions in the paper. The repository contains `Projects`, `Data_Collection`, `RQ1`, `RQ2`, `RQ3`, `RQ4`, and `Threats_to_validity` folders. The details of each folder are described below.

### Projects

This folder contains the list of selected projects for SQL and NoSQL systems. Each file contains the name of the project and the corresponding GitHub URL.

### Data_Collection

The `Data_Collection` folder contains the raw dataset, the list of import statements, and the details of snapshots taken for both SQL and NoSQL systems.

#### JNoSQL_Supported_databases.csv

This file contains the list of _JNoSQL_ supported databases. It contains the name of the database and the corresponding links.

#### SQL_import_statements.txt and NoSQL_import_statements.txt

These files contain the list of import statements to identify SQL and NoSQL subject systems.

#### SQL_project_versions.csv and NoSQL_Project_versions.csv

Both files contain the list of snapshots taken for all the selected subject systems. Each snapshot is identified by a commit SHA and assigned a corresponding version number incrementally from oldest to newest. In addition, each file contains the commit time of the snapshots.

#### SQL_raw_dataset.csv and NoSQL_raw_dataset.csv

The dataset files contain SATD comments identified from multiple snapshots of both SQL and NoSQL systems. It provides the comment location, and whether the comment is data-access or not. The datasets for all the research questions are derived from this raw dataset.

#### SQL_projects_commit_time_stat.csv, NSQL_projects_commit_time_stat.csv, and combined_projects_commit_time_stat.csv

Those files report the mean, standard devation and 95% confidence interval of commit time span for each SQL subject system, NoSQL subject system and the combination of the two respectively.

#### Commit_time_analysis.ipynb
This notebook shows how we generated the commit_time stats for our subject systems.

#### Commit_time_distribution_plots.ipynb
This R notebook shows the distribution of commit_time stats.

### RQ1

This folder contains the analysis scripts and data for answering RQ1.

#### projects.csv

This file contains the name of the subject systems, the latest version, the total number of commits, and the group being either SQL or NoSQL. This file is used to find the groupings and to draw the distribution of the total number of commits.

#### Data_Preparation.ipynb

This file is used to generate the files `RQ1_SQL_Diffusion_dataset.csv` and `RQ1_NoSQL_Diffusion_dataset.csv` from the raw dataset located in the `Data_collection` folder.

#### sql_G1.csv , sql_G1s.csv, sql_G3s.csv,  Nosql_G1.csv , Nosql_G2s.csv  

These datasets are subsets of the diffusion datasets grouped according to the total number of commits for each subject system.

RQ1 contains the `EvolutionPlots.ipynb` R notebook, and input datasets used to answer RQ1. The diffusion dataset contains the total number of data accesses and the regular (non-data-access) comments for SQL and NoSQL systems. The other datasets are extracted from the diffusion datasets according to the projects' total number commits.

#### EvolutionPlots.ipynb

This is an R notebook used to analyze the dataset and draw the plots reported in RQ1.

### RQ2

This folder contains the datasets and the analysis R script used to answer RQ2.

#### RQ2_SQL_Combined_Processed.csv and RQ2_NoSQL_Combined_Processed.csv

These datasets contain the `T` and the `status` of each unique comment. `T` and `status` variables are inputs to the survival analysis as they are defined in the paper.

#### RQ2_SQL_Processed.csv and RQ2_NoSQL_Processed.csv

Both files are subsets of the combined datasets obtained by removing regular (non-data-access) SATDs from the combined datasets.

#### RQ2_R_Analysis_NoteBook.ipynb

This file is an R notebook for all the analyses reported in RQ2.


### RQ3

This folder contains the topic modeling notebooks, data preparation notebook, and the manual analysis result file.

#### RQ3_SQL-TopicModeling.ipynb and RQ3_NOSQL-TopicModeling.ipynb

These notebooks contain the data cleaning and LDA topic modeling implementations for SQL and NoSQL systems, respectively.

#### RQ3_Prepare_Data_For_Manual_Analysis.ipynb

This notebook is used to generate the sample dataset from the outputs of the LDA analysis. We used stratified random sampling to generate statistically significant sample comments.

#### Labeled_data_and_codebook.xlsx

This file contains the codebook used in the manual tagging of data-access SATDs. In addition, it contains the final labels after resolving disagreements between the authors.

### RQ4

This folder contains the tagged dataset (the labeled dataset from RQ3 tagged with introduction and removal commit goals) and the notebook files for the data analysis.

#### RQ4_Dataset_Tagged.csv

This file contains information related to the introduction and removal of each data-access SATD labeled in RQ3.

#### RQ4_Analysis_Notebook.ipynb

This file contains a python notebook for the analysis reported in RQ4.

#### RQ4_R-plots.ipynb

This is an R notebook to plot the introduction and removal commit time.

### Threats_to_validity

This folder contains the file `IsDAC_check.csv` corresponding to the manual checking described in the _Threats to construct validity_. `isDAC=1` means that the file contains a direct data-access code and 0 means that it does not have a direct data-access code.

## Running the notebooks

There are either Python 3 or R notebooks in the repository. Running the notebooks require Python 3 and R kernels. We used Anaconda for Python and R environments to run the notebooks.
