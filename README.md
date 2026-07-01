## 🩺 Understanding Biomarkers and Risk Factors for Chronic Kidney Disease (CKD) Prevention

<img width="337" height="149" alt="Kidney" src="https://github.com/user-attachments/assets/e335bafb-711e-4d71-8179-c4412cc9f0b4" />


*Stages of CKD* [shutterstock](https://www.shutterstock.com/image-vector/chronic-kidney-disease-stages-ckd-healthy-2598407695?trackingId=b84416d6-0509-4b69-8144-b5c438db18a2&listId=searchResults)

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

[Raw Data](https://github.com/Prosper-133/Understanding-Biomakers-for-Chronic-Kidney-Disease-CKD-prevention/blob/main/Chronic_Kidney_Dsease_data.csv)

> 📝 **Data Integrity Note:** This is a synthetic dataset generated for educational and analytical workflow testing purposes. While variables closely mirror real-world parameters, the data has been cleanly optimized for evaluation workflows, categorical mappings, and advanced statistical visualizations.
> 
> 

### 🛠️ Excel & Power Query Data Transformations

[Transformed Data](https://github.com/Prosper-133/Understanding-Biomakers-for-Chronic-Kidney-Disease-CKD-prevention/blob/main/CKD%20Transformed%20Data.xlsx)

To build a more readable, context-driven clinical narrative, the raw data underwent structured transformations in **Excel** and **Power Query** prior to its notebook exploration:

* **Nominal Categorical Mapping:** Originally encoded numeric or binary categorical variables were mapped into descriptive, nominal categories (e.g., transforming binary values into descriptive strings) to tell a clearer story with the data.
  
* **Missing Value Imputation:** During notebook validation, an anomaly of **180 missing values** was detected under `EducationLevel`. Cross-referencing revealed these represented individuals with no formal schooling. The entries were explicitly cleaned and handled by filling the missing records with the descriptive nominal string `"No Formal Education"`.



---

## 🧬 Diagnostic Benchmark: All 5 Biomarkers

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


#### Biomarker Performance Summary Insights

The comparative analysis reveals distinct trade-offs in diagnostic performance across the five assessed biomarkers, confirming that no single test is entirely flawless on its own.

* **The Pathophysiological Driver:** It is vital to ground these statistical metrics in clinical reality: **structural or functional damage to the kidney is what ultimately determines the level of each biomarker.** 

**Functional decline** represents an impairment in the kidney's dynamic operations—its ability to filter blood and clear metabolic waste. This physiological slowdown is what drives the blood-based markers, causing a plummeting **GFR** and a sharp rise in **Serum Creatinine** and **BUN Levels**.

**Structural damage**, conversely, represents a physical, anatomical breakdown of the renal tissue itself, such as glomerular tearing or interstitial scarring (fibrosis). This anatomical injury compromises the physical filtration barriers, allowing large molecules to slip through, which directly echoes in urine-based markers like **ProteinInUrine** and **ACR**.




* **Top Performance:** Biomarkers with the highest **Overall Accuracy** serve as excellent first-line screening tools because their numerical shifts tightly correlate with these objective tissue injuries, consistently mapping to the true diagnosis while maintaining a low rate of misclassifications.

* **The Clinical Trade-Off (False Alarms vs. Silent Cases):** The right-hand analysis highlights a critical clinical balance. Markers exhibiting high **False Positives (False Alarms)** tend to over-diagnose healthy individuals, which can cause unnecessary clinical anxiety and lead to costly follow-up testing. Conversely, markers with high **False Negatives (Silent Cases)** pose a much greater clinical risk; they fail to flag patients who genuinely have Chronic Kidney Disease, allowing early-stage structural micro-tears and functional decline to progress completely undetected.

#### How They Intersect
In chronic conditions like CKD, structural damage drives functional decline. For example, long-term high blood pressure physically tears the delicate structural walls of the glomerulus (structural damage). Because the barrier is damaged, proteins leak through (ACR rises), and eventually, that specific filtering unit scars over and dies. As thousands of these units die off, the global filtration speed of the kidney drops (functional damage, causing GFR to plummet).

Understanding this sequence is precisely why clinical screening requires both blood tests (for function) and urine tests (for structure) to get a true picture of kidney health.

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

### Risk Factor Prevalence Insights

#### 1. The Strongest Correlates (The Real Culprits)

The risk factors showing the widest percentage gaps between the two populations represent the strongest associations with a CKD diagnosis:

* **Family History of Kidney Disease:** This factor shows the most dramatic relative inflation. It is nearly **twice as common** in the CKD population ($14.6\%$) compared to the healthy control group ($8.1\%$). This strongly highlights genetic or hereditary predispositions within the dataset.
* **Urinary Tract Infections (UTIs):** Present in $21.5\%$ of CKD patients but only $16.3\%$ of healthy controls. This aligns well with clinical expectations, as recurrent or severe upper UTIs (pyelonephritis) can cause structural renal scarring over time.

#### 2. High Prevalence, Low Contrast (The Baselines)

Some risk factors have very high percentages, but because they are equally common in healthy people, they lack strong diagnostic or predictive power on their own:

* **Family History of Hypertension ($30.4\%$ vs. $26.7\%$) & Smoking ($29.7\%$ vs. $25.2\%$):** While these are the most frequently occurring traits among the sick patients, they are also highly prevalent in the healthy group. They represent widespread baseline behaviors or traits rather than exclusive triggers for CKD within this population.

#### 3. The "Inverted" Anomaly: Water Quality

* **The Finding:** Interestingly, **Water Quality (Poor)** is slightly *more* prevalent among healthy individuals ($22.2\%$) than CKD patients ($19.5\%$).
* **The Interpretation:** In real-world epidemiology, poor water quality (heavy metal contamination, etc.) is a known driver of chronic kidney issues. However, because this is a **synthetic dataset**, this minor inversion is a classic example of statistical independence or intentional uniform distribution generated by the simulation algorithm. It tells us that in this specific data environment, water quality is acting as a weak, non-predictive feature.

#### 4. Low-Prevalence Indicators

* **Previous Acute Kidney Injury (AKI) & Heavy Metals Exposure:** These occupy the bottom slots. While an AKI history is slightly higher in the sick group ($10.5\%$ vs. $11.1\%$—another minor uniform layout fluctuation), their low overall numbers ($<11\%$) mean they are rare attributes across the entire cohort.

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
