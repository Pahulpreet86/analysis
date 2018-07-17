# analysis
### Data Pre-processing   
Total number of attributes=49    
Number of attributes with value in single column=19  
Number of attributes with value in multiple columns=30   
#### Processing Steps

##### 1) Attributes with values in multiple columns are converted to a single column.
For example:   
attribute: F2) Secondary Investment Objectives 
columns(related):column\_m,column\_n,column\_o,column\_p,column\_q,column\_r,column\_s,column\_t,column\_u,column\_v

Logic: if the value is available in the first column, that value would be allocated for the F2) Secondary Investment Objectives attribute. Else if the value is not available in first then it looks for value in the second column, if the value exists there, then assign that value else repeat.

##### 2) Based on the repeated pattern of words and phrases, categories label are assigned to them, with the label name as the pattern.
For example:  
attribute: F2) Secondary Investment Objectives     
One of the values available for this attribute was converted as follows:     
Original value: "Learning: Develop STEM skills, practices, or knowledge of students or the public"   
Label value: "Learning"

After all these processing steps, data frame was saved as CSV file and then used for analysis.(2010\_Federal\_STEM\_Education\_Inventory\_Data\_Set.csv)

---
### Stage 1
##### 1)  % growth of funding between year 2008 & 2009 and corresponding target variable is created. (Stage 1.ipynb)

---
### Stage 2

##### 1) All the attributes are visualized. (Stage2 Visualization.ipynb)

##### 2) Normalized Mutual info score is calculated between all non-funding variable and the target variable. Along with that, additionally, visualization using heat map is provided for the same. (Stage2 Mutual info Score.ipynb)
---
### Stage 3
Following steps were taken for the modeling of the data to be used for prediction:   
##### 1) Attributes with missing values more than 15% of the dataset were removed (i.e more than 38 missing instances)

Attributes(left): C1) Funding FY2008,C2) Funding FY2009,C3) Funding FY2010,Agency,Subagency,Year,Mission-specific or General STEM,F1) Primary Investment Objective,F2) Secondary Investment Objectives,H) Educational Services or Products Produced,J) Focus on Underrepresented Groups in STEM,K) Eligibility Restrictions,N) STEM Discipline Focus,Q) Legislation Required to Shift Focus?,U) Measured Outputs, V) Outcomes Measured, Target, Growth of Funding(%)  
       
In these attributes :         

Variables:  C1) Funding FY2008,C2) Funding FY2009,C3) Funding FY2010,Agency,Subagency,Mission-specific or General STEM,F1) Primary Investment Objective,F2) Secondary Investment Objectives,H) Educational Services or Products Produced,J) Focus on Underrepresented Groups in STEM,K) Eligibility Restrictions,N) STEM Discipline Focus,Q) Legislation Required to Shift Focus?,U) Measured Outputs, V) Outcomes Measured

Outcome: Target (1 or 0 )     

The model has to predict the weather for the next year funding will increase or decrease (or same) for an investment.   
##### The data is then restructured to form two dataset: 
###### a) 2008 dataset:
It contains an additional attribute "Period" with the value (for each instance) equal to 2008 and the target variable with value 1 or 0 (which depend on the increase or decrease in funding from 2008 to 2009 and not contain funding of 2009 and 2010)

###### b) 2009 dataset:
It contains an additional attribute "Period" with the value (for each instance) equal to 2009 and the target variable with value 1 or 0 (which depend on the increase or decrease in funding from 2009 to 2010 and not contain funding of 2008 and 2010)

###### These two datasets are concatenated into one and then the labels of the rest of the attributes are converted to dummy variables (1 or 0) and saved as CSV file. (Dataset.csv)
###### (#Stage 3.ipynb)
