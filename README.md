# **Prediction of Metabolic Syndrome Using Machine Learning**

- Yvon Bilodeau
- April 2022

---

## **Project Description**

### **Goal**

The goal of this project is to predict the presence of metabolic syndrome, positive or negative, based on common risk factors utilizing categorical machine learning.

### **Metabolic Syndrome Diagnosis**

The National Institutes of Health guidelines define metabolic syndrome as 
"a group of conditions that together raise your risk of coronary heart disease, diabetes, stroke, and other serious health problems. Metabolic syndrome is also called insulin resistance syndrome"

 - Source - [The National Institutes of Health](https://www.nhlbi.nih.gov/health/metabolic-syndrome#:~:text=Metabolic%20syndrome%20is%20a%20group,more%20of%20the%20following%20conditions.)

Metabolic syndrome is increasingly common, and up to one-third of U.S. adults have it. If you have metabolic syndrome or any of its components, aggressive lifestyle changes can delay or even prevent the development of serious health problems."

 - Source - [Mayo Clinic](https://www.mayoclinic.org/diseases-conditions/metabolic-syndrome/symptoms-causes/syc-20351916?utm_source=Google&utm_medium=abstract&utm_content=Metabolic-syndrome&utm_campaign=Knowledge-panel)

### **Dataset**

The dataset was aquired from [Data World](https://data.world/informatics-edu/metabolic-syndrome-prediction). They aquired the data for this analysis from the [NHANES](https://www.cdc.gov/nchs/nhanes/index.htm), National Health and Nutrition Examination initiative, in which several features were combined from multiple tables.

The dataset consists of 2401 rows, and 15 columns.The rows represent 2401 observations, and the columns represent 14 features and 1 target variable.

| Feature         | Description  |
| --------------  | ------------ | 
| seqn            | Respondent sequence number | 
| Age             | Age in Years | 
| Sex             | Male or Female | 
| Marital         | Marital status | 
| Income          | Income in Dollars | 
| Race            | Racial Group | 
| WaistCirc       | Waist Circumference (cm)| 
| BMI             | Body Mass Index (kg/m**2) | 
| Albuminuria     | Albumin in Urine (mg/L)) | 
| UrAlbCr         | Ratio of Albumin (mcg/L) to Creatinine (mg/L) in Urine | 
| UricAcid        | Uric Acid in Blood (mg/dl) | 
| BloodGlucose    | Glucose in Blood (mg/dL) | 
| HDL             | High Density Lipoprotein (mg/dl) | 
| Triglycerides   | Triglycerides in Blood (mg/dL) | 
| MetabolicSyndrome | Presence or not of at least three of the five metabolic risk factors | 

"The National Institutes of Health guidelines define metabolic syndrome as having three or more of the following traits, including traits for which you may be taking medication to control:

- **Large waist** — A waistline that measures at least 35 inches (89 centimeters) for women and 40 inches (102 centimeters) for men
- **High triglyceride level** — 150 milligrams per deciliter (mg/dL), or 1.7 millimoles per liter (mmol/L), or higher of this type of fat found in blood
- **Reduced "good" or HDL cholesterol** — Less than 40 mg/dL (1.04 mmol/L) in men or less than 50 mg/dL (1.3 mmol/L) in women of high-density lipoprotein (HDL) cholesterol
- **Increased blood pressure** — 130/85 millimeters of mercury (mm Hg) or higher
- **Elevated fasting blood sugar** — 100 mg/dL (5.6 mmol/L) or higher"

"Having just one of these conditions doesn't mean you have metabolic syndrome. But it does mean you have a greater risk of serious disease. And if you develop more of these conditions, your risk of complications, such as type 2 diabetes and heart disease, rises even higher.

<img src = "https://github.com/YBilodeau/Metabolic-Syndrome-Prediction-Project/blob/main/Images/WaistCirc%20and%20Age.png">

<img src = "https://github.com/YBilodeau/Metabolic-Syndrome-Prediction-Project/blob/main/Images/Triglycerides%20and%20Age.png">

<img src = "https://github.com/YBilodeau/Metabolic-Syndrome-Prediction-Project/blob/main/Images/BloodGlucose%20and%20Age.png">

<img src = "https://github.com/YBilodeau/Metabolic-Syndrome-Prediction-Project/blob/main/Images/HDL%20and%20Age.png">

## **Model Evaluation**
### **Error Types** 
 In every binary classification problem we select one class to be the 'positive' class and one to be the 'negative' class. The positive class should be the one you are most interested in finding. For our Metabolic Syndrome dataset the positive class will be the presence of metabolic syndrome and the negative class will be the absence of metabolic syndrome.

**Type 1 error:**
If our model predicts that there is the presence of metabolic syndrome, but it in fact there is an absence of metabolic syndrome, it will have made a type 1 error.  This is also known as a false positive.

**Type 2 error:**
If our model predicts that there is an absence of metabolic syndrome, when there is the presence of metabolic syndrome, it will have made a type 2 error.  This is is also known as a false negative.

### **Scores**
#### **Accuracy Scores**
Accuracy is the metric that is most intuitive.  

This is defined as:

<img src="https://render.githubusercontent.com/render/math?math=recall = \frac{True Positives + True Negatives}{All Samples}">

In other words accuracy is correct predictions our model made out of the total number of predictions.

**Pros:**
Accuracy is easy to understand and gives a combined picture of both kinds of errors in one number.

**Cons:**
Accuracy can be deceiving when a dataset is unbalanced.  It also does not give specific information about the kinds of errors that a model is making.

For example, we saw above that 34% of the instances in this dataset were positive. If our dataset were even more imbalanced, say 99.9% positive, then a prediction that EVERYTHING is positive would have a very high accuracy.  However, that would not be a very useful model for actual medical use.  More often we see the opposite: a disease is very rare, occurring .01% of the time or less, and a model that predicts that NO samples ever have the disease will have a high accuracy, but will actually be useless...and dangerous!

<img src="https://github.com/YBilodeau/Metabolic-Syndrome-Prediction-Project/blob/main/Images/Accuracy%20Scores.png">

#### **Recall Scores**
When we want to reduce the number of false negatives, we want to improve recall. 

Recall is defined as: 

<img src="https://render.githubusercontent.com/render/math?math=recall = \frac{True Positives}{False Negatives + True Positives}">

That is to say: how many samples did our model label as positive out of all of the true positive samples?

Pros: A higher recall means a fewer false negative predictions, also known as type 2 errors.  It's great for when classifying a positive as a negative is a costly mistake.

Cons: Does not consider how many samples are falsely labeled as positive, or false positives.  It does not penalize type 1 errors.

In the case of this dataset, we might assume that the consequence for a false negative is that a person is less likely to make healthy lifestyle changes in order to take steps to lower the risk of heart disease and or to prevent type 2 diabetes, while the consequence for a false positive may be stress, but also an increased likelihood healthy lifestyle changes.

<img src="https://github.com/YBilodeau/Metabolic-Syndrome-Prediction-Project/blob/main/Images/Recall%20Scores.png">

#### **Precision Scores**
When we want to reduce the number of false positives, we want to improve precision.

Precision is defined as:

**<img src="https://render.githubusercontent.com/render/math?math=precision = \frac{True Positives}{False Positives + True Positives}">**

In other words: What ratio of the samples that we predicted were in the positive class were actually in the positive class?

**Pros:**  A high precision means fewer type 1 errors, or fewer false positives.  This is a good metric to maximize if a false positive prediction is a costly mistake.

**Cons:** Precision does not penalize a model for false negatives.  It does not count type 2 errors.

In this case precision would be measuring how many of the patients were diagnosed with metabolic syndrome were actually at risk of heart disease and or type 2 diabetes.

<img src="https://github.com/YBilodeau/Metabolic-Syndrome-Prediction-Project/blob/main/Images/Precision%20Scores.png">

## **Model Comparison Summary and Conclusion**

| Model | Accuracy Score | Recall | Precision | F1 Macro Average | F1 Weighted Average |
| ----------- | ----------- | ----------- | ----------- | ----------- |
| KNN | 0.8120 | 0.5874 | .8121 | 0.77 | 0.80 |
| Logistics Regression - L1 | 0.8353 | 0.6796 | .8092 | 0.81 | 0.83 |
| Logistics Regression - L2 | 0.8353 | 0.6650 | .8204 | 0.81  | 0.83 |
| Random Forest | 0.8835 | 0.7767 | .8696 | 0.87 | 0.88 |


### **Recommended Model**
**The Random Forest Model** is reccomended due to having the highest Accuracy, Recall, and Precision Scores, as well as the highest F1 Macro and F1 Weighted Averages.

Accurate prediction can lead to early diagnosis and treatment. Inaccurate prediction can delay diagnosis and treatment.

### **Benefit of Early Diagnosis and Treatment**
"The main goals of treating metabolic syndrome are to lower your risk of heart disease and to prevent type 2 diabetes if it hasn’t already developed. If you already have type 2 diabetes, treatment can lower your risk of heart disease by controlling all your risk factors.

Heart-healthy lifestyle changes are the first line of treatment for metabolic syndrome. You may have to see a dietitian and a physical therapist to help find a diet and exercise plan that works for you. If healthy lifestyle changes do not work, you may need medicines or weight loss surgery."
- Source - [The Mayo Clinic](https://www.nhlbi.nih.gov/health/metabolic-syndrome/treatment)
