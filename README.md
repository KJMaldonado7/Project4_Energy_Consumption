# Energy Consumption and Cost

## Overview
We attempted to build a machine learning model that could accurately predict estimated costs and consumption of energy by houses based on a variety of characteristics. Our goal is to achieve over 75% accuracy or an R<sup>2</sup> value above 0.75.

### Data Source
We used data from the US Energy Information Administration's [2020 Residential Energy Consumption Survey](https://www.eia.gov/consumption/residential/data/2020/index.php?view=microdata). We initially downloaded this data as a CSV for initial cleaning. That file is in the main repo under `recs2020_public_v7.csv`.

## Data Preprocessing
The file in which we preprocessed our data can be found in the main repo under `Project-4-DataFrames.ipynb`.

We first divided our data into four different areas:
* Housing Charateristics (e.g. when the house was made, exterior material)
* Energy-efficient upgrades (e.g. are LED bulbs used in the house, presence of solar panels)
* Regional Information (e.g. where the house is located in the United States)
* Demographic Information (e.g. characteristics about occupants of the house)

We saved those tables in the `Table_CSVs` directory, as well as other tables outlining the meaning of the values of each column.

We created a SQL database of our tables in PostgreSQL. This was because the data was already tabular in origin. That database creation can be found in the main repo under `Energy_Output_Expenses.sql`.

### Target Variables
For all of our models, we used the target variables of `TOTALBTU` (amount of energy used) or `TOTALDOL` (amount of money spent on energy generation).

### Variable to be removed
For all of ur models, we removed the `DOIED` variable, which is just an identification variable.

## Compiling, Training, and Evaluating the Models

### Housing Characterics - Keisha
We chose this model and here's why.

#### Model 1
*EXAMPLE TABLE*

| Variable | Value |
| --- | --- |
| Number of Hidden Layers | 2 |
| Hidden Layer 1 Neurons | 80 |
| Hidden Layer 1 Activation Function | ReLU |
| Hidden Layer 2 Neurons | 30 |
| Hidden Layer 2 Activation Function | ReLU |
| Output Layer Activation Function | Sigmoid |
| Number of Epochs | 100 |
| Model Accuracy | 0.7301457524299622 |

*Commentary on results. Next step chosen and why.*

**REPEAT BASED ON NUMBER OF STEPS IN YOUR CODE**

#### Model ___ (final)
*EXAMPLE TABLE*

| Variable | Value |
| --- | --- |
| Number of Hidden Layers | 2 |
| Hidden Layer 1 Neurons | 80 |
| Hidden Layer 1 Activation Function | ReLU |
| Hidden Layer 2 Neurons | 30 |
| Hidden Layer 2 Activation Function | ReLU |
| Output Layer Activation Function | Sigmoid |
| Number of Epochs | 100 |
| Model Accuracy | 0.7301457524299622 |

*Commentary on results. We finally achieved ____ result.*

### Energy-efficient upgrades - Joanna
In our journey to improve energy efficiency predictions, we tried out several different approaches to make sure our models were accurate at least close to 75% of the time. We tested various methods like Linear Regression, Random Forest, and Deep Learning networks. Additionally, we refined our data analysis techniques, implementing various data splitting strategies to foster improved learning within the models, avoiding mere memorization. 

The trial files are stored in the directory 'energy_consumption_ML_tries'.

The ultimate model is located in the root directory and named 'Final_Energy_Consumption_Model.ipynb'.

#### Model 1

| Variable | Value |
| --- | --- |
| Target | totalbtu |
| Features | dwcycle, tvtype1, typetherm, lgtinled, smartmeter, solar, elecveh, totaldol |
| Data Split| *test_size=0.2*|
| Model | Random Forrest |
| Optimizer | RandomForestRegressor|
| R<sup>2</sup> | 0.5760602548867669

#### Model 2

| Variable | Value |
| --- | --- |
| Target | totalbtu |
| Features |  dwcycle, tvtype1, typetherm, lgtinled, smartmeter, solar, elecveh, totaldol  |
| Data Split| *test_size=0.2*|
| Model | Random Forrest |
| Optimizer | RandomForestRegressor|
| R<sup>2</sup> | 0.5772147759816009

#### Model 3

| Variable | Value |
| --- | --- |
| Target | totalbtu |
| Features |  dwcycle, tvtype1, typetherm, lgtinled, smartmeter, solar, elecveh, totaldol |
| Data Split| *test_size=0.2*|
| Model | Linear Regression |
| Optimizer | Linear Regression |
| R<sup>2</sup> | 0.5994969333217187 |

#### Model 4

| Variable | Value |
| --- | --- |
| Target | totalbtu |
| Features |  dwcycle, tvtype1, typetherm, lgtinled, smartmeter, solar, elecveh, totaldol |
| Data Split| *test_size=0.1*|
| Model | Linear Regression |
| Optimizer | Linear Regression |
| R<sup>2</sup> | 0.6994187472726883 |

#### Model 5 (final)

| Variable | Value |
| --- | --- |
| Target | totalbtu |
| Features |  dwcycle, tvtype1, typetherm, lgtinled, smartmeter, solar, elecveh, totaldol  |
| Data Split| *test_size=0.2*|
| Model | Linear Regression |
| Optimizer | Linear Regression |
| R<sup>2</sup> | 0.7933460682175177 |

In our final attempt, we implemented a crucial step by categorizing the energy consumption DataFrame into three distinct bins: 'Low', 'Medium', and 'High'. This categorization was based on specific thresholds of 55000 and 95000, effectively dividing the data into different consumption levels for better analysis. The bin_total_btu function was applied to create a new column 'BTU_Bin' within the DataFrame, signifying the respective binned categories. Following this, one-hot encoding was utilized on the 'BTU_Bin' column to transform it into a numerical format suitable for machine learning models. During this process, the target variable 'totalbtu' was separated and labeled as 'y', while the features were organized and stored as 'X' for subsequent modeling and in-depth analysis. This systematic approach directly aligns with our primary objective of enhancing energy efficiency predictions by incorporating categorized energy levels into our modeling pipeline, thereby facilitating more accurate and insightful predictive modeling outcomes.

### Regional Information - Michele
After conducting ten iterations and trials, our objective of achieving a minimum accuracy threshold of 75% or an R-squared value of 0.75 led us to explore several models, including Linear Regression, Random Forest, CatBoost, LightGBM, and Deep Learning Network. Throughout these endeavors, we adjusted hyperparameters, engineered features, manipulated targets, and employed diverse data splits to safeguard against model overfitting. ​However, it was only after the decision to discretize the target variables that we ultimately realized favorable outcomes from our model.
The refined model employed linear regression with binned targets to deliver the desired results.

The tables below summarize the most pertinent experiments conducted along with their respective results. Each table's name corresponds to the specific model attempt, providing a clear reference for further analysis and comparison.

The attempts files are saved in the folder `regional_attempts`.

The final model is on the root under the name `Final_Regional_Model.ipynb`

#### Model 1
| Variable | Value |
| --- | --- |
| Target | totalbtu |
| Features | regionc, division, state_postal, ba_climate |
| Data Split| test_size=0.25 |
| Model | Linear Regression / Random Forest  |
| Optimizer | RandomForestRegressor |
| R<sup>2</sup> | 0.10980100284209482 |

#### Model 4
| Variable | Value |
| --- | --- |
| Target | totalbtu |
| Features | regionc, division, state_postal, ba_climate |
| Data Split| test_size=0.2|
| Model | *CatBooster*  |
| R<sup>2</sup> | 0.11186680602851973|

#### Model 5
| Variable | Value |
| --- | --- |
| Target | totalbtu |
| Features | regionc, division, state_postal, ba_climate |
| Data Split| test_size=0.2|
| Model | *LightGBM*  |
| R<sup>2</sup> | 0.11176486825412113|

#### Model 9
| Variable | Value |
| --- | --- |
| Target | *totalbtu*|
| Features | regionc, division, state_postal, ba_climate |
| Target preparation | *StandardScaler*|
| Data Split| test_size=0.2|
| Model | *Keras Sequential*  |
| Number of Hidden Layers | 2 |
| Hidden Layer 1 Neurons | *80* |
| Hidden Layer 1 Activation Function | ReLU |
| Hidden Layer 2 Neurons | *30* |
| Hidden Layer 2 Activation Function | ReLU |
| Output Layer Activation Function | *Sigmoid* |
| Number of Epochs | *100* |
| Model Accuracy | 0.0000e+00 |

#### Model 10 - (final)
| Variable | Value |
| --- | --- |
| Target | totalbtu *(binned the Target)*|
| Features | regionc, division, state_postal, ba_climate |
| Data Split| *test_size=0.05* |
| Model | Linear Regression  |
| R<sup>2</sup> | 0.7529492375445945 |

After binning the total_btu column, finally, we got R<sup>2</sup> as 0.75.
```# Define a function to perform binning on TOTALBTU column
def bin_total_btu(total_btu):
    if total_btu < 55000:
        return 'Low'
    elif total_btu >= 55000 and total_btu < 95000:
        return 'Medium'
    else:
        return 'High'
```


### Demographic Information - Austin
We pulled demographic information from the energy consumption survey including data such as the age of the primary homeowner, number of children and total household members, and total household income, among other things. Our goal was to see if a machine learning model could accurately predict the home's total energy consumption ('TOTALBTU') based on these demographic characteristics.

Our first attempt involved setting the target variable as 'TOTALBTU' and the feature variables as the rest of the columns (minus the ID column) and initializing a linear regression model. This model proved to be quite ineffective, returning an R<sup>2</sup> score of just 0.19.

Our second attempt involved creating a scaler instance and using a Keras Seaquential model with three layers (relu, relu and sigmoid activations). However, his model consistently returned an error message at the training step and was ultimately unsuccessful.

The final and most successful attempt incorprated binning of the 'TOTALBTU' column into three bins of 'Low,' 'Medium,' and 'High' energy output before initializing a linear regression model. With the data grouped into three distinct categories, the model was much more successful in predicting household energy output and returned an R<sup>2</sup> score of 0.79.

#### Model 1

| Variable | Value |
| --- | --- |
| Target | totalbtu |
| Features | hhsex, hhage, employhh, education, sdescent, householder_race, nhsldmem, numchild, moneypy |
| Data Split| test_size=0.2 |
| Model | Linear Regression |
| Model Accuracy | 0.18746129854499471 |

#### Model 2 

| Variable | Value |
| --- | --- |
| Target | totalbtu |
| Features | hhsex, hhage, employhh, education, sdescent, householder_race, nhsldmem, numchild, moneypy |
| Target preparation | *StandardScaler*|
| Data Split| random_state=78 |
| Model | Keras Sequential  |
| Number of Hidden Layers | 2 |
| Hidden Layer 1 Neurons | *6* |
| Hidden Layer 1 Activation Function | ReLU |
| Hidden Layer 2 Neurons | *6* |
| Hidden Layer 2 Activation Function | ReLU |
| Output Layer Activation Function | *Sigmoid* |
| Number of Epochs | *100* |
| Model Accuracy | N/A - error |

#### Model 3 - (final) 

| Variable | Value |
| --- | --- |
| Target | totalbtu |
| Features | hhsex, hhage, employhh, education, sdescent, householder_race, nhsldmem, numchild, moneypy |
| Target preparation | *StandardScaler*|
| Data Split| test_size=0.1, random_state=45 |
| Model | Linear Regression  |
| Model Accuracy | 0.7938565177892568 |

On the final model, after we binned the target we were finally able to reach over 79% accuracy.
```def bin_total_btu(total_btu):
    if total_btu < 55000:
        return 'Low'
    elif total_btu >= 55000 and total_btu < 95000:
        return 'Medium'
    else:
        return 'High`

## Summary
Our best results came after binning our target variables (whether that be `TOTALBTU` or `TOTALDOL`). This likely the result of the large variance of our target variables and as a result, it makes sense to bin them as we did. This allowed us to achieve our 75% accuracy goal and 80% R<sup>2</sup> value.
