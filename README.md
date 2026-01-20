# Content of the branch 'guido-clean'

This branch is meant to track the work of Guido Spina on the MSc thesis project "XAI tools to predict biological invasiveness: a case study in plants". Not all files used to carry out the work are included in this sections: the code written by barbara can be found in the branch 'clean-barbara'.

## guido_try_trait_analysis

This folder tracks an older version of the project that has been abandoned. It is still accessible, but its content is outdated and will not be included in the final version of the project

## invasive_plants_analysis

This folder includes the files used to study the "invasive"-"non invasive" comparison of plant species. In particular we focus on the genus "Lythrum", studying 40 species of this genus to understand why some of them are invasive (in certain regions) and some are not.

**NOTE**: in the following files, often other files are used, for example the .csv database from which the locations are extracted or similar operations. Since they are often very large, they have not been uploaded to the repository.

- `LOSO_training_no_hyssopifolia`: this file trains the models for each species using LOSO validation, excluding *L. hyssopifolia* from the dataset.

- `NEW_group_k_fold.ipynb`: in this file we perform the LOSO validation to obtain the first results that prompt us to reflect on the role of L. hyssopifolia (which obtained terrible results) and finally to exclude it from the dataset (together with 'embeddings_UMAP.ipynb').

- `NEW_model_grid_search.ipynb`: this file contains preliminary tests on the two classes model, opposed to the previous (wrong) tests on the three classes model. It proves that BioCLIP is still the best performing model, but final tests have been performed in the file "final_model_training.ipynb"

- `analysis_of_prediction.ipynb`: after obtaining the prediction (invasive, non-invasive) for each sample utilizing the correct model, in this file we perform some analysis to extract metrics such as F1 score or accuracy.

- `download_plant_images.ipynb`: this file is used to download the images present in the website [iNaturalist](https://www.inaturalist.org/home), using iNaturalist's API.  

    **Note**: the file _invasive_plants_name_list.csv_ is used to retrieve the taxa of the species, but it is not present in the repository.


- `embeddings_UMAP.ipynb`: in this file we take the embeddings and we use UMAP to map them into a 2D space to observe the distance between different clusters of species.

- `final_model_training.ipynb`: this file trains a model using the correct classifier logic, but does it without splitting the dataset into species. No LOSO, a single model trained with 80-20 split. It demonstrates that the classifier obtains good performances using a regular split.

- `final_model_evaluation.ipynb`: this file is used to evaluate the specific models trained using the LOSO validation, predicting each image using the correct model. The models were trained using either 'save_models_trained_with_hyssopifolia.ipynb' (*L. hyssopifolia* present in the training data) or 'LOSO_training_no_hyssopifolia.ipynb' (not present in the training data).

- `image_sampling_distribution.ipynb`: we use KL distance and Entropy to compare the distributions of the images and the distribution of the sampling used to build the validation clusters. It showed that the two distributions were similar, but was not used for the final work.

- `model_grid_search.ipynb`: this grid search for the model hyperparameters version uses three classes. However it is inserted in this sections because it shows interesting behaviors such as the augmentation not improving the accuracy significantly and Cross Entropy being a better loss type than Focal Loss.

- `plant_distribution.ipynb`: this file contains both analysis and plots on the distribution of the species and analysis on the results of the LOSO validation with two species.

- `predictions_all_models.ipynb`: we use each model (one for each species) to predict the output (invasive or non-invasive) for every sample, separated per species, and save the output into a csv file.

- `predictions_masked_regions_with_logits.ipynb`: similarly to what 'final_model_evaluation.ipynb' does, with this file we generate the prediction and the logits for the images when masking the regions, to understand if the prediction change from the original images.

- `predictions_with_logits.ipynb`: similar to 'predictions_all_models.ipynb' but includes the logits for the prediction.

- `region_labelling.ipynb`: generate a file by labeling each image with the morphological regions it contains, according to the clusters of single regions. Each region belongs to an image, therefore we generalize by going from labeled regions to labeled images.

- `save_models_trained_with_hyssopifolia.ipynb`: save the models trained using LOSO validation. This version of the training includes *L. hyssopifolia* in the training data.

- `testing_strategies_training.ipynb`: a file used to perform some tests on the training, for example what happens if we augment the dataset or remove some species from it.

- `unique_traits.ipynb`: after biologist [Riccardo Ciarle](https://www.linkedin.com/in/riccardo-ciarle-b41a482b9/?originalSubdomain=nz=) kindly shared with us the list of specific morphological traits belonging to each species, we used this file to analyze which traits were exclusive for invasive species, which ones for non-invasive species and which ones were common to both. We also determined the traits that belonged to most species for all three categories.
  
### unused_files
**Old files or files not taken into consideration for the final work**

- `classifier_bioclip_2.ipynb`: this file tracks an old version of the work when we were wrongly using 3 classes instead of 2. **TO BE IGNORED**

- `classify_photos.ipynb`: In this file we classify each photo of a particular species with either "Invasive", "Native" or "Introduced non-invasive". To do so, we take the coordinate of each picture and see in which bounding box it falls into (file "Updated_Complete_Region_Dataset.csv"). If it falls into more than one bounding box, we check for which one it is closer to center.
This has been modifyied for the "two classes" approach into "classify_photos_2_classes.ipynb". **TO BE IGNORED**

- `classify_photos_2_classes.ipynb`: Classify the species not based on the location, but based exclusively on the potential of a species to be invasive or non invasive.

- `coordinates_mapping.ipynb`: Given the list of original regions, we asked ChatGPT (GPT-4o) to extract for each of them the Nominatim API query to extract the point coordinates and the bounding box coordinates. In this file we execute the API calls to obtain the coordinates for each region. If for some region the API call fails, we inspect these cases manually. Not used anymore since we moved to the "two classes" approach. **TO BE IGNORED**

- `group_k_fold.ipynb`: first test of LOSO validation with n-splits (initially 28 to group together species with very few samples). Its analysis is contained in 'group_k_fold_analysis.ipynb". Still using three classes, therefore **TO BE IGNORED**

- `group_k_fold_analysis.ipynb`: some analysis and plotting of the results of 'group_k_fold.ipynb'. Uses three classes so **TO BE IGNORED**

- `image_classifier.ipynb`: some tests for the original three-classes classifier. **TO BE IGNORED** 

- `k_fold.ipynb`: 5 splits k-fold similar to 'group_k_fold.ipynb'. It also uses three classes, so **TO BE IGNORED**
  
- `plant_zones_extraction.ipynb`: with this file we obtain, for each plant species, the regions in which they are native or non-native. 
    
    To do so, first we manually download from the database [Plants of the World Online](https://powo.science.kew.org) the dataset containing metadata related to all the species.
    Then we extract the ids of the plants we are interested in and from those we can obtain the native and non-native regions.

    **Note**: the files _species_list_lythrum.csv_, _wcvp_names.csv_, _wcvp_distribution.csv_ are used in the code but they are not present in the repository.

- `regions_mapping.ipynb`: using an LLM to map all the regions for each sample to a normalized version of the region in order to determin
ate if they are invasive, non-invasive or native. Since the three-classes classification has been abandoned, this is **TO BE IGNORED**
