# Energy Consumption and Cost

## Overview
We attempted to build a machine learning model that could accurately predict estimated costs and consumption of energy by houses based on a variety of characteristics. Our goal is to achieve over 75% accuracy or an R<sup>2</sup> value above .80.

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

### Regional Information - Michele
Describes the energy consumption in the USA according to the geographical location
After numerous iterations and trials, our pursuit of achieving a minimum accuracy of 75% led us to explore various models such as linear regression, Random Forest, CatBoost, and Deep Learning network. We conducted thorough investigations, including the manipulation of features and targets, as well as diverse data splits to prevent the model from overfitting. ​It was only when we opted to bin the target variables that we finally attained favorable outcomes from our model. 
The refined model employed linear regression with binned targets to deliver the desired results.

#### Model 1
| Variable | Value |
| --- | --- |
| Target | totalbtu |
| Features | regionc, division, state_postal, ba_climate |
| Data Split| test_size=0.25 |
| Model | Linear Regression / Random Forest  |
| Optimizer | RandomForestRegressor |
| Model Accuracy | 0.10980100284209482 |

#### Model 2
| Variable | Value |
| --- | --- |
| Target | totalbtu |
| Features | regionc, division, state_postal, ba_climate |
| Data Split| test_size=0.4|#
| Model | Linear Regression / Random Forest  |
| Optimizer | RandomForestRegressor |
| Model Accuracy | 0.10938294576918528 |



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

### Demographic Information - Austin
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

## Summary
Our best results came after binning our target variables (whether that be `TOTALBTU` or `TOTALDOL`). This likely the result of the large variance of our target variables and as a result, it makes sense to bin them as we did. This allowed us to acheive our 75% accuracy goal and 80% R<sup>2</sup> value.
