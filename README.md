# **Prediction of Metabolic Syndrome Using Machine Learning**

- Yvon Bilodeau
- April 2022

---

## **Project Description**

### **Goal**

The goal of this project is to predict the presence of metabolic syndrome, yes or no, based on common risk factors utilizing categorical machine learning.

### **Metabolic Syndrome Diagnosis**

The National Institutes of Health guidelines define metabolic syndrome as 
"a group of conditions that together raise your risk of coronary heart disease, diabetes, stroke, and other serious health problems. Metabolic syndrome is also called insulin resistance syndrome"

 - Source - [The National Institutes of Health](https://www.nhlbi.nih.gov/health/metabolic-syndrome#:~:text=Metabolic%20syndrome%20is%20a%20group,more%20of%20the%20following%20conditions.)

"The National Institutes of Health guidelines define metabolic syndrome as having three or more of the following traits, including traits for which you may be taking medication to control:

- **Large waist** — A waistline that measures at least 35 inches (89 centimeters) for women and 40 inches (102 centimeters) for men
- **High triglyceride level** — 150 milligrams per deciliter (mg/dL), or 1.7 millimoles per liter (mmol/L), or higher of this type of fat found in blood
- **Reduced "good" or HDL cholesterol** — Less than 40 mg/dL (1.04 mmol/L) in men or less than 50 mg/dL (1.3 mmol/L) in women of high-density lipoprotein (HDL) cholesterol
- **Increased blood pressure** — 130/85 millimeters of mercury (mm Hg) or higher
- **Elevated fasting blood sugar** — 100 mg/dL (5.6 mmol/L) or higher"

"Having just one of these conditions doesn't mean you have metabolic syndrome. But it does mean you have a greater risk of serious disease. And if you develop more of these conditions, your risk of complications, such as type 2 diabetes and heart disease, rises even higher.


Metabolic syndrome is increasingly common, and up to one-third of U.S. adults have it. If you have metabolic syndrome or any of its components, aggressive lifestyle changes can delay or even prevent the development of serious health problems."

 - Source - [Mayo Clinic](https://www.mayoclinic.org/diseases-conditions/metabolic-syndrome/symptoms-causes/syc-20351916?utm_source=Google&utm_medium=abstract&utm_content=Metabolic-syndrome&utm_campaign=Knowledge-panel)

### **Source of data**

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

## **Model Comparison Summary and Conclusion**

| Model | Train Accuracy Score | Test Accuracy Score | F1 Macro Average | F1 Weighted Average |
| ----------- | ----------- | ----------- | ----------- | ----------- |
| Baseline | 0.6578 | 0.6572 | .40 | .52 |
| Logistics Regression - L1 | 0.8528 | 0.8353 | .81 | .83 |
| Logistics Regression - L2 | 0.8388 | 0.8353 | .81 | .83  |
| Random Forest | 1.000 | 0.8835 | .87 | .88  |
| KNN | 0.8506 | 0.8120 | .77 | .80 |
