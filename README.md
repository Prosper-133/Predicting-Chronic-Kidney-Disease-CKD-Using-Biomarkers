## 🩺 Understanding Biomarkers and Risk Factors for Chronic Kidney Disease (CKD) Prevention

<img width="337" height="149" alt="Kidney" src="https://github.com/user-attachments/assets/e335bafb-711e-4d71-8179-c4412cc9f0b4" />


*Image Credit: [Shutterstock*](https://www.shutterstock.com/image-vector/chronic-kidney-disease-stages-ckd-healthy-2598407695?trackingId=b84416d6-0509-4b69-8144-b5c438db18a2&listId=searchResults)

---

## 🌍 Global Context & Project Aim

Chronic Kidney Disease (CKD) is a critical and mounting global health crisis, currently affecting approximately **850 million people** worldwide. Its impact is characterized by staggering epidemiological trends:

* **Mortality Trend:** It is currently the **3rd fastest-growing** cause of death globally.


* **Future Projections:** By 2040, CKD is projected to become the **5th leading cause** of years of life lost (YLL) globally.


* **The "Silent" Disease:** In resource-limited settings, up to **90% of individuals** remain completely unaware of their condition until it reaches advanced, symptomatic stages.



The primary goal of this project is to perform an exploratory data analysis (EDA) using `EDA_ckd_transformed.ipynb` to evaluate the dynamic effectiveness of various physiological biomarkers and environmental/lifestyle risk factors in screening, monitoring, and diagnosing CKD.

---

## 📊 Dataset & Advanced Transformation Pipeline

This study utilizes a health record dataset consisting of **1,659 patients**.

> 📝 **Data Integrity Note:** This is a synthetic dataset generated for educational and analytical workflow testing purposes. While variables closely mirror real-world parameters, the data has been cleanly optimized for evaluation workflows, categorical mappings, and advanced statistical visualizations.
> 
> 

### 🛠️ Excel & Power Query Data Transformations

To build a more readable, context-driven clinical narrative, the raw data underwent structured transformations in **Excel** and **Power Query** prior to its notebook exploration:

* **Nominal Categorical Mapping:** Originally encoded numeric or binary categorical variables were mapped into descriptive, nominal categories (e.g., transforming binary values into descriptive strings) to tell a clearer story with the data.
* **Missing Value Imputation:** During notebook validation, an anomaly of **180 missing values** was detected under `EducationLevel`. Cross-referencing revealed these represented individuals with no formal schooling. The entries were explicitly cleaned and handled by filling the missing records with the descriptive nominal string `"No Formal Education"`.



---

## 🧬 Diagnostic Benchmark Summary: All 5 Biomarkers

Modern renal diagnostics rely on distinguishing between **functional biomarkers** (tracking current filtration efficiency) and **structural indicators** (revealing cellular or microvascular damage).

In `EDA_ckd_transformed.ipynb`, we evaluate the five foundational biomarkers across the entire cohort:

1. **Serum Creatinine:** A byproduct of muscle metabolism used to compute total GFR; elevated blood levels signal compromised filtration.


2. **Urine Albumin-to-Creatinine Ratio (ACR):** The gold standard for structural damage; tracking "leaky" protein barriers.


3. **Proteinuria (Urine Protein):** A broader indicator of glomerular and tubulointerstitial injury.


4. **Glomerular Filtration Rate (GFR):** The overall indicator of functional filtration volume per minute.


5. **Blood Urea Nitrogen (BUN):** Measures metabolic urea waste clearance in the bloodstream.



The performance models generated below showcase the individual accuracy and collective diagnostic strength of these markers:

### 📊 Performance Summary: Diagnostic Accuracies vs. Mismatches

<img width="1589" height="593" alt="Performance Summary" src="https://github.com/user-attachments/assets/256a1705-9c20-40e1-9ed3-a31c570f9d37" />


The plot highlights how accurately each biomarker stands independently against the confirmed diagnostic state, alongside their unique misclassification profiles (False Alarms vs. Silent Cases):

* **Serum Creatinine** offers the highest individual diagnostic accuracy at **83.5%**, showing only 73 false alarms but leaving 200 cases silent.
* **BUN Levels** hold the lowest isolated accuracy at **67.0%**, significantly prone to missing diagnoses with **479 silent cases**.
* **Structural indicators (ACR & ProteinInUrine)** maintain robust performance profiles (**82.4%** and **77.5%** respectively), demonstrating their critical role in catching underlying tissue pathology early.

---

## 🔍 The Multi-Stage Screening Cascade

Because individual biomarkers are prone to distinct error profiles, clinical screening rarely relies on a single metric. The waterfall sequence below tracks how a positive cohort of **1,524 patients** is filtered across consecutive biomarker tests, highlighting how structural and functional tests catch different overlapping populations until every single case is accounted for:

### 📉 Step-by-Step Diagnostic Elimination

| Step | Patients Remaining | Patients Caught | Diagnostic Context |
| --- | --- | --- | --- |
| **0. Initial Positive Population** | **1,524** | **0** | Starting group of verified positive diagnoses. |
| **1. Filter: GFR** | **387** | **1,137** | Volumetric filtration captures the primary bulk of active kidney degradation. |
| **2. Filter: ACR** | **40** | **347** | Micro-albuminuria damage filters catch an additional wave of silent cases where filtration volume seemed normal. |
| **3. Filter: Serum Creatinine** | **3** | **37** | Metabolic muscle byproducts resolve nearly all remaining baseline oversights. |
| **4. Filter: BUNLevels** | **1** | **2** | Blood urea clearance isolates the true hidden outlier population. |
| **5. Filter: ProteinInUrine** | **0** | **1** | The final macro-protein filter resolves the final remaining case. |

---

## ⚠️ Environmental & Lifestyle Risk Profiles

<img width="1590" height="691" alt="RFP Profiles" src="https://github.com/user-attachments/assets/6e10f337-7d13-4e2a-a932-cbf00fe8480b" />


Beyond clinical labs, macro-environmental factors and lifestyle choices directly modulate renal microvascular stress. The twin-panel visualization maps out the distinct prevalence rates of risk components between active CKD patients and healthy control populations:

* **Genetic Pre-disposition:** Family histories of Hypertension (**30.4%**) and Diabetes (**25.9%**) score significantly higher among active CKD patient profiles than healthy populations, functioning as core risk multipliers.
* **Environmental Pressures:** Poor water quality and chemical/heavy metal tracking consistently correlate with elevated disease tracking, serving as a reminder that structural tissue protection requires strict systemic and environmental mitigation.

---

## 🚀 How to Use This Repository

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/ckd-analysis.git
cd ckd-analysis

```

### 2. Set Up Your Environment

Ensure you have the required open-source data science tools installed:

```bash
pip install pandas seaborn matplotlib openpyxl

```

### 3. Run the Analysis Workspace

Open your local editor or terminal to interact with the transformed notebook:

```bash
jupyter notebook EDA_ckd_transformed.ipynb

```
