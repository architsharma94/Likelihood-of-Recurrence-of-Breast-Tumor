# Likelihood-of-Recurrence-of-Breast-Tumor

## PHASE 1

### Repository guide for Phase 1:
* Data => Data - Phase 1.xls
* Analysis, Code and Reporting => Phase 1.ipynb

### Introduction 
In the modern world of medical science, the amalgamation of statistics and technology has tremendously improved our understanding of factors that affect our health. There is a very common proverb championed by the healthcare industry that prevention is better than cure. This notion has driven scientists across the globe to formulate models that can help predict a person's vulnerability to diseases and infections. Foreseeing an individual’s susceptibility to a disease is quite vital for diagnosis and treatment, especially for high risk diseases such as a cancer which may be fatal.

Amongst females in Australia itself, in 2016 the breast cancer was the second most detected type of cancer and in 2018 the second leading reason of fatality by cancer (Welfare, 2020). These figures are a huge concern added on by the gravity of recurring of the breast tumor after the first incidence or remission.

Early warning of the chances of reappearance of breast cancer may give women better fighting chances than detection at later stages of cancer.In order to contribute to this cause of predicting person's vulneribilty to a disease, we have set out to build a model that can predict recurrence of malignancy in an individual, which can help the doctors provide timely and appropriate healthcare services.

### Goals and Objectives 
Recurrence may be traced to some biological factors. Risk of recurrence is said to be high for higher number of lymph nodes while treatment at primary incidence of cancer. Menopause may also increase the risk of breast cancer.(Society, 2010) Through this project, we explore the factors that play a role in the recurrence of breast cancer in a person.

The aim of this project is to build a comprehensive model for predicting the recurrence of breast tumors in females. The objectives defined to achieve the aim are as follows:
* Preprocess data: Handle missing values, outliers, irrelevant columns and other abnormalities to increase efficiency.
* Data exploration: Investigate the relationship between the features and understand their impact through meaningful insights.
* Predictive Modelling: Assess the data and implement a suitable regression technique.
* Diagnostics: Perform statistical diagnostic checks on the model to gauge the accuracy and efficiency of model.

### Conclusion 
Based on the first stage of analysis, it can be said that there are many factors that may influence the reappearance of the breast tumor. The degree of malignancy, receiving of radiation therapy and menopause can have relation to the likelihood of breast tumor reccuring.

In the next stage, we will further inspect the relations between the target variable (recurrence of breast tumor) and its causation. Using appropriate Regression models, we aim to predict the likelihood of a female with a history of breast tumor being diagnosed with it again.

## PHASE 2

### Repository guide for Phase 2:
* Data => Data - Phase 2.csv
* Raw Report (rMarkdown) => Phase 2.R
* Compiled Report => Phase 2 (Code and report compiled).html 

### Introduction
The aim of this project is to predict the recurrence of breast tumor in females based on the malignancy-related information of 286 patients. An early warning or knowing which biological factors may lead to a reappearance of malignancy of breast tumor, can help doctors to provide preventive measures and treatment effectively. Moreover, the patient may have a better fighting chance with early detection. In phase 1, exploratory data analysis was performed, and the data was cleaned. The different relationships between the various biological features were explored.

### Methodology
In this second phase of the analysis, statistical modelling was done over the pre-processed data. A logistic regression model was created to investigate the probability of recurrence of breast tumor. The response variable is binary, and the dataset also contains category explanatory variables and therefore, logistic regression is the method undertaken in this project. The event of recurrence of malignancy is the target variable, with ‘r’ referring to cases showing reappearance and ‘n’ showing no recurrence. 9 features describing the various factors such as irradiation, degree of malignancy the first time, are all used to build the logistic regression model. Significant predictors are found, and the odds of recurrence are compared with the different levels of the same predictor. The analysis is done using R programming language.

### Critique & Limitations
* Size of dataset – The dataset had just over 250 observations. A larger dataset usually helps achieve a more robust predictive model.
* Handling of Categorical Predictors – The predictors were converted to a numerical format for model building and subsequent evaluation. This was done to perform logistic regression. A different approach could have involved splitting the categorical predictors with more than 2 levels for analysis. This approach might help with maintaining the ordinality of features.
* Exhaustive GLMulti Modelling - In this investigation, genetic search with level 1 (only main interactions included) was used for modelling with GLMulti. A different approach could involve introduction of interactions and/or performing an exhaustive search for finding suitable candidate models.
* Precision/Recall - The predictive power of the model could not be tested using accuracy, precision and recall. These additional measures offer a holistic approach towards finding the right model for prediction. A train-test approach can be followed, wherein the model is trained on a train dataset. After performing logistic regression, the candidate models can then be checked for accuracy using the test dataset.

### Summary & Conclusions
A dataset containing medical details of 261 females diagnosed with breast tumor was assessed to build to logistic regression model for predicting the recurrence of the disease. First, the dataset was cleaned and pre-processed to get rid of noise and erroneous values. The resulting data, containing 9 predictors and 1 response, was visualized to understand their impact on one another.

Based on the first stage of analysis, it could be said that there were many factors that may influence the reappearance of the breast tumor. The degree of malignancy, receiving of radiation therapy and menopause can have relation to the likelihood of breast tumor recuring. Below are the key takeaways from the visualization:

The age of majority of the patients at the time of diagnosis ranged from approximately 30 to 75, and most of the breast cancers were diagnosed in the age bracket of 50 to 55.
Approximately 80% of the patients did not opt for radiation therapy, while nearly just 20% of them claimed to have received it.
The average age of patients with tumor size (P) and tumor size (N) is nearly the same. And the distribution of age is wider in case of Tumor size (P) incomparison to Tumor size (N).
For all cases where cancer did metastasized to lymph node from the lower right quadrant of breast,recurrence cases were observed.
In Phase 2, the dataset, which is a mix of count and categorical predictors, was converted to a numeric format for performing logistic regression. A binomial distribution was assumed, hypothesis test for independence was performed. Most of the predictors were found to be independent.

In model building, 3 different approaches were utilized for finding candidate models. Manual, GLmulti and backward alternating stepwise selection were performed to find 3 best models according to the lowest AIC score. The AIC scores from the 3 candidate models are shown below:

* Manual Model – 277.1
* GLMulti – 277.3
* Backward Alternating Stepwise Selection – 264.7

These models were used for prediction, wherein backward alternating stepwise selection returned the best prediction. The Pearson Standardized residual analysis confirmed that the backward alternating model was a decent model, with a few outlier observations.

Next, the Goodness of Fit test was conducted. The GOF measure of Manual model was the closest to 1, followed by GLMulti and Backward Alternating. However, the lowest AIC was observed for Backward Alternating stepwise selection model, along accurate prediction and a GOF measure close to 1. Hence, the model obtained from backward alternating selection was chosen for further analysis.

The chosen model is given by the following equation:

logit(pi) = exp(link)

where, link = 28.58190203(Intercept)-0.97614381age+4.39611159menopause+3.87427235inv.nodes-16.21917957node.caps-7.21163772deg.malig+7.16984349breast-2.08568138breast.quad-3.25972981irradiation+4.75189242tumor.cd+0.11801148age:menopause-0.09208782age:inv.nodes+0.30330935age:node.caps+0.11233463age:deg.malig+0.0456061age:breast.quad+0.07419307age:irradiation+0.08162175age:tumor.cd+1.38291966menopause:inv.nodes-2.91687998menopause:node.caps-1.39768537menopause:deg.malig-0.82966183menopause:breast.quad-2.38844187menopause:tumor.cd-0.53566611inv.nodes:node.caps+4.20295285node.caps:deg.malig-3.43070364node.caps:breast+1.81843696node.caps:breast.quad+2.41369489node.caps:irradiation-4.51367151node.caps:tumor.cd-0.52068158breast:breast.quad-1.95597623breast:irradiation

This model was further used for prediction, calculation of subsequent confidence intervals, and odds ratio.
