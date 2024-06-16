# GWU Responsible ML
Group 3, the authors of this repository, spent seven weeks developing interpretable machine learning models during Summer 2022 in Professor Patrick Hall's Responsible Machine Learning course. The objective of our project is to predict the probability of applicants being charged a higher rate than others for mortgages using the Home Mortgage Disclosure Act's historic mortgage reporting data. To avoid the impetuous of deploying black-box machine learning models into social populaces that can be adversely affected by bias, our group strived to develop explainable and interpretable predictive models that improve trust and encourage ethical decisions. 
  
## Model Details

### Authors
   * Kyle Lyon, `kylelyon@gwu.edu`
   * Charles Bloomer, `charlesbloomer@gwu.edu`
   * Zeeshan Raza, `zraza10@gwu.edu`
   * Ziyad Maknojia, `zam@gwu.edu`

### Basic Information
* **Model date**: May, 2022
* **Model version**: 2.0
* **License**: Apache 2.0
* **Model implementation code**: Responsible Machine Learning, Assignment 5, Summer 2022

### Workflow
   * First, we compared three models, then we select EBM as the best model, and then we worked on it with bias testing, red-teaming, and model debugging.

## Intended Use
* **Primary intended uses**: This research team aims to reduce discrimination and bias in the issuance of mortgage rates to applicants by providing transparency with explainable machine learning models.
* **Primary intended users**: Students, professors, and members of the George Washington University may use this repository.
* **Out-of-scope use cases**: Models that appear in this repository are for educational-purposes and should not be used to determine real-world credit worthiness.

## Training Data

* **Data dictionary**:

| Name | Modeling Role | Measurement Level| Description|
| :----: | :-------------: | :----------------: | :----------: |
| black | input | binary | whether the borrower is Black (1) or not (0)|
| asian | input | binary | whether the borrower is Asian (1) or not (0)|
| white | input | binary | whether the borrower is White (1) or not (0)|
| male | input | binary | whether the borrower is male (1) or not (0) |
| female | input | binary | whether the borrower is female (1) or not (0)|
| term 360 | input | binary | whether the mortgage is a standard 360 month mortgage (1) or a different type of mortgage (0)|
| conforming | input | binary | whether the mortgage conforms to normal standards (1), or whether the loan is different (0), e.g., jumbo, HELOC, reverse mortgage, etc.|
| debt to income ratio missing | input | binary | missing marker (1) for debt to income ratio std|
| loan amount std | input | int | standardized amount of the mortgage for applicants|
| loan to value ratio std | input | float | ratio of the mortgage size to the value of the property for mortgage applicants|
| no intro rate period std | input | binary | whether or not a mortgage does not include an introductory rate period |
| intro rate period std | input | float | standardized introductory rate period for mortgage applicants |
| property value std | input | int | value of the mortgaged property |
| income std | input | int | standardized income for mortgage applicants |
| debt to income ratio std | input | float | standardized debt-to-income ratio for mortgage applicants |
| phat | input | float | prediction probabilities of high-priced mortgage for mortgage applicants |
| r | input | int | log loss residuals for the predicted probabilities |
| high priced | target | binary| whether (1) or not (0) the annual percentage rate (APR) charged for a mortgage is 150 basis points (1.5%) or more above a survey-based estimate of similar mortgages |


* **Source of training data**: Home Mortgage Disclosure Act (HMDA) Aggregate Lending Data [[Source]](https://github.com/jphall663/GWU_rml/tree/master/assignments/data) [[Website]](https://www.ffiec.gov/hmda/history2.htm)
* **How training data was divided into training and validation data**: 70% Training, 30% Validation 
* **Number of rows in training and validation data**:
  * Training rows: 112,237, columns=23
  * Validation rows: 48,101, columns=23

## Test Data
* **Source of test data**:  Home Mortgage Disclosure Act (HMDA) aggregate lending data [[Source]](https://github.com/jphall663/GWU_rml/tree/master/assignments/data)
* **Number of rows in test data**: 19830
* **State any differences in columns between training and test data**: All the columns are as the same as the training & validation data, except for that the target variable **high priced** column does not exist in this test data.

## Model Details
* **Columns used as inputs in the final model**:
   * `property_value_std`, `no_intro_rate_period_std`, `loan_amount_std`, `income_std`, `conforming`, `intro_rate_period_std`, `debt_to_income_ratio_std`, `term_360`
* **Column(s) used as target(s) in the final model**: "high_priced"
* **Type of models**: 
  * Explainable Boosting Machine (EBM)
  * Decision Tree 
* **Software used to implement the model**: Python 3.6.9, [InterpretML](https://github.com/interpretml/interpret) v0.2.5.

## Quantitative Analysis
| Partition | AUC |
| :--------:|:---:|
| Valid | 0.7949 |

| Compare v. Control  | AIR |
| :-----------------: | :---: |
| Asian people vs. White people | 1.152 | 
|Black people vs. White people| 0.814 |
|Females vs. Males | 0.956 |

   * #### Local Feature Importance Across Models  
      Feature importance refers to techniques that assign a score to input features based on how useful they are at predicting a target variable. [[Source]](https://machinelearningmastery.com/calculate-feature-importance-with-python/)  
   ![Local Feature Importance](assignments/a02/a02_feature_importance.png)
   * #### Global Feature Importance Across Models  
      Global feature importance shows which features are globally the most important for the model. It average across all predictions we want to find the most important features and also quantify and rank this importance. [[Source]](https://www.knime.com/blog/understand-ml-model-global-feature-importance)
   ![Global Feature Importance](assignments/a02/a02_fi.png)
   * #### Partial Dependence Plots 
      The partial dependence plot shows the marginal effect one or two features have on the predicted outcome of a machine learning model. [[Source]](https://christophm.github.io/interpretable-ml-book/pdp.html)
   ![Partial Dependence Plot (1/4)](assignments/a02/partial_dependence_plots/pdp1.png)  
   ![Partial Dependence Plot (2/4)](assignments/a02/partial_dependence_plots/pdp2.png)  
   ![Partial Dependence Plot (3/4)](assignments/a02/partial_dependence_plots/pdp3.png)  
   ![Partial Dependence Plot (4/4)](assignments/a02/partial_dependence_plots/pdp4.png)  
   * #### Grid Search Results Plot  
      We use Grid Search to find a model with good accuracy and improved fairness. Grid search is a tuning technique that attempts to compute the optimum values of hyperparameters. [[Source]](https://medium.com/fintechexplained/what-is-grid-search-c01fe886ef0aa0)  
   ![Grid Search](assignments/a03/grid_search_results.png)
   * #### Best AIR and AUC  
   ![Best AUC and AIR](assignments/a03/best_auc-air.png)
   * #### Best Model Hyperparameters  
   ![Best Parameters](assignments/a03/a03_best_parameters.png)
   * #### Model Extraction Attack  
   ![Model Extraction Attack](assignments/a04/extraction_attack.png)
   * #### Stolen Decision Tree Model  
   ![Stolen Model](assignments/a04/decision_tree.png)
   * #### Variable Importance: H20 Distributed Randomo Forest  
   ![Variable Importance](assignments/a04/a04_variable_importance.png)
   * #### Sensitivity Analysis: Stress Testing  
   ![Sensitivity Analysis](assignments/a05/sensitivity-analysis.png)
   * #### Residual Analysis  
      We used the residual plot to find outliers to improve model training.  
   ![Residual Analysis](assignments/a05/residual-analysis.png)

## Ethical Considerations
   * Like many other models, our machine learning model's accuracy is susceptible to shifts in the real-world, and in this particular case, economic shifts (e.g. recession).
   * Analysis that contains racial data are usually susceptible to legalities such as disparate treatment. Data pre-processing should be scrutinized for legal issues.
   * Bias testing and remediation ensures models are assesing what they are supposed to be testing and nothing is intefering with results. Failure to implement bias testing and remediation can cause discrimination and societal harm.
   * Although this model was tested and remediated for bias, there is much more to bias than models and data, and this model should be monitored for bias issues moving forward.
