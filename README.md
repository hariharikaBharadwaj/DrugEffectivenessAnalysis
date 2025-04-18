# DrugEffectivenessAnalysis
Data analytics on Health care project

Project Documentation:
Drug Effectiveness project was designed as part of Data Analytics course to demonstrate practical application of data analytics and BI tools in healthcare. The core aim was to simulate a real-world healthcare analysis scenario using Power BI, supported by structured data modeling, cleaning, and reporting techniques.
1. Data Cleaning and Preparation (Excel)
The dataset comprised multiple sheets including Master Data, Patient Details, Treatment, Outcomes, Vitals, and Drug List. Initial steps included reviewing each sheet, identifying null or inconsistent values, and standardizing formats:
- Date columns were converted to datetime format.
- Duplicates and irrelevant rows (e.g., 'To be deleted') were removed.
- Numerical columns were checked for outliers or invalid entries.
- Text fields were trimmed and normalized for consistency.
This analysis is based on the dataset from `Drug_Effectiveness_Data.xlsx`, which includes the following sheets:
- Patient_Details: Demographic and diagnostic information.
- Treatment: Drug administered, dosage, duration, recovery time, and medical facility data.
- Outcomes: Outcome type, adherence %, and side effects.
- Vitals: Before/after metrics of BP and cholesterol, plus BMI and smoking status.
- DrugList: Lookup table with average dosages for each drug.
2. Loading into Power BI
All cleaned Excel sheets were imported into Power BI using the 'Get Data' feature. Power BI's query editor was used for further transformations, such as:
- Renaming columns for clarity.
- Creating calculated columns for Age Groups, BMI categories, and Treatment Duration.
- Setting appropriate data types for fields (e.g., categorical vs. numeric).
- Removing unnecessary columns before modeling.
3. Data Modeling
The Power BI data model was created using the 'Model' view. Relationships were established as follows:
- One-to-many between Patient_Details and Master Data on PatientID.
- One-to-many between DrugList and Master Data on DrugID.
- One-to-many between Treatment and Master Data on TreatmentID.
- One-to-many between Outcomes and Master Data on OutcomeID.
- One-to-many between Vitals and Master Data on PatientID + DateOfVitals.
These relationships enabled a star-schema structure, optimizing performance and enabling intuitive report building.

Detailed Relationship Cardinalities
Treatment ↔ Patient Details
Relationship: Many to One. Each patient can have multiple treatments, but each treatment belongs to one patient.
Cardinality:
	Treatment[PatientID] → PatientDetails[PatientID]
Vitals ↔ Patient Details
Relationship: Many to One. Each patient can have many vitals recorded over time.
Cardinality:
	Vitals[PatientID] → PatientDetails[PatientID]    
         
Outcomes ↔ Patient Details
Relationship: Many to One. A patient may have multiple outcomes (e.g., for different treatments or over time).
 Cardinality:
	Outcomes[PatientID] → PatientDetails[PatientID]

Vitals ↔ Treatment
Relationship: Many to One. If vitals are tied to a treatment event (e.g., vitals before/after a drug is given), there may be multiple vitals per treatment.
Cardinality: 
	Vitals[TreatmentID] → Treatment[TreatmentID]

Outcomes ↔ Treatment
Relationship: Many to One. A single treatment could result in multiple outcome entries (e.g., recovery, side effects, relapse).
Cardinality
	Outcomes[TreatmentID] → Treatment[TreatmentID]   
 
4. Dashboard Pages and Insights
The dashboards were structured to deliver targeted insights across multiple perspectives:
• Drug Effectiveness Overview: Shows top-performing drugs by diagnosis and outcome.
• Patient Demographics & Risks: Correlates BMI, smoking status, and age with recovery.
• Hospital & Region Analysis: Evaluates recovery performance across regions and hospitals.
• Doctor & Adherence Insights: Analyzes prescribing patterns and impact of treatment adherence.
• Disease Stage & Symptoms: Explores symptom severity and recovery trends.
• Patient Journey: Timeline visual tracking diagnosis to recovery, with vitals trend line and notes context.

5. Relationship Analysis
Descriptive analysis revealed the following:
- Patients treated with Sitagliptin or Simvastatin had better outcomes for specific diagnoses like Type 2 Diabetes and Hyperlipidemia.
- Lower BMI and non-smoker profiles correlated with a higher rate of improvement.
- Top-performing hospitals in New York and California consistently delivered better results.
- Age groups 45–75 showed the best response to treatment.
- Strong relationships were observed between real-time notes suggesting adherence and quicker recovery.
These findings underscore the importance of lifestyle factors, institutional effectiveness, and adherence in treatment success.

6. Challenges Encountered and Solutions
• Inconsistent Date Formats: Solved by converting all date columns using Power BI's Power Query.
• Ambiguous Side Effects Text: Categorized side effects by keyword matching for severity tagging.
• Missing Vitals Entries: Imputed or excluded based on context and presence of core data.
• Inter-sheet Redundancy: Ensured referential integrity by removing duplicated patient IDs and aligning keys.

7. Learnings and Reflections
This project enhanced understanding of:
- Designing robust data models for real-world problems.
- Integrating multi-source Excel datasets into a unified BI solution.
- Using DAX and Power Query effectively for transformation and KPI development.
- Communicating insights through well-structured visuals with business relevance.
The project reflects a complete data lifecycle from ingestion to actionable insight generation.
Throughout the process, industry-standard practices were adopted, including:
- Use of star-schema modeling for efficient and scalable data relationships.
- Clear data lineage from raw input to dashboard visualization.
- Modular dashboard pages to focus on specific analysis goals.
- Analytical storytelling using visuals like bar charts, line graphs, card indicators, and slicers for interactivity.



