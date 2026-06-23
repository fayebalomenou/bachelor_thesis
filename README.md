# Bachelor Thesis
This repository contains all the code for the BSc thesis with title **Relationship between Occupancy and Indoor Environmental Conditions in the NU Building**
The project investigates the relationship between occupancy and the indoor environmental variables using the available sensor data from Floors 10, 11 and 12 of the NU Building of VU Amsterdam. 
The analysis is supported by Semantic Modeling using **SAREF, SAREF4BLDG and OM 1.8 ontologies**. 

## Setup
To run the code ensure you have **Python 3.10** or higher. The jupyter notebooks can be run using **Jupyter Lab** or **VSCode**.

## Data Access
Due to size limitations the individual .ttl files of each floor and the merged .ttl file, containing the Knowledge Graph, have been uploaded to Google Drive and can be accessed using the following links:
- floor_10.ttl:https://drive.google.com/file/d/1u6mfjlGhzj8jXhIHOuFcRhY_WewQokvM/view?usp=sharing
- floor_11.ttl: https://drive.google.com/file/d/1EHwOfRa7C5rB1PJyY22EMsgcYNMFzKoM/view?usp=sharing
- floor_12.ttl: https://drive.google.com/file/d/1ene8Cf8bYxk7x04T4HoGoPc1zgmIph4f/view?usp=sharing
- merged_floors.ttl: https://drive.google.com/file/d/184tBhy7qmGNG0nqj8OQS15nezL8XBe4z/view?usp=sharing

## Code Execution Order
### 1. floor-conversions.ipynb
Run the floor-conversions.ipynb notebook to create the individual .ttl files for each floor.
### 2. merge-floors.ipynb
Run the merge-floors.ipynb notebook, which merges the previous created RDF files into one .ttl file, containing the Knowledge Graph.
### 3. QLever
Due to size limitations QLever was deployed on a Google Cloud Compute Engine Virtual Machine in order to store and query the Knowledge Graph. The merged_floors.ttl was downloaded to the VM from Google Drive using *gdown* and was indexed in order to be queryable. 
The **ENDPOINT** in each of the jupyter notebooks in the **notebooks** folder needs to be manually updated in order to point to the most current QLever instance.
### 4. SPARQL_queries.ipynb
This notebook is used for validating the structure of the created Knowledge Graph and for retrieving statistics of the indoor environmental variables it contains.
### 5. occupancy_proxy.ipynb
This notebook is used for deriving the occupancy proxies for MCO and Thingy sensors. The resulting Python Dataframes containing the occupancy labels (df_mco_occupancy.pkl and df_thingy_occupancy.pkl) are located in the **data** folder.
### 6. random_forest.ipynb
This notebook is used for the Random Forest Analysis. Environmental features are queried separately and merged with the previous created occupancy labels. The resulting Python Dataframes (df_mco_raw.pkl and df_thingy_raw.pkl) are located in the **data** folder.

## Reproducibility 
The code can be executed without regenerating anything as long as the path configuration is updated to match the   
 
