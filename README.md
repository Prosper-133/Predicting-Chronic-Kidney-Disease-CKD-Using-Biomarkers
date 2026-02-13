# Predicting Chronic Kidney Disease (CKD) Using Biomarkers 🩺

<img width="624" height="280" alt="image" src="https://github.com/user-attachments/assets/2e85ced3-1919-4d29-9280-ae7822dabef4" />

*Stages of CKD* [shutterstock](https://www.shutterstock.com/image-vector/chronic-kidney-disease-stages-ckd-healthy-2598407695?trackingId=b84416d6-0509-4b69-8144-b5c438db18a2&listId=searchResults)

## Project Overview
Chronic Kidney Disease (CKD) is a global health crisis affecting approximately **850 million people**. It is currently the third fastest-growing cause of death globally. This project focuses on the exploratory data analysis (EDA) of a synthetic dataset containing **1,659 patient records** to understand the diagnostic power of various clinical biomarkers.

The primary goal is to analyze the relationship between clinical measurements like **GFR**, **BUN**, and **Proteinuria** to see how effectively they signal kidney impairment, even in the early, asymptomatic stages.

## Dataset Description
The analysis uses a synthetic dataset from Kaggle, which includes 54 features covering:
- **Demographics:** Age, Gender, Ethnicity, and Socio-economic status.
- **Clinical Biomarkers:** GFR (Glomerular Filtration Rate), BUN (Blood Urea Nitrogen), Serum Creatinine.
- **Lifestyle & Environment:** Diet, Smoking, Water Quality, and Heavy Metals Exposure.
- **Medical History:** Presence of Diabetes, Hypertension, and family history of kidney failure.


## Key Exploratory Data Analysis (EDA) Insights

### 1. The GFR Paradox
The analysis revealed that while a **GFR of 90+** is typically considered "normal," several patients in this category were still diagnosed with CKD.

<img width="860" height="549" alt="GFR_1" src="https://github.com/user-attachments/assets/a69ab8a1-0071-42f1-91d7-bfd2a71cbaba" />

* **Insight:** Diagnosis in these cases is driven by **Proteinuria** (protein in the urine). This highlights that structural damage (leaking filters) often precedes the actual drop in filtration volume.

<img width="893" height="549" alt="Normal Gfr" src="https://github.com/user-attachments/assets/38a84b09-07fa-4ae9-bb0b-4c1aa3df3663" />

### 2. Biomarker Distributions
- **Mean GFR:** ~70.3 mL/min/1.73m² (indicating a population mostly in Stage 2 CKD).
- **Mean BUN:** ~20.1 mg/dL.
- **Mean Proteinuria:** ~2.5 g/day.
- **Observation:** The dataset is perfectly clean with **zero missing values**, making it ideal for testing diagnostic workflows.

### 3. The "Healthy" Outlier
A unique discovery in the data was **exactly one patient** who presented with entirely normal biomarkers (Normal GFR, Normal BUN, and no Proteinuria) yet was still diagnosed with CKD. This serves as a critical reminder that while biomarkers are essential, comprehensive medical screening must account for outliers and external risk factors.

<img width="911" height="549" alt="Normal Protein" src="https://github.com/user-attachments/assets/de5f6350-3c8b-4f0c-9f05-61680cb76a08" />


### **Outlier Profile: The "Healthy" CKD Patient**

| Feature | Value | Clinical Interpretation |
| :--- | :--- | :--- |
| **Glomerular Filtration Rate (GFR)** | **90+ (Normal)** | The kidneys are filtering blood at a healthy volume. |
| **Blood Urea Nitrogen (BUN)** | **Normal** | No toxic buildup of metabolic waste in the bloodstream. |
| **Protein in Urine** | **Normal** | No signs of structural "leaking" in the kidney's filters. |
| **Family History of Diabetes** | **Yes** | **Critical Risk Factor**; Genetics often predispose individuals to renal stress before it shows in labs. |
| **Alcohol Consumption** | **18.94 Units** | **High**; Significant intake causes chronic dehydration and renal strain. |
| **Water Quality** | **0 (Poor)** | Potential exposure to environmental toxins or heavy metals. |
| **Diagnosis** | **CKD Positive** | **Confirmed**; Identified through risk factors rather than current lab failure. |

### 4. Correlation Analysis
As this is a synthetic dataset, the statistical correlation between lifestyle factors (like Water Quality or Medication Adherence) and clinical markers was found to be low. However, the **analytical workflow**
established remains robust for application on real-world medical data.

## Clinical Background: Why These Markers Matter
- **Proteinuria:** Acts as a "driver" of the disease. Leaking protein is nephrotoxic, causing tubulointerstitial inflammation and permanent scarring (fibrosis).
- **BUN:** An "indicator" of waste buildup. High levels signal that the kidney can no longer effectively clear metabolic byproducts.
- **ACE Inhibitors:** The project references how these medications are used to lower internal kidney pressure and slow the progression of scarring.

## How to Use This Repository
1. **Clone the repo:** `git clone https://github.com/your-username/ckd-analysis.git`
2. **Install Dependencies:** `pip install pandas seaborn matplotlib`
3. **Run the Notebook:** Open `EDA_ckd.ipynb` to view the full visualization and correlation matrices.

## Conclusions
This project demonstrates that CKD is not a one-size-fits-all condition. By focusing on the interplay between GFR and Proteinuria, we can identify high-risk patients even when their primary lab results appear stable. This methodology is vital for moving from reactive treatment to proactive prevention.

---
*Note: This project was created for educational purposes using a synthetic dataset.* 
