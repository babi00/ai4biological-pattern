# Content of the branch 'guido-clean'

This branch is meant to track the work of Guido Spina on the MSc thesis project "AI for Biological Patterns".

## guido_try_trait_analysis

This folder tracks an older version of the project that has been abandoned. It is still accessible, but its content is outdated and will not be included in the final version of the project

## invasive_plants_analysis

This folder includes the files used to study the "invasive"-"non invasive" comparison of plant species. In particular we focus on the genus "Lythrum", studying 40 species of this genus to understand why some of them are invasive (in certain regions) and some are not.

**NOTE**: in the following files, often other files are used, for example the .csv database from which the locations are extracted or similar operations. Since they are often very large, they have not been uploaded to the repository.

- `plant_zones_extraction.ipynb`: with this file we obtain, for each plant species, the regions in which they are native or non-native. 
    
    To do so, first we manually download from the database [Plants of the World Online](https://powo.science.kew.org) the dataset containing metadata related to all the species.
    Then we extract the ids of the plants we are interested in and from those we can obtain the native and non-native regions.

    **Note**: the files _species_list_lythrum.csv_, _wcvp_names.csv_, _wcvp_distribution.csv_ are used in the code but they are not present in the repository.


- `download_plant_images.ipynb`: this file is used to download the images present in the website [iNaturalist](https://www.inaturalist.org/home), using iNaturalist's API.  

    **Note**: the file _invasive_plants_name_list.csv_ is used to retrieve the taxa of the species, but it is not present in the repository. 
