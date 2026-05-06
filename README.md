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

<table>
  <tr>
    <td valign="top">

<b>Great Plains</b><br><br>

<table>
<tr><th>Year</th><th>R²</th><th>RMSE</th></tr>
<tr><td>2017</td><td>0.862</td><td>1.021</td></tr>
<tr><td>2018</td><td>0.707</td><td>1.457</td></tr>
<tr><td>2019</td><td>0.809</td><td>1.020</td></tr>
<tr><td>2020</td><td>0.752</td><td>1.210</td></tr>
<tr><td>2021</td><td>0.809</td><td>1.468</td></tr>
<tr><td>2022</td><td>0.781</td><td>1.519</td></tr>
<tr><td>2023</td><td>0.782</td><td>1.309</td></tr>
<tr><td>2024</td><td>0.687</td><td>1.507</td></tr>
</table>

    </td>
    <td valign="top">

<b>Eastern Temperate Forests</b><br><br>

<table>
<tr><th>Year</th><th>R²</th><th>RMSE</th></tr>
<tr><td>2017</td><td>0.718</td><td>0.839</td></tr>
<tr><td>2018</td><td>0.708</td><td>1.043</td></tr>
<tr><td>2019</td><td>0.492</td><td>1.018</td></tr>
<tr><td>2020</td><td>0.688</td><td>0.852</td></tr>
<tr><td>2021</td><td>0.584</td><td>1.024</td></tr>
<tr><td>2022</td><td>0.709</td><td>0.911</td></tr>
<tr><td>2023</td><td>0.717</td><td>0.995</td></tr>
<tr><td>2024</td><td>0.644</td><td>1.132</td></tr>
</table>

    </td>
  </tr>
</table>



[1] Ma, Y., Shen, Y., Swatantran, A. and Lobell, D.B. (2026) 'Harvesting AlphaEarth: benchmarking the geospatial foundation model for agricultural downstream tasks', International Journal of Applied Earth Observation and Geoinformation, 149, p. 105258. doi: 10.1016/j.jag.2026.105258.\\

[2] Ma, Y., Shen, Y., Swatantran, A. and Lobell, D.B. (2026) Harvest_AlphaEarth. Available at: https://github.com/yuchima8/Harvest_AlphaEarth (Accessed: 6 May 2026).
