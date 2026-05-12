# diabetes-analysis-bmi-waist-hba1c
Multiple linear recession using Python to examine a hypothesis that waist circumference is associated more strongly than BMI with increased insulin resistance, resulting in poor glycaemic control in type 2 diabetes.

# 0. Introduction
## Clinical question
##Which is more strongly associated with poor glycaemic control of type 2 diabetes, BMI or waist circumfence?

## Background
It is widely known that type2 diabetes is primarily caused by increased insulin resitance, which is mainly attributed to excess body fat, particularly when it is stored as visceral fat, while other factors such as genetics, ages, diets and muscle volume, may play roles.


From my early clinical experience, I have seen a lot of cases of type 2 diabetes where the focus of treatment goal aside from controling HbA1c is reducing patients' weights,  rather than waist circumfences, aiming for a normal BMI.


Moreover, there has been a both clinically and epidemiologically controversial assumption that BMI is a quick marker for general metabolic signals.

As waist circumfence tend to reflect visceral more directly than BMI, which is a reflection of overall body mass, I tried to examine a hypothesis through this analysis, that waist circumfence could be associated more strongly with increased insulin resistance, resulting in poor glycaemic control in type 2 diabetes.

# 1. Data Selection
## 1-1. diabetes type (type1 vs type2)
I excluded patients data with type1 diabetes, as the clinical question mentioned above is purely about the relationships between common obesity indexes and insulin resistance, while type1 diabetes also involves other mechanism than insulin resistance, which is autoimmune condition.

## 1-2. index for glycaemic control (HbA1c vs 'glucose')

### HbA1c was used as the primary marker of long-term glycaemic control in this analysis for the following reasons;

* In general, HbA1c reflects long-term blood glucose level, less affected by day-to-day variation, and therefore used clinically for long-term diabetes control. While it can be affected by other factors such as red blood cell lifespan or renal disease, it is still reliable on population-level.

* In general, blood glucose is prone to high variability, strongly affected by fasting or non-fasting
* In this database, the 'glucose' variable is the only marker of glycaemic status available; however, the timing and type of measurement (fasting, random, post-prandial, or even a simulated mixture of all) is not specified, while each of them could have a clinically different meaning for 'glycaemic control'.

## 1-3 note: what each column refers to
t2d_grs: a genetic risk score for type 2 diabetes. mi_date:myocardial infarction date. Tdi:Townsend deprivation inde packyears: the amount of cigarette per week, multiplied by years of smoking

# 2. Statistical Method
Conducted multiple linear recession using Python, including covariables which may work as cofounding (such as gender, age, LDL cholesterol, etc)
For further details, please refer to metabolic_data.ipynb

# 3. Result
The coefficient of the independent variable 'bmi' on the dependent variable 'hba1c' is by far the largest among other variables, including 'waist_circ'

# 4. Discussion
The result gained from this analysis contradicts the shifting clinical consensus that waist circumference is much more essential predictor of increased insulin resistance over BMI.
Here are the main three possible limitations behind this result that are unique to this particular analysis;

1. Given that the dataset is simulated, relationships are artificially generated, or variable dependencies may be just arbitrary. For example, an intentional data        generation such as assigning stronger metabolic signals (including HbA1c and LDL)to BMI rather than waist circumfence, or, constructing HbA1c directly based on BMI, is possible, making BMI look more associated with HbA1c in disguise over waist circumference.

2. 'bmi' and 'waist_circ' variables have a moderate correlation in this model(corr = 0.6), which makes each coefficient unstable.

3. While 'waist_circ' also has a moderate correlation with 'sex_binary' (corr=0.61) in this dataset, 'bmi' is less overlapped with other variables, leaving more unique signal(coefficient) in this model,especially if BMI is strongly embedded in HbA1c data generation as mentioned above.

# 5. Conclusion
In this particular dataset and model, BMI appears to have stronger statistical association with poor glycaemic control of type2 diabetes over waist circumference, which contradicts the shifting clinical consensus.
However, the nature of simulated dataset does not guarantee biological realism.
Therefore, the hypothesis of waist circmference as a sharper indicator of increased insulin resistance cannot be verified from the given dataset.




