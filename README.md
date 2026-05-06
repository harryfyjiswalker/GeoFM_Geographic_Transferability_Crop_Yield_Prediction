# Exploring Out-of-Domain Generalisation of AlphaEarth embeddings for crop yield prediction

This project explored the effect of reducing the dimensionality of AlphaEarth embeddings on the transferability of crop yield prediction models, inspired by the finding of Ma _et al._ (2026) that models trained on the full 64-dimensional feature set exhibit significant performance degradation under performance transfer across the US Corn Belt.[1] 

## Data and Baselines

### Study Area

Using the embedding data provided by the authors ([2]), the geographic split used by Ma _et al._ -- into the Great Plains and Eastern Temperate Forests ecoregions -- is replicated using the EPA Level I ecoregion boundaries.

<div align="center">

| Region                     | Observations      | Mean Yield (t/ha) |
|---------------------------|-------------------|-------------------|
| Eastern Temperate Forests | 2,608 county-year | 12.13             |
| Great Plains              | 3,459 county-year | 10.83             |

</div>

<p align="center">
  <img src="images/StudyAreaGPETF1.png" alt="Alt text" width="500"/>
</p>

### Baselines 

Before evaluating transfer experiments, the in-domain performances are determined using a Random Forest classifier under leave-one-year-out (LOYO) cross validation. The model yields average in-domain $R^2$ of 0.774 and 0.657 for Great Plains and Eastern Temperate Forests, respectively. The LOYO results are displayed below.

<div align="center">

| Year | GP R² | GP RMSE | ETF R² | ETF RMSE |
|:----:|:-----:|:-------:|:------:|:--------:|
| 2017 | 0.862 | 1.021   | 0.718  | 0.839    |
| 2018 | 0.707 | 1.457   | 0.708  | 1.043    |
| 2019 | 0.809 | 1.020   | 0.492  | 1.018    |
| 2020 | 0.752 | 1.210   | 0.688  | 0.852    |
| 2021 | 0.809 | 1.468   | 0.584  | 1.024    |
| 2022 | 0.781 | 1.519   | 0.709  | 0.911    |
| 2023 | 0.782 | 1.309   | 0.717  | 0.995    |
| 2024 | 0.687 | 1.507   | 0.644  | 1.132    |

</div>

The transfer results with the full 64-dimensional embeddings are then evaluated. Similar performance degradation to Ma _et al._ is observed.

<div align="center">

| Transfer Direction | Target R² | Target RMSE |
|-------------------|-----------|-------------|
| ETF → GP          | -0.0894   | 2.8677      |
| GP → ETF          | 0.4976    | 1.1433      |

</div>

## Methods

### Quantifying Domain Shift

Before attempting dimensionality reduction, the degree of domain shift in the AEF embedding space was analysed:



[1] Ma, Y., Shen, Y., Swatantran, A. and Lobell, D.B. (2026) 'Harvesting AlphaEarth: benchmarking the geospatial foundation model for agricultural downstream tasks', International Journal of Applied Earth Observation and Geoinformation, 149, p. 105258. doi: 10.1016/j.jag.2026.105258.\\

[2] Ma, Y., Shen, Y., Swatantran, A. and Lobell, D.B. (2026) Harvest_AlphaEarth. Available at: https://github.com/yuchima8/Harvest_AlphaEarth (Accessed: 6 May 2026).
