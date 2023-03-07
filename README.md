# Applying Machine Learning to Understand Water Security and Water Access Inequality in Underserved Colonia Communities
This is the source code for reproducing results shown in the Colonias paper

## Dataset
Original dataset is obtained from **Rural Community Assistance Partnership** (RCAP) on the GIS web platform named [Phase II Colonia Web Map ](https://crginc.maps.arcgis.com/apps/webappviewer/index.html?id=1d3a4eefcaee45519603e4aac90a223e)

1. `Colonias.gdb`: Oringal dataset from RCAP
2. `colonias_Y_norm.csv`: preprocessed dataset for colonias with public water services from the original dataset (`Colonias.gdb`)
3. `colonias_N_norm.csv`: preprocessed dataset for colonias without public water services from the original dataset (`Colonias.gdb`)
4. `parameters_Y.csv`: clustering results (`Silhouette Score`) under different damping factors for colonias with public water services
5. `parameters_N.csv`: clustering results (`Silhouette Score`) under different damping factors for colonias without public water services
6. `colonias_Y_norm_labeled.csv`: `colonias_Y_norm.csv` attached with the optimal clustering labels for colonias with public water services
7. `colonias_N_norm_labeled.csv`: `colonias_N_norm.csv` attached with the optimal clustering labels for colonias without public water services

`colonias_N_norm.csv` and `colonias_Y_norm.csv` are inputs of Affinity Propagation algorithm.
Selected attributes and corresponding descriptions are as follows:

![image](https://user-images.githubusercontent.com/15030443/223287814-cd20de62-eddb-4217-96c2-40471e78aff2.png)

## Code Usage
### Dependencies
- Python 2.7+
- scikit-learn == 0.21
- gower 0.1.2
- pandas
- numpy
- graphviz 0.20.1
- matplotlib

You can reproduce our workflow by following steps below.
1. `ap_optimal_param.ipynb`: this code is to compare clustering results (`Silhouette Score`) under different `damping` factors and `iteration`s. You can generate `parameters_Y.csv` and `parameters_N.csv` accordingly (can be found under the folder `dataset/`).
2. `params_SS.ipynb`: plot `Silhouette Score` values under different damping factors and iterations for colonis with/without public water services.
3. `ap_get_labels.ipynb`: according to step 1, optimal parameters with the highest `Silhouette Score` will be choosen as the `input`. It outputs clustered labels under the best parameters, which will be saved in `csv` files.
4. Attach labels with original `csv` files (`colonias_N_norm.csv`, `colonias_Y_norm.csv`) into new `csv` files (`colonias_N_norm_labeled`, `colonias_Y_norm_labeled`). *(You also can update label information on the same csv files)*
5. `decision_tree.ipynb`: Generate decision tree for clustering results of colonias with/without public water services


