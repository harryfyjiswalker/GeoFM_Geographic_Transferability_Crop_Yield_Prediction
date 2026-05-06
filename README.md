# Exploring Out-of-Domain Generalisation of AlphaEarth embeddings for crop yield prediction

This project explored the effect of reducing the dimensionality of AlphaEarth embeddings on the transferability of crop yield prediction models, inspired by the finding of Ma _et al._ (2026) that models trained on the full 64-dimensional feature set exhibit significant performance degradation under performance transfer across the US Corn Belt.[1] 

## Study Design and Results

### Study Area

Using the embedding data provided by the authors ([2]), I replicated their geographic split into the Great Plains and Eastern Temperate Forests ecoregions using the EPA Level I ecoregion boundaries.

<div align="center">

| Region                     | Observations      | Mean Yield (t/ha) |
|---------------------------|-------------------|-------------------|
| Eastern Temperate Forests | 2,608 county-year | 12.13             |
| Great Plains              | 3,459 county-year | 10.83             |

</div>

<p align="center">
  <img src="images/StudyAreaGPETF1.png" alt="Alt text" width="500"/>
</p>

### Baseline 

Before evaluating transfer experiments, we determine in-domain performances using a Random Forest classifier under leave-one-year-out (LOYO) cross validation. The model yields average in-domain $R^2$ of 0.774 and 0.657 for Great Plains and Eastern Temperate Forests, respectively. The LOYO results are displayed below.

<div align="center">
  
| Region                     | Year | R²    | RMSE  |
|----------------------------|------|-------|-------|
| Great Plains               | 2017 | 0.862 | 1.021 |
| Great Plains               | 2018 | 0.707 | 1.457 |
| Great Plains               | 2019 | 0.809 | 1.020 |
| Great Plains               | 2020 | 0.752 | 1.210 |
| Great Plains               | 2021 | 0.809 | 1.468 |
| Great Plains               | 2022 | 0.781 | 1.519 |
| Great Plains               | 2023 | 0.782 | 1.309 |
| Great Plains               | 2024 | 0.687 | 1.507 |
| Eastern Temperate Forests  | 2017 | 0.718 | 0.839 |
| Eastern Temperate Forests  | 2018 | 0.708 | 1.043 |
| Eastern Temperate Forests  | 2019 | 0.492 | 1.018 |
| Eastern Temperate Forests  | 2020 | 0.688 | 0.852 |
| Eastern Temperate Forests  | 2021 | 0.584 | 1.024 |
| Eastern Temperate Forests  | 2022 | 0.709 | 0.911 |
| Eastern Temperate Forests  | 2023 | 0.717 | 0.995 |
| Eastern Temperate Forests  | 2024 | 0.644 | 1.132 |

</div>



[1] Ma, Y., Shen, Y., Swatantran, A. and Lobell, D.B. (2026) 'Harvesting AlphaEarth: benchmarking the geospatial foundation model for agricultural downstream tasks', International Journal of Applied Earth Observation and Geoinformation, 149, p. 105258. doi: 10.1016/j.jag.2026.105258.\\

[2] Ma, Y., Shen, Y., Swatantran, A. and Lobell, D.B. (2026) Harvest_AlphaEarth. Available at: https://github.com/yuchima8/Harvest_AlphaEarth (Accessed: 6 May 2026).
