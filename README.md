# PwC Power BI Project (Forage Internship)



# Introduction

This project is part of the PwC virtual internship hosted by Forage. The project involves creating an interactive Power BI dashboard to analyze call center performance, customer churn analysis, and Diversity & inclusion dashboard. The aim is to uncover key insights that can help the organization improve efficiency, customer satisfaction, and agent productivity. 

Throughout the project, various steps were followed to source, clean, model, and analyze data using Power BI.

## Task 1: Call Center Performance Dashboard
* Objective : 
To analyze the performance of a call center using various KPIs such as call resolution time, agent performance, and customer satisfaction.
* Key Insights:
Identified peak call times and agent performance gaps.
Created a dynamic dashboard showcasing call resolution rates, average call handling time, and customer satisfaction scores.
Used DAX to calculate metrics like call resolution efficiency and customer satisfaction rating.
* Tools : Power BI, Power Query, Data Modeling, and DAX.
## Task 2: Customer Churn Analysis
* Objective : 
To predict customer churn by analyzing trends and patterns in customer behavior. The focus was on identifying the key factors that contribute to customer attrition.
* Key Insights:
Analyzed customer data to highlight trends that lead to higher churn rates.
Built a visual report showcasing churn likelihood by customer segment.
Recommended strategies for improving retention based on data analysis.
* Tools : Power BI, DAX, Predictive Analysis.
## Task 3: Diversity & Inclusion Dashboard
* Objective : 
To visualize diversity and inclusion metrics within a company, showcasing the gender and ethnic composition of the workforce.
* Key Insights:
Built an interactive dashboard that visualized the company’s diversity across departments.
Analyzed trends in employee demographics, and highlighted areas for improvement in inclusion initiatives.
Provided recommendations based on the insights drawn from data visualizations.
* Tools: Power BI, DAX.


# Data Source

The Dataset used for this analysis was presented by Pwc Switzerland and available at: Forage Job Simulation 


# DAX 
## Task 1 : 
* Agent Call = CALCULATE(COUNTROWS('Call Center Dataset'), ALL('Call Center Dataset'[AgentKey])) 
* Avg = CALCULATE(COUNTROWS('Call Center Dataset'), Answered[Answered (Y/N)] ="Y")
* Avg speed of ans in seconds = CALCULATE(AVERAGE(SpeedofAnswerInSeconds[Speed of answer in seconds]), Answered[Answered (Y/N)]="Y")
* Call by topic = CALCULATE(COUNTROWS('Call Center Dataset'), Topic[TopicKey] = "Admin Support")
* Total Answered call = CALCULATE(COUNTROWS('Call Center Dataset'),Answered[Answered (Y/N)] ="Y", ALL('Call Center Dataset'[AgentKey]))
* Total Call Id = --CALCULATE(COUNTA(Main[CallKey]), ALL(Main))
  CALCULATE(COUNTROWS('Call Center Dataset'), ALL('Call Center Dataset'[AgentKey]))
* Total No. of NotResolved = CALCULATE(COUNTROWS('Call Center Dataset'), Resolved[Resolved] = "N", ALL('Call Center Dataset'[AgentKey]))
* Total No. of Resolved = CALCULATE(COUNTROWS('Call Center Dataset'), Resolved[Resolved] = "Y", ALL('Call Center Dataset'[AgentKey]))
* Total Rejected call = CALCULATE(COUNTROWS('Call Center Dataset'),Answered[Answered (Y/N)] = "N",ALL('Call Center Dataset'[AgentKey]))
## Task 2 : 
* % Dependent = DIVIDE(CALCULATE(COUNT('Churn-Dataset'  [Dependents]), 'Churn-Dataset'[Dependents]="Yes",'Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn-Dataset'[Dependents]),'Churn-Dataset'[Churn]="Yes"),0)
* % Device Protection = DIVIDE(CALCULATE(COUNT('Churn-Dataset'[DeviceProtection]),'Churn-Dataset'[DeviceProtection]="Yes",'Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn-Dataset'[DeviceProtection]),'Churn-Dataset'[Churn]="Yes"),0)
* % Online backup = DIVIDE(CALCULATE(COUNT('Churn-Dataset'[OnlineBackup]),'Churn-Dataset'[OnlineBackup]="Yes",'Churn-Dataset'[Churn]="Yes"), CALCULATE(COUNT('Churn-Dataset'[OnlineBackup]),'Churn-Dataset'[Churn]="Yes"), 0)
* % Online Security = DIVIDE(CALCULATE(COUNT('Churn-Dataset'[OnlineSecurity]),'Churn-Dataset'[OnlineSecurity]="Yes",'Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn-Dataset'[OnlineSecurity]),'Churn-Dataset'[Churn]="Yes"),0)
* % Partner = DIVIDE(CALCULATE(COUNT('Churn-Dataset'[Partner]),'Churn-Dataset'[Partner]="Yes",'Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn-Dataset'[Partner]),'Churn-Dataset'[Churn]="Yes"),0)
* % Phone service = DIVIDE(CALCULATE(COUNT('Churn-Dataset'[PhoneService]),'Churn-Dataset'[PhoneService] ="Yes", 'Churn-Dataset'[Churn] = "Yes"),CALCULATE(COUNT('Churn-Dataset'[PhoneService]),'Churn-Dataset'[Churn] = "Yes"),0)
* % Straming TV = DIVIDE(CALCULATE(COUNT('Churn-Dataset'[StreamingTV]),'Churn-Dataset'[StreamingTV]="Yes",'Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn-Dataset'[StreamingTV]),'Churn-Dataset'[Churn]="Yes"),0)
* % Streaming Movie = DIVIDE(CALCULATE(COUNT('Churn-Dataset'[StreamingMovies]),'Churn-Dataset'[StreamingMovies]="Yes",'Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn-Dataset'[StreamingMovies]),'Churn-Dataset'[Churn]="Yes"),0)
* % Tech support = DIVIDE(CALCULATE(COUNT('Churn-Dataset'[TechSupport]),'Churn-Dataset'[TechSupport]="Yes",'Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn-Dataset'[TechSupport]),'Churn-Dataset'[Churn]="Yes"),0)
* Avg monthly chargel = AVERAGE('Churn-Dataset'[MonthlyCharges])
* Avg yearly charges = AVERAGE('Churn-Dataset'[TotalCharges])
* Churn count = CALCULATE(COUNT('Churn-Dataset'[Churn]), ALLSELECTED('Churn-Dataset'[Churn]),'Churn-Dataset'[Churn] = "Yes")
* Churn rate = DIVIDE(CALCULATE(COUNT('Churn-Dataset'[Churn]), 'Churn-Dataset'[Churn] = "yes" ), COUNT('Churn-Dataset'[Churn]), 0)
* Senior citizen = DIVIDE(CALCULATE(COUNT('Churn-Dataset'[SeniorCitizen]),'Churn-Dataset'[SeniorCitizen]=1,'Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('Churn-Dataset'[SeniorCitizen]),'Churn-Dataset'[Churn]="Yes"),0)
* Yearly charges = CALCULATE(SUM('Churn-Dataset'[TotalCharges]))
## Task 3 :
* % Female = DIVIDE([Female],([Female]+[Male]))
* % Male = DIVIDE([Male],([Female]+[Male])) 
* Avg Female rating = CALCULATE(AVERAGE('Pharma Group AG'[FY20 Performance Rating]),FILTER('Pharma Group AG','Pharma Group AG'[Gender]="Female"))
* Avg Male rating = CALCULATE(AVERAGE('Pharma Group AG'[FY20 Performance Rating]),FILTER('Pharma Group AG','Pharma Group AG'[Gender]="Male"))
* Female = CALCULATE(DISTINCTCOUNT('Pharma Group AG'[Employee ID]),FILTER('Pharma Group AG','Pharma Group AG'[Gender]="Female"))
* Male = CALCULATE(DISTINCTCOUNT('Pharma Group AG'[Employee ID]),FILTER('Pharma Group AG','Pharma Group AG'[Gender]= "Male"))

### Visualizations (using pivot Table)
## Task 1 :
* Card
* Slicer
* Donut chart
* Line chart
* 100% Stacked bar chart
* Matrix
* Gauge

## Task 2 :
* Card
* Slicer
* Donut chart
* Pie chart
* Clustered bar chart

## Task 3 :
* Multi-row card
* Slicer
* Donut chart
* 100% Stacked bar chart
* Line & clustered column chart
* Clustered bar chart
* Line chart
* Stacked bar chart
* 100% Stacked column chart

 # Task 1: Call Center Performance Dashboard (Power BI)

![Pwc_Dashboard](https://github.com/user-attachments/assets/319efeb5-ea5b-42b7-8745-f792de03c008)

* Data Modeling (Star Schema)
![Pwc_Star schema](https://github.com/user-attachments/assets/cd31188c-4cb5-48a2-b7de-47abf13cddaf)


# Task 2 : Customer Churn Analysis

![Customer_Churn_Dashboard](https://github.com/user-attachments/assets/945261da-22ad-49ed-8087-0f8470099eb3)

* Data Modeling

![Customer_Churn_Modeling](https://github.com/user-attachments/assets/756fca6b-b2af-413d-91bf-574ec0647595)


# Task 3 : Diversity & Inclusion Dashboard
* Page 1
![Diversity and inclusion Dashboard_page 1](https://github.com/user-attachments/assets/f4814c64-4d64-4c4f-b6f3-b5b5a8f1830a)
* Page 2
![Diversity and inclusion Dashboard_page 2](https://github.com/user-attachments/assets/2b9dfaf2-62fd-4bbb-b2c7-59b78d9b4be1)

* Data Modeling
![Diversity and Inclusion_Dashboard Modeling](https://github.com/user-attachments/assets/47177916-3b2d-4f1d-9106-ff15bcf16bbc)


# Key Insights

The PwC Dashboard provides valuable insights, including:

## Task 1: Call Center Performance Dashboard

* Agent Performance: Significant variance in performance across agents, with top performers handling higher call volumes and achieving quicker resolutions.

* Customer Satisfaction: Higher satisfaction was observed when calls were resolved during the first interaction. Agents with lower resolution times tended to have better customer feedback.
* Peak Call Times: The majority of calls were received during specific peak hours, suggesting the need for optimized staffing during those times to reduce wait times and improve service efficiency.

## Task 2: Churn Analysis

* High-Risk Segments: Identified customer segments with the highest likelihood of churn based on factors such as long response times, unresolved issues, and low customer satisfaction scores.
* Retention Strategies: Customers with frequent unresolved issues were more likely to churn, indicating that better resolution protocols could enhance retention rates.
* Predictive Trends: Data analysis revealed specific patterns (e.g., frequent service inquiries and extended wait times) that could serve as early indicators of potential churn.
## Task 3: Diversity & Inclusion Dashboard

* Workforce Diversity: Imbalances in gender and ethnic diversity were identified, especially in leadership roles, indicating areas for improvement in hiring and promotion policies.
* Inclusion Gaps: Certain departments had lower representation of diverse groups, pointing to potential biases or challenges in recruitment or retention within these areas.
* Actionable Recommendations: By visualizing the demographic distribution, insights were drawn to support more inclusive hiring practices and diversity training across the organization.

# Conclusion 

Throughout the Forage PwC Virtual Internship, I gained hands-on experience analyzing and visualizing real-world business data using Power BI and SQL. Each task allowed me to develop actionable insights that could drive meaningful improvements in operational efficiency, customer retention, and workplace diversity.

* Call Center Performance: The insights revealed significant performance gaps and opportunities for optimizing staffing and training, particularly during peak call times. Improving call resolution efficiency directly correlates with higher customer satisfaction, reinforcing the importance of quick, effective service.

* Customer Churn Analysis: The analysis of customer churn patterns provided a roadmap for developing targeted retention strategies. By identifying high-risk segments and early indicators of churn, businesses can proactively address customer concerns and reduce attrition rates.

* Diversity & Inclusion: The Diversity & Inclusion dashboard highlighted the need for more balanced representation across departments and leadership roles. By fostering an inclusive environment and improving hiring practices, the organization can promote a more diverse and equitable workforce.
