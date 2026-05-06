# Exploring Out-of-Domain Generalisation of AlphaEarth embeddings for crop yield prediction

This project explored the effect of reducing the dimensionality of AlphaEarth embeddings on the transferability of crop yield prediction models, inspired by the finding of Ma _et al._ (2026) that models trained on the full 64-dimensional feature set exhibit significant performance degradation under performance transfer across the US Corn Belt.[1] 

##Study Area

Using the embedding data provided by the authors ([2]), I replicated their geographic split into the Great Plains and Eastern Temperate Forests ecoregions using the EPA Level I ecoregion boundaries.

| Category        | Region                     | Observations              | Mean Yield (t/ha) |
|----------------|---------------------------|---------------------------|-------------------|
| Source (East)  | Eastern Temperate Forests | 2,608 county-year         | 12.13             |
| Target (West)  | Great Plains              | 3,459 county-year         | 10.83             |

<p align="center">
  <img src="images/StudyAreaGPETF1.png" alt="Alt text" width="500"/>
</p>




[1] Ma, Y., Shen, Y., Swatantran, A. and Lobell, D.B. (2026) 'Harvesting AlphaEarth: benchmarking the geospatial foundation model for agricultural downstream tasks', International Journal of Applied Earth Observation and Geoinformation, 149, p. 105258. doi: 10.1016/j.jag.2026.105258.\\

[2] Ma, Y., Shen, Y., Swatantran, A. and Lobell, D.B. (2026) Harvest_AlphaEarth. Available at: https://github.com/yuchima8/Harvest_AlphaEarth (Accessed: 6 May 2026).
