# Content of the branch 'guido-clean'

This branch is meant to track the work of Guido Spina on the MSc thesis project "XAI tools to predict biological invasiveness: a case study in plants".

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

- `NEW_model_grid_search.ipynb`: this file contains preliminary tests on the two classes model, opposed to the previous (wrong) tests on the three classes model. It proves that BioCLIP is still the best performing model, but final tests have been performed in the file "final_model_training.ipynb"

- `classifier_bioclip_2.ipynb`: this file tracks an old version of the work when we were wrongly using 3 classes instead of 2. **TO BE IGNORED**

- `classify_photos.ipynb`: In this file we classify each photo of a particular species with either "Invasive", "Native" or "Introduced non-invasive". To do so, we take the coordinate of each picture and see in which bounding box it falls into (file "Updated_Complete_Region_Dataset.csv"). If it falls into more than one bounding box, we check for which one it is closer to center.
This has been modifyied for the "two classes" approach into "classify_photos_2_classes.ipynb". **TO BE IGNORED**

- `classify_photos_2_classes.ipynb`: Classify the species not based on the location, but based exclusively on the potential of a species to be invasive or non invasive.

- `coordinates_mapping.ipynb`: Given the list of original regions, we asked ChatGPT (GPT-4o) to extract for each of them the Nominatim API query to extract the point coordinates and the bounding box coordinates. In this file we execute the API calls to obtain the coordinates for each region. If for some region the API call fails, we inspect these cases manually. Not used anymore since we moved to the "two classes" approach. **TO BE IGNORED**

  
