# GWU_Responsible_Machine_Learning
Group 3, the authors of this repository, spent seven weeks developing interpretable machine learning models during Summer 2022 in Professor Patrick Hall's Responsible Machine Learning course. The objective of our project is to predict the probability of applicants being charged a higher rate than others for mortgages using the Home Mortgage Disclosure Act's historic mortgage reporting data. To avoid the impetuous of deploying black-box machine learning models into social populaces that can be adversely affected by bias, our group strived to develop explainable and interpretable predictive models that improve trust and encourage ethical decisions. 

## Authors

* **Person or organization developing model**:
  * Kyle Lyon, `kylelyon@gwu.edu`
  * Charles Bloomer, `insert email`
  * Zeeshan Raza, `zraza10@gwu.edu`
  * Ziyad Maknojia, `zam@gwu.edu`
  
## Model Details

### Basic Information
* **Model date**: May, 2022
* **Model version**: 1.0
* **Model type**: Explainable Boosting Machine (EBM)
* **License**: Apache
* **Model implementation code**: TBD

### Intended Use
* **Primary intended uses**: add text
* **Primary intended users**: add text
* **Out-of-scope use cases**: add text

### Training Data


* **Data dictionary**:

| Name | Modeling Role | Measurement Level| Description|
| ---- | ------------- | ---------------- | ---------- |

* **Source of training data**: add text
* **How training data was divided into training and validation data**: add num
* **Number of rows in training and validation data**: 
  * Training rows: add num
  * Validation rows: add num

### Evaluation Data

### Test Data
* **Source of test data**: add text
* **Number of rows in test data**: add num
* **State any differences in columns between training and test data**: add text

### Model Details
* **Columns used as inputs in the final model**:
   * <pre><code>rem_x_names = ['property_value_std',
               'no_intro_rate_period_std',
               'loan_amount_std',
               'income_std',
               'conforming',
               'intro_rate_period_std',
               'debt_to_income_ratio_std',
               'term_360']</code><pre> 
* **Column(s) used as target(s) in the final model**: add text
* **Type of models**: 
  * add text 
* **Software used to implement the model**: add text
* **Version of the modeling software**: TBD
* **Hyperparameters or other settings of your model**:
   * <pre><code>rem_params = {'max_bins': 512,
              'max_interaction_bins': 16,
              'interactions': 10,
              'outer_bags': 4,
              'inner_bags': 0,
              'learning_rate': 0.001,
              'validation_size': 0.25,
              'min_samples_leaf': 5,
              'max_leaves': 5,
              'early_stopping_rounds': 100.0,
              'n_jobs': NTHREAD, 
              'random_state': SEED}</code></pre>

### Quantitative Analysis
  * #### Week 1:


  * #### Week 2:
      * Local Feature Importance Across Models
         * ![Local Feature Importance](assignments/a02/a02_feature_importance.png)
      * Global Feature Importance Across Models
         * ![Global Feature Importance](assignments/a02/a02_fi.png)
      * Partial Dependence

  * #### Week 3
     * Grid Search Results Plot
        * ![Grid Search](assignments/a03/grid_search_results.png)
     * Best AIR and AUC
        * ![Best AUC and AIR](assignments/a03/best_auc-air.png)
     * Best Model Hyperparameters
        * ![Best Parameters](assignments/a03/a03_best_parameters.png)
     * Best Model Features
        * ![Best Model Features](assignments/a03/a03_best_parameters.png)


  * #### Week 4
     * Model Extraction Attack
        * ![Model Extraction Attack](assignments/a04/extraction_attack.png)
     * Stolen Decision Tree Model
        * ![Stolen Model](assignments/a04/decision_tree.png)
     * Variable Importance: H20 Distributed Randomo Forest
        * ![Variable Importance](assignments/a04/a04_variable_importance.png)


  * #### Week 5


  * #### Week 6

### Ethical Considerations
