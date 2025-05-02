# ai4biological-pattern

- **download_and_analyze_from_iNaturalist**
    - `download_observations.ipynb` : notebook to download data (metadata and photos) from iNaturalist
    - `annotate_unnotated_data_v3.ipynb` : notebook to fine-tune a ResNet model to predict phenology plant state by observation's photo - fine-tuned using annotate observation -> predict observation without annotations
    - **repositories**
    > *prefix_specie_place* where the specie is the spece of the observations, the place is the region of the observations (*n_a* for North America - incl. Ocean) and prefix follows this strategy:
    >    - `PROVA` for toy example - only to use at earlier stage to build models
    >    - `annotations` - data obtained via `download_observations.ipynb` only of observations with annotations
    >    - `complete` - data obtained via `download_observations.ipynb` of observations with and without annotations