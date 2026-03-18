# 📈 Project 2: Advanced Salary & Skill Intelligence (Power Pivot & DAX)

## 🎯 Project Overview
This project utilizes **Power Pivot** and **DAX** to create a relational data model that analyzes global compensation. The focus is on real-time comparative analysis between specific markets and global benchmarks.

---

## 📂 Sheet-by-Sheet Breakdown

### 1. Salary Analysis (Dynamic Market Benchmarking)
This sheet features a three-part comparison designed to show how a specific selection stacks up against major markets.
* **The Dynamic "Median Salary" Column:** Unlike the US/Non-US columns, this metric is fully controlled by the **Slicers**. When a user selects a specific country (e.g., UK) and a job role (e.g., Data Analyst), this column instantly recalculates to show the exact median for that specific intersection.
* **Fixed Market Benchmarks:** * **US Median:** Calculated using `CALCULATE([Median Salary], data_jobs_salary[country] = "United States")` to provide a constant high-water mark.
    * **Non-US Median:** Calculated using `CALCULATE([Median Salary], data_jobs_salary[country] <> "United States")` to show the average outside the US market.
* **Logic Integration:** This setup allows a user to see, for example, exactly how much a Data Analyst in United Kingdom earns compared to the fixed US and Non-US standards.

*As shown below, the "Median Salary" column updates instantly to reflect the specific country and role selected via Slicers:*

<img width="856" height="325" alt="Screenshot (844)" src="https://github.com/user-attachments/assets/c8d52d47-d984-4875-972d-826ad3798504" />

### 2. Top Skills in Data (Demand Analysis)
This analysis identifies the most critical technical tools for specific roles.
* **Skill Likelihood Calculation:** I created a measure using `DIVIDE` to determine the frequency of a skill within the total pool of job postings.
* **Contextual Updates:** The visualization is tied to the **Job Title Slicer**, ensuring that the "Top Skills" shown are specifically relevant to the selected career path.

*The bar chart below visualizes the demand for technical skills; as you filter by Job Title and Country, the results update to show the most relevant competencies for that specific path:*

<img width="971" height="271" alt="Screenshot (847)" src="https://github.com/user-attachments/assets/e1c7abe3-c8bf-495d-a9e4-eec68fb9a3c8" />


### 3. Salary vs. Skills (ROI Correlation)
A deep dive into whether a broader skill set leads to a higher paycheck.
* **Correlation Mapping:** Using a **Scatter Plot**, I mapped the median salary against the average number of skills required per job.
* **Analysis:** This visualization helps identify which roles provide the best salary "ROI" per skill learned, distinguishing between roles that require many skills and those that pay high for a few niche tools.

*In the following scatter plot, you can observe the correlation between the average number of skills per job and the median annual compensation across different data roles:*

<img width="1028" height="255" alt="Screenshot (849)" src="https://github.com/user-attachments/assets/f48a0bc0-e219-485a-a429-af1065716aab" />

### 4. Skills Salary Analysis (Individual Skill Valuation)
This sheet identifies the highest-paying individual skills in the industry.
* **The Bi-Directional Filter:** I implemented the `CROSSFILTER` DAX function to force the relationship between the Salary and Skills tables to work in **Both** directions.
* **Formula:** `CALCULATE([Median Salary], CROSSFILTER(data_jobs_salary[job_id], data_jobs_skills[job_id], BOTH))`.
* **Result:** This enabled me to accurately rank the Top 10 skills by their financial value, showing which specific technologies (like Python or SQL) command the highest market premiums.

*Below is the ranking of the top 10 highest-paying skills among the most frequently requested technologies, ensuring that the results reflect real-world market opportunities rather than outliers:*

<img width="1006" height="338" alt="Screenshot (852)" src="https://github.com/user-attachments/assets/f447887b-8efe-4d6d-90fd-0ee3fa3eb3e2" />

## 🛠️ Technical Skills Applied
* **Power Pivot Data Modeling:** Built a relational structure to handle complex many-to-many data scenarios.
* **Advanced DAX Logic:** Developed custom measures using `CALCULATE`, `CROSSFILTER`, and `DIVIDE` to create dynamic, error-free reports.
* **Interactive Dashboarding:** Integrated Slicers and **Report Connections** to ensure that a single user action updates all relevant visualizations across the project.
