# Why 1 in 6 Telecom Customers Left — and What the Data Reveals
### Telecom Customer Churn & Service Quality Analysis

* **Tools**: Microsoft Excel · Power Query · Power Pivot · DAX
* **Methods**: Data Cleaning · Data Modeling · KPI Analysis · Exploratory Data Analysis · Business Recommendations
* **Dataset**: 3,000 customers

📄 [View the Project Presentation (PDF)](https://drive.google.com/file/d/1sMAPf5xnKLpsG2rayET_xjVbm9GHhHWN/view?usp=sharing)  
📁 [Open the Interactive Excel Workbook (.xlsx)](https://drive.google.com/uc?export=download&id=1O4vy_iaOhMpXo8_0kr5kzCV58bJRMpan)  
*(To explore the workbook: Download it and click **"Enable Editing"** on the top message bar to interact with its PivotTables, slicers, and dashboard elements).*

---

## 1. The 30-Second Story
One in six customers left. The real question was where the business should look to understand the pattern—and what it could do next.

The analysis revealed four findings worth investigating:
* **16.6% customer churn**: 499 out of 3,000 customers were recorded as churned.
* **$38,000.01 in monthly recurring revenue** associated with churned customers, compared with approximately **$207.9K in baseline monthly recurring revenue**.
* **64.14 hours average resolution time for Technical Support** and **63.44 hours for Network Quality**, the two categories with the longest reported resolution times.
* **51.7% of churned customers fell into the under-utilized category** in the customer-level data, suggesting a potential plan-fit question rather than proving that unused allowances caused churn.

The investigation also found that all recorded complaint counts in the analyzed usage records were associated with churned customers. This striking pattern warrants further investigation, particularly into how complaints were recorded and when they occurred relative to churn.

These are observed patterns, not proof of a single cause of churn. The goal was to turn them into specific questions the business could investigate and test.

---

## 2. The Business Problem: Where Should the Company Look First?
Losing a customer means losing a relationship—and potentially losing recurring revenue.

In this dataset, 499 of 3,000 customers were recorded as churned, producing a churn rate of approximately 16.63%. The workbook reports $38,000.01 in monthly recurring revenue associated with churned customers, against baseline monthly recurring revenue of $207,945.

Instead of stopping at the overall churn rate, I investigated three areas:
1. **Service quality**: Were some support categories experiencing substantially longer resolution times or more escalations?
2. **Plan fit**: Did churned customers show usage patterns that could indicate a mismatch between their needs and their plans?
3. **Complaints**: How were complaint records distributed between churned and active customers, and could their timing provide useful information?

To answer these questions, I prepared the data and integrated customer, plan, monthly usage, support-interaction, date, and churn information into an Excel Data Model.

---

## 3. Finding One: Some Support Issues Took Much Longer to Resolve
The reported overall average resolution time was 40.28 hours.

| Support Metric | Result |
| :--- | :--- |
| **Overall average resolution time** | 40.28 hours |
| **Escalation rate** | 25.59% |
| **Technical Support average resolution time** | 64.14 hours |
| **Network Quality average resolution time** | 63.44 hours |

Technical Support and Network Quality had the longest average resolution times among the categories examined.

### Why this matters
Long resolution times can create a frustrating customer experience. They may also indicate operational bottlenecks, complicated technical issues, or processes that need improvement.

However, these results do not establish that support delays caused customers to leave. They identify where a more detailed investigation could begin.

### Recommended business actions
* Review the most frequent issue types within Technical Support and Network Quality.
* Compare resolution times for escalated and non-escalated interactions.
* Investigate whether delays are concentrated in particular periods, plans, or customer segments.
* Examine repeat contacts and customer satisfaction alongside resolution times.
* Test a service target of resolving eligible cases within 24 hours and monitor whether the change improves customer outcomes.

**How to measure success**: Track average and median resolution time, unresolved backlog, escalation rate, repeat contacts, customer satisfaction, and subsequent churn.

*Metric note*: The 40.28-hour average is based on the resolution-time values in the workbook's source column. The category averages should be interpreted with the same care. Missing durations, imputed values, and unresolved interactions can affect comparisons, so the reporting definition should state which records are included.

---

## 4. Finding Two: Plan Utilization Raises a Customer-Fit Question
The customer-level data shows that 258 of the 499 churned customers—approximately 51.7%—fell into the under-utilized category.

This is a more precise result than simply claiming that most churned customers used very little of their allowance. It gives the business a specific segment to investigate.

### Why this matters
Customers who consistently use only a small share of their allowance may be paying for capacity or features they rarely need. Other customers may need more capacity or clearer information about overage charges.

But usage alone cannot explain why a customer leaves. Price, service quality, customer needs, competitor offers, and other factors may also matter.

The analysis also reported 620.7169 GB in average overages among positive overage records for capped-plan usage, approximately 621 GB under that calculation.

### Recommended business actions
* Compare churn rates across plan types and utilization segments.
* Investigate whether customers with consistently low utilization would benefit from alternative plans.
* Examine high-overage records to understand which customers face the largest usage excesses.
* Separate capped plans from unlimited plans and exclude non-numeric placeholders from allowance calculations.
* Compare overage patterns with charges, complaints, satisfaction, and churn.
* Evaluate plan recommendations against both customer outcomes and recurring revenue.

**How to measure success**: Track plan changes, utilization, overage amounts and charges, customer satisfaction, retention, and recurring revenue before and after any intervention.

*Metric notes*:
* The 51.7% result uses the customer-level count of 258 under-utilized customers among 499 churned customers. The utilization band should be defined explicitly in the dashboard or accompanying metric documentation.
* The approximately 621 GB figure represents the average under the positive-overage-record calculation checked in the workbook. It should not be described as the average overage for every capped-plan customer. The unit, aggregation, and population must remain explicit because this is a record-level measure, not necessarily a customer-level average.

---

## 5. Finding Three: Every Recorded Complaint Was Associated with a Churned Customer
In the analyzed usage records, all recorded complaint counts were associated with churned customers, while none were recorded for active customers.

That is one of the most striking patterns in the dataset. It also requires the most caution.

### Why this matters
If complaints consistently precede churn in real operational data, complaint handling could become an important part of a retention strategy.

But the observed distribution does not establish that complaints occurred before customers churned. It may reflect the dataset's construction, the complaint-recording process, the relationship between tables, or the way the records were filtered.

### Recommended business actions
* Check how complaints are recorded and whether the flag or count is linked to churn status.
* Confirm the grain of the complaint information: customer, month, or individual interaction.
* Compare complaint timestamps with recorded churn dates.
* Check that active and churned customers were subject to the same complaint-recording process.
* Test whether complaints predict future churn using data that was not used to identify the original pattern.
* If the relationship is validated, pilot a complaint follow-up process with a 24-hour contact target.

**How to measure success**: Track contact completion, complaint resolution, repeat complaints, satisfaction, and subsequent churn. Compare outcomes against a baseline or suitable comparison group.

*Metric note*: This is a descriptive finding about the analyzed records. It is not a proven “100% leading indicator” or a validated churn-prediction rule. Timing and recording consistency must be established before making either claim.

---

## 6. Finding Four: Dissatisfaction Depends on How It Is Measured
The workbook reports a 46.01% dissatisfaction share among rated support interactions.

The denominator matters. There were 8,491 rated interactions, of which 3,907 had satisfaction scores of 1 or 2.

| Satisfaction Measure | Result |
| :--- | :--- |
| **Rated interactions** | 8,491 |
| **Interactions rated 1 or 2** | 3,907 |
| **Share of rated interactions rated 1 or 2** | **46.01%** |
| **All support interactions** | 9,485 |
| **Share of all interactions represented by ratings of 1 or 2** | **Approximately 41.19%** |

* The 46.01% figure answers: *Among interactions with a rating, what share received a score of 1 or 2?*
* The 41.19% figure answers a different question: *What share of all support interactions had a recorded rating of 1 or 2?*

Neither measure should be interpreted without its denominator. The first excludes unrated interactions, while the second includes them in the total.

### Recommended business actions
* Report the rated-interaction dissatisfaction share alongside the rating coverage.
* Monitor the proportion of interactions with missing satisfaction ratings.
* Compare satisfaction by support category, resolution time, and escalation status.
* Investigate whether dissatisfaction is concentrated in the categories with the longest resolution times.

*Interpretation note*: These results describe recorded support interactions, not necessarily unique customers. A customer may have more than one interaction.

---

## 7. What Could the Business Do About It?
The findings suggest several practical actions that can be tested:

| Priority | Action | Success Measures |
| :--- | :--- | :--- |
| **1. Service Quality** | Investigate long resolution times in Technical Support and Network Quality. Pilot a 24-hour resolution target for eligible cases. | Resolution time, backlog, escalations, repeat contacts, satisfaction, subsequent churn |
| **2. Plan Fit** | Identify customers with consistently low utilization or high overage usage and evaluate suitable alternatives. | Plan changes, overage charges, retention, satisfaction, recurring revenue |
| **3. Complaint Handling** | Investigate complaint timing and recording. If validated, pilot a 24-hour retention follow-up process. | Contact completion, resolution, repeat complaints, satisfaction, subsequent churn |
| **4. Measurement Quality** | Standardize definitions for churn, MRR, utilization, overage, satisfaction, and support metrics. | Reconciled KPIs, consistent reporting, fewer ambiguous records |

These are proposed interventions, not outcomes already demonstrated by the analysis. Their effectiveness should be measured after implementation.

### An Illustrative Retention Scenario
What if the business retained 10% of the customers currently recorded as churned? Using the workbook's reported $38,000.01 monthly recurring revenue associated with churned customers:
* **Target customers**: 10% of 499 is approximately 50 customers.
* **Illustrative monthly revenue retained**: approximately $3,800.
* **Illustrative annual revenue retained**: approximately $45,600, assuming the monthly amount continues for 12 months.

*This is a scenario, not a forecast.* It assumes the retained customers would continue generating the relevant revenue at the current rate. Actual results would depend on which customers were retained, their individual MRR, the timing of retention, and whether their revenue remained stable.

---

## 8. How the Analysis Was Built

### Data Preparation — Power Query
Power Query was used to clean and structure the source data for analysis, including preparing records for the Excel Data Model. The workflow addressed missing values and inconsistencies while preserving the distinction between missing information and genuine business values.

**Resolution-time treatment**:
* Median imputation was applied to eligible resolved support interactions with missing resolution durations.
* Missing durations for pending or unresolved interactions were retained as `NULL` rather than treated as completed cases.
* Imputed values are estimates, not observed resolution times, and can influence summary statistics.

This approach was intended to retain eligible resolved records that lacked a duration. The effect of imputation should still be considered when interpreting averages and comparing support categories.

### Data Modeling — Power Pivot
The project used a multi-fact star-schema approach to analyze customer, plan, usage, support, date, and churn information.

* **Fact tables**: `fact_monthly_usage`, `fact_customer_service`, `fact_churns`
* **Dimension tables**: `dim_customers`, `dim_plans`, `dim_date`

The model used one-to-many relationships from the relevant dimensions to the fact tables, enabling analysis across different business processes without relying on direct fact-to-fact relationships. The date dimension was extended through December 31, 2026, to cover the intended reporting horizon and avoid unwanted blank date categories in date-based filtering.

**Modeling considerations**:
* Each fact table has its own grain. A customer-level record, a monthly customer record, a support interaction, and a churn event are not interchangeable.
* Measures combining multiple fact tables must respect the grain of each table and the relationship paths in the model.
* Repeated monthly records or support interactions must not inflate customer counts or revenue.
* Customer-level churn rates should use distinct customers and a clearly defined customer-level denominator.
* Revenue calculations should use an explicitly defined reporting period and appropriate treatment of churn dates.

### KPI Calculations — DAX
DAX measures were used to calculate and summarize business metrics, including:
* Baseline monthly recurring revenue (MRR)
* Average revenue per user (ARPU)
* Churn-associated MRR
* Customer churn rate
* Average support resolution time
* Escalation rate
* Plan utilization and overage measures
* Retention scenario calculations

The goal was to make the analysis reusable across PivotTables, charts, and slicers rather than relying entirely on static calculations. Metric definitions matter as much as the formulas.

### Analysis and Reporting — Excel
PivotTables, charts, KPI summaries, and slicers were used to explore customer and plan performance and compare support categories. Deliverables include an interactive Excel workbook and a four-page PDF presentation.

---

## 9. Metric Validation Notes

| Metric | Reported Result | Interpretation and Validation |
| :--- | :--- | :--- |
| **Customer churn** | 499 of 3,000; 16.63% | Distinct customer count and customer-level denominator |
| **Churn-associated MRR** | $38,000.01 | Revenue associated with churned customers; confirm period and aggregation |
| **Baseline MRR** | $207,945 | Confirm the reporting period and definition of the baseline |
| **Overall resolution time** | 40.28 hours | Confirm included records and treatment of imputed durations |
| **Escalation rate** | 25.59% | 2,427 escalated interactions out of 9,485 support interactions |
| **Technical Support resolution time** | 64.14 hours | Category-level average; confirm record inclusion and imputation treatment |
| **Network Quality resolution time** | 63.44 hours | Category-level average; confirm record inclusion and imputation treatment |
| **Under-utilized churned customers** | 258 of 499; 51.7% | Customer-level category count; document the utilization-band definition |
| **Average positive overage** | 620.7169 GB (~621 GB) | Average under the positive-overage-record calculation; not necessarily a per-customer average |
| **Complaints among churned customers** | All recorded complaint counts were associated with churned customers | Validate record grain, complaint definition, recording process, and timing relative to churn |
| **Dissatisfaction among rated interactions** | 3,907 of 8,491; 46.01% | Scores of 1 or 2 divided by rated interactions |
| **Ratings of 1 or 2 as a share of all interactions** | Approximately 41.19% | 3,907 divided by 9,485 total support interactions |
| **Illustrative retention scenario** | ~$3,800/mo ($45,600/yr) | Conditional scenario based on retaining approximately 10% of churned customers |

The purpose of these notes is to make the analysis transparent and reproducible. A metric should only be described as independently verified after its calculation, population, denominator, and business definition have been checked.

---

## 10. Limitations
1. **Association is not causation**: The analysis identifies patterns associated with churn but does not establish that support delays, utilization, or complaints caused customers to leave.
2. **Complaint timing matters**: A complaint cannot be considered a leading indicator unless it is shown to occur before churn and to provide useful predictive information.
3. **Missing resolution durations require care**: Median imputation introduces estimated values that may influence averages and category comparisons.
4. **Satisfaction metrics depend on the denominator**: The 46.01% result applies to rated interactions, not all interactions.
5. **Utilization and overage definitions must be explicit**: Comparisons can be misleading if unlimited-plan placeholders, different allowance types, or different aggregation levels are mixed together.
6. **Fact-table grain affects totals**: Repeated monthly records or support interactions can inflate counts and revenue if measures are not designed around distinct customers and the appropriate reporting period.
7. **The retention scenario is hypothetical**: The estimated revenue impact assumes a particular retention rate and continued revenue; it is not evidence of a guaranteed financial outcome.
8. **The dataset has a defined scope**: Findings from this dataset may not generalize to other telecom providers, customer populations, or reporting periods.
9. **Some patterns require data-quality investigation**: The concentration of complaint records among churned customers should be checked for recording or modeling effects before being used as a retention rule.

---

## 11. What I Would Investigate Next
To move from exploratory findings toward stronger business recommendations, I would:
1. Validate the definitions and denominators of the headline KPIs.
2. Compare churn rates across support categories, complaint status, plan types, and utilization segments.
3. Check whether support delays and complaints occurred before the recorded churn event.
4. Investigate relationships between overage charges, plan type, customer satisfaction, and churn.
5. Compare results across periods to determine whether the patterns persist.
6. If suitable historical data is available, test whether these variables improve churn prediction on a separate evaluation period.
7. Measure the outcome of any retention intervention against a baseline or comparison group.

---

## 12. Conclusion
This project uses Excel to investigate a practical telecom business question: *Where should the company look first to better understand churn and protect recurring revenue?*

The analysis highlights three areas worth examining: long support-resolution times, possible mismatches between plan allowances and customer usage, and the concentration of recorded complaints among churned customers. It also examines dissatisfaction while distinguishing the share among rated interactions from the share across all interactions.

The project does not claim to have proved why customers left. Instead, it turns the observed patterns into specific questions, documents the limitations, and proposes actions whose results can be measured.

### Skills Demonstrated
* Excel data preparation and cleaning
* Power Query
* Power Pivot and the Excel Data Model
* Star-schema data modeling
* DAX measures and KPI calculations
* PivotTables, charts, and slicers
* Customer churn and recurring-revenue analysis
* Data-quality checks and metric-definition considerations
* Exploratory data analysis
* Business interpretation and recommendations
* Communicating findings, assumptions, and limitations
