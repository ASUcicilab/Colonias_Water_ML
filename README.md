# Applying Machine Learning to Understand Water Security and Water Access Inequality in Underserved Colonia Communities
This is the source code for reproducing results shown in the Colonias paper

## Dataset
There are two sets of datasets (`colonias_N_norm.csv` and `colonias_Y_norm.csv`) as inputs of the workflow. `colonias_N_norm.csv` contains the water service information of colonias without public water services. `colonias_Y_norm.csv` contains the water service information of colonias with public water services. You can find them under the folder `dataset/`

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
2. `params_SS_Y.ipynb/params_SS.ipynb`: plot `Silhouette Score` values under different damping factors and iterations for colonis with/without public water services.
3. `ap_get_labels.ipynb`: according to step 1, optimal parameters with the highest `Silhouette Score` will be choosen as the `input`. It outputs clustered labels under the best parameters, which will be saved in `csv` files.
4. Attach labels with original `csv` files (`colonias_N_norm.csv`, `colonias_Y_norm.csv`) into new `csv` files (`colonias_N_norm_labeled`, `colonias_Y_norm_labeled`). *(You also can update label information on the same csv files)*
5. `decision_tree.ipynb`: Generate decision tree for clustering results of colonias with/without public water services


