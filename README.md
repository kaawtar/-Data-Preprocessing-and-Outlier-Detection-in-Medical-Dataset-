# Data Preprocessing and Outlier Detection in Medical Dataset
This project focuses on cleaning and preprocessing a medical dataset to ensure data quality before applying machine learning techniques. The main objectives are handling missing values, testing data normality, detecting and interpreting outliers, and preparing the dataset for future modeling in healthcare applications.  
## 📊 Dataset  

The dataset used comes from **KAGGLE** (Pima Indians Diabetes Database).  
It contains clinical features such as Glucose, Blood Pressure, Insulin, BMI, Age, etc., with the target variable `Outcome` (0 = non-diabetic, 1 = diabetic).  

Key challenges of the dataset include missing values, skewed distributions, and potential biological/clinical outliers.
## 🔄 Project Workflow  

1. **Exploratory Data Analysis (EDA)** – Understanding variable distributions and relationships.  
2. **Missing Value Imputation** – Using statistical and biological reasoning to fill missing data.  
3. **Normality Testing** – Applying Shapiro-Wilk, Kolmogorov-Smirnov, and visualizations (histograms, QQ plots).  
4. **Outlier Detection** – Using multiple methods:  
   - IQR  
   - Z-Score  
   - Isolation Forest  
   - Local Outlier Factor (LOF)  
   - DBSCAN  
5. **Interpretation** – Linking detected outliers to biological plausibility (e.g., extreme glucose or insulin levels).  
6. **Final Clean Dataset** – Ready for machine learning applications.  
## 🛠️ Technologies Used  

- **Python** (Pandas, NumPy, Scikit-learn)  
- **Matplotlib & Seaborn** (visualization)  
- **SciPy** (statistical testing)  
- **Scikit-learn** (Isolation Forest, LOF)  
## ✅ Results  

- Missing values were successfully imputed using a strategy combining KNN and biological reasoning.  
- Normality testing confirmed that most variables deviate from Gaussian distribution → requiring robust methods.  
- Outlier detection identified biologically implausible values (e.g., glucose = 0, insulin = 846) that were flagged for removal.  
- A **clean, standardized dataset** is now available for machine learning.  
## Interprétation biologique
L’analyse a révélé plusieurs observations extrêmes sur certaines variables cliniques. Ces valeurs atypiques peuvent s’expliquer par des phénomènes physiopathologiques réels ou par des erreurs de mesure :

Glucose : des valeurs très élevées (≥180 mg/dL, jusqu’à 199 mg/dL) correspondent à une hyperglycémie sévère, souvent observée chez des patients diabétiques mal contrôlés ou en situation de stress métabolique. Elles sont cohérentes biologiquement, mais doivent être surveillées car elles influencent fortement les modèles.

Insulin : certaines valeurs dépassent 500–700 µU/mL (ex. 744 µU/mL), ce qui est très au-dessus de la normale (2–25 µU/mL à jeun). Cela peut refléter une hyperinsulinémie extrême, liée à une résistance insulinique marquée, mais il est aussi possible que ce soit des erreurs de saisie ou d’unités.

Blood Pressure : des valeurs comme 110 mmHg de diastolique (ligne 177) sont biologiquement rares et traduisent une hypertension sévère ou une erreur de mesure.

SkinThickness : certaines valeurs très élevées (≥60 mm) ou très faibles (~13 mm) sont inhabituelles et peuvent refléter une mauvaise standardisation de la mesure du pli cutané.

BMI : des valeurs >55 (ex. 59.4) indiquent une obésité morbide, cliniquement plausible mais très rare dans la population générale.

Diabetes Pedigree Function (DPF) : des valeurs >2 (ex. 2.4) reflètent un risque familial extrêmement élevé, mais ces cas restent minoritaires.

Âge : la présence d’outliers d’âge (ex. 81 ans ligne 459) est biologiquement plausible, mais ces individus doivent être interprétés avec prudence car ils diffèrent fortement du reste de la population (majoritairement plus jeune).

👉 En résumé, certains outliers représentent probablement des patients à haut risque ou avec des pathologies sévères, tandis que d’autres (ex. insuline >700 ou tension diastolique >100) pourraient être des artefacts de mesure. Il est donc nécessaire de distinguer les valeurs biologiquement plausibles des erreurs probables avant de décider de leur suppression ou conservation
