# Predicting Life Expectancy from Health and Economic Indicators

## Context 
The life expectancy of a country is a crucial indicator of its healthcare quality, influenced by various factors such as HIV prevalence, healthcare funding, and other less tangible elements. Understanding these determinants is essential for a nation to formulate policies and strategies aimed at enhancing its citizens' quality of life. Moreover, this knowledge is beneficial for businesses impacted by life expectancy trends, such as life insurance providers, as it enables them to adapt and optimize their operations in response to these dynamics. Therefore, developing a model that not only predicts a nation's life expectancy with accuracy but also illuminates the contributing factors and their impacts is invaluable for healthcare, political, and economic planning at a national level but also has potential applications at a more localized scale, such as in neighborhood-level planning and analysis.

## Predicting Life Expectancy: Its Value Across Sectors

###  **Business Implications**
- **Insurance Sector**: Accurate life expectancy predictions could be invaluable in the insurance world, especially for life insurance and annuities. Premiums are often set to offset the information asymmetry that insurance companies grapple with. These predictions may help in reducing this asymmetric information, setting premiums accordingly, and determining financial reserves.
- **Pension Funds**: Additionally, understanding life expectancy trends  in a region aids pension funds in balancing their liabilities and ensuring they're financially prepared for long-term payouts.
- **Targeted Products and Services**: Companies can develop and market products that cater to various age groups, influenced by life expectancy trends. This is particularly relevant in retirement planning and healthcare products.

###  **Economic Impact**
- **Policy and Governance**: Governments can utilize life expectancy forecasts for critical policy-making decisions, such as setting retirement ages and planning for social security and healthcare funding.
- **Labor Market Dynamics**: These predictions can help in shaping the workforce, retirement policies, and skill development programs, especially for older workers.
- **Investment Strategies**: Life expectancy trends can guide investors and financial advisors, particularly in sectors like healthcare and retirement living.

###  **Healthcare Significance**
- **Public Health Strategy**: Life expectancy forecasts can shape public health initiatives, focusing on disease prevention, health education, and lifestyle modifications. The insigths gleaned from the model can illuminate the most important factors that affect the quality of life in a nation. With these insights, governments can determine how to optimally allocate resources to the healthcare sector to improve their nations' healthcare quality. Healthcare providers and policymakers can optimize resource distribution, targeting areas that significantly impact life expectancy.
- **Research and Development Drive**: These trends inform where R&D efforts should be concentrated, particularly in pharmaceuticals and medical technology focusing on longevity-impacting conditions.

## Hypothesis

The life expectancy of a population is significantly influenced by a combination of healthcare-related factors (such as HIV prevalence and healthcare funding) and socio-economic conditions. This interplay of factors not only affects the quality of healthcare but also has wide-ranging implications for businesses (especially in the insurance and pension sectors), economic policies, and public health strategies. By accurately modeling and predicting life expectancy, stakeholders across these sectors can make more informed decisions, leading to optimized business strategies, effective policy formulation, and targeted public health initiatives.

## Data Description for "Life Expectancy (WHO)" Dataset

**Source:** [Life Expectancy (WHO) - Kaggle](https://www.kaggle.com/datasets/kumarajarshi/life-expectancy-who/data)

This dataset aggregates various health factors and indicators across countries, compiled by the World Health Organization (WHO). It encompasses a wide array of health-related variables, offering insights into different aspects influencing the life expectancy in various countries.

### Data Dictionary:

1. **Country**: Name of the country.
2. **Year**: Calendar year of the data entry.
3. **Status**: Developed or Developing status of the country.
4. **Life Expectancy**: Life Expectancy in age.
5. **Adult Mortality**: Adult Mortality Rates of both sexes (probability of dying between 15 and 60 years per 1000 population).
6. **Infant Deaths**: Number of Infant Deaths per 1000 population.
7. **Alcohol**: Alcohol, recorded per capita (15+) consumption (in liters of pure alcohol).
8. **Percentage Expenditure**: Expenditure on health as a percentage of Gross Domestic Product (GDP).
9. **Hepatitis B**: Hepatitis B (HepB) immunization coverage among 1-year-olds (%).
10. **Measles**: Number of reported cases per 1000 population.
11. **BMI**: Average Body Mass Index of the entire population.
12. **Under-Five Deaths**: Number of under-five deaths per 1000 population.
13. **Polio**: Polio (Pol3) immunization coverage among 1-year-olds (%).
14. **Total Expenditure**: General government expenditure on health as a percentage of total government expenditure (%).
15. **Diphtheria**: Diphtheria tetanus toxoid and pertussis (DTP3) immunization coverage among 1-year-olds (%).
16. **HIV/AIDS**: Deaths per 1000 live births HIV/AIDS (0-4 years).
17. **GDP**: Gross Domestic Product per capita (in USD).
18. **Population**: Population of the country.
19. **Thinness 1-19 years**: Prevalence of thinness among children and adolescents for Age 10 to 19 (%).
20. **Thinness 5-9 years**: Prevalence of thinness among children for Age 5 to 9(%).
21. **Income Composition of Resources**: Human Development Index in terms of income composition of resources (index ranging from 0 to 1).
22. **Schooling**: Number of years of Schooling(years).

This dataset provides a comprehensive view of the factors affecting life expectancy and can be used for in-depth analysis and modeling to understand the relationships between these variables and life expectancy.

#### Univariate Analysis
![Univariate](https://github.com/Abdul-AA/Life-Expectancy/blob/e4e5c3e60d42c65991291da1b2cef8a81c0273b6/Plots/Univariate.png)
#### Bivariate Analysis
##### Insights
- Developed countries tend to have higher life expectancy, countries with low Diphtheria immunization rates tend to have lower life expectancy, and countries with a high prevalence of thinness among children tend to have lower life expectancy.
- Life expectancy has not changed substantially over the years regardless of development status.
- No strong relationahip between life expectancy and HIV/AIDS prevalence.
- Strong positive relationahip between life expctency vs GDP, percentage of resources allocated to healthcare, BMI. 
- The relationship between BMI and life expectancy can be complex. A healthy BMI (usually considered to be in the range of 18.5 to 24.9) is often associated with better overall health and lower risks of chronic diseases such as heart disease, diabetes, and certain cancers. However, both underweight (BMI less than 18.5) and obesity (BMI over 30) are linked with increased health risks and potentially lower life expectancy.

![Bivariate](https://github.com/Abdul-AA/Life-Expectancy/blob/e4e5c3e60d42c65991291da1b2cef8a81c0273b6/Plots/Bivariate.png)
#### Multivariate Analysis
![Multivariate](https://github.com/Abdul-AA/Life-Expectancy/blob/main/Plots/Multivariate.png)



### Data Preprocessing
Before model building, several steps were conducted to prepare the dataset for modeling:
- The dataset was divided into training and test sets. All model training was done on the training set, while the test set was used solely for evaluation. The original dataframe was also retained for Exploratory Data Analysis (EDA).
- Rows with null values in the target variable were dropped.
- Missing values were filled using KNN imputer, chosen because most missing values carry information distinct to their nature; simply filling them with the median would be counterintuitive.
- The categorical variable 'status' was one-hot encoded.
- Scaling was not applied to the numeric variables because decision tree is robust to feature scale
- 'Year' and 'Country' were dropped from the dataset because, given the use case, we are not interested in temporal patterns. Additionally, using 'Country' as a feature may lead to overly optimistic results due to information leakage, as we are trying to predict a nation's life expectancy based on specific factors.
- All preprocessing steps were first explored individually to assess their impact. They were then incorporated into a pipeline with the model to ensure consistency with the test set.

## Model
Given the goal of this project, parsimony is key. Therefore, I have prioritized simplicity and explainability in selecting the best model. This approach is vital because the aim of the project is not only to predict life expectancy but, more importantly, to understand the factors at play and their influence on life expectancy. 
### Model Approach
A decision tree model was selected. A base model was initially created with a maximum depth of 5. Subsequently, a grid search was conducted to determine the optimal combination of maximum depth, minimum sample leaf, and minimum sample split. The hyperparameter grid was tailored to avoid a complex decision tree—meaning a relatively low maximum tree depth and relatively high maximum sample split and leaf.

### Model Evaluation 
The root mean squared error (RMSE) was the metric I sought to minimize in evaluating and tuning the model. RMSE was chosen because it penalizes larger deviations from actual values. The model's performance on the training set was compared to its average RMSE over 10-fold cross-validation to gauge its generalization capability. Further assessment of generalization was conducted using the test set, which was not involved in the training process.

## Results and Lesson Learned
With RMSEs of 2.68 and 2.85 on the training and test sets respectively, the model demonstrates a good balance between bias and variance. The similar RMSE values on unseen data indicate model generalization. After establishing the model's reliability, key insights include:
- The most important factors affecting life expectancy include the nation's development status, percentage of Diphtheria immunization among one-year-olds, and prevalence of thinness amongst 5-9 year-olds. 


## Interpratability of Results
As mentioned earlier, a simple algorithm was chosen to enhance explainability. More complex, 'black box' algorithms such as ensemble trees might offer better performance but are harder to interprete. To further facilitate the model's interpretability, the decision rules of the model were programmatically extracted, showing the growth and splits at each node of the decision tree. Additionally, the top tree features were visually displayed to show how the tree splits at each node, the number of samples at each node, the squared error at each node, and the average life expectancy of the samples in each node. Examining these values, along with the decision rules, enhances the explainability of the model.


## Threats to Validity

- **Dataset Dependence**: The primary threat to the validity of the results from this model lies in the dataset. Any changes in the dataset could lead to significantly different results, highlighting a known limitation of decision trees. Furthermore, the dataset's timeframe (2000-2014) may not reflect more recent trends or changes.

- **Simplification of Reality**: The dataset may oversimplify the complex reality of factors influencing life expectancy, particularly intangible aspects. While data science projects often contend with this issue, relying on data that does not fully represent reality, the available data is usually representative enough to provide relevant insights.

- **Causality vs. Correlation**: The model is capable of identifying correlations but not causality. It’s important to remember that correlation between variables does not imply one causes the other, which could lead to misinterpretations of the model's findings.

- **Missing Values**: The absence of potentially influential observation that were dropped during preprocessing may have limited the robustness of the model. Also, the missing values that were filled using KNN imputer may have introduced bias into the model. 

These considerations are crucial for a thorough assessment of the model’s limitations and inform future enhancements or interpretations of its outcomes.


## Next Steps

- **Causal Inference Analysis**: Perform causal inference analysis to derive even more actionable and reliable insights. This approach will help in distinguishing between correlation and causation, which is crucial for formulating effective policies and strategies. Some of the inisghts gleaned do not sound logical such as the strong relationship between BMI and life expectancy. A causaul inference would be ideal to do some further probing.

- **Update Dataset**: Develop the model with a more up-to-date dataset. Using recent data will ensure that the model reflects current trends and factors affecting life expectancy.

- **Research on Missing Values**: Conduct research to address the missing values by referring back to the original dataset. Inputting the actual values instead of using an imputer will enhance the robustness and accuracy of the model.

- **Explore Additional Variables**: Investigate additional variables that could improve the model's robustness. These might include environmental factors like air quality indices and healthcare access metrics such as the number of healthcare professionals per capita.

- **Code Optimization**: Optimize the code to prepare it for production. This step involves refining the code for efficiency, readability, and scalability.

- **Model Productionization**: Integrate the model into an appropriate platform for use. This involves ensuring the model can be reliably and efficiently used in a real-world, operational environment.

Implementing these steps will significantly enhance the model's effectiveness and applicability in practical scenarios.
