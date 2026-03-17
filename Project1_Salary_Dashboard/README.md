# 📊 Data Science Salary Dashboard (2023 Analysis)

## 🎯 Why I Built This
In the rapidly evolving world of data, transparency is key. I developed this project to demystify the global compensation landscape and provide clarity on what data professionals are actually earning. I wanted to create a tool that moves beyond guesswork and uses real market data to empower job seekers in their salary negotiations.

## ❓ The Core Questions
To drive the analysis, I focused on answering these four pivotal questions:
1. **Salary by Role:** What is the median salary for specific roles like Data Scientist, Data Engineer, and Analyst?
2. **Geographic Impact:** Which countries currently offer the most competitive compensation?
3. **Platform Popularity:** Which job boards (LinkedIn, Indeed, etc.) are the most active hubs for data science vacancies?
4. **Employment Trends:** How does job type (Full-time, Contract, Internship) correlate with pay scales?

---

### 🖥️ Full Dashboard Preview
Here is a complete look at the interactive dashboard:

![Main Dashboard](./salarydash.png)

---

## 🛠️ The Mechanism Behind the Charts
This dashboard isn't just a static image—it's built on a dynamic engine that processes data based on user input. Here is the technical breakdown:

### 1. Data Validation & Dynamic Input
Instead of standard slicers, I used **Data Validation** to create custom dropdown menus for **Job Title**, **Country** and **Job Type**. 
* **The Logic:** When a user selects a value from the dropdown, it triggers a ripple effect across the analysis sheets.
* **Dynamic Axis:** The charts are linked to these specific input cells, allowing the X and Y axes to update their values instantaneously based on the selection.

### 2. The Multi-Sheet Analytical Engine
The dashboard is powered by 4 specialized background sheets (**Title**, **Country**, **Type**, **Platform**) which serve as the data processing center:

* **📂 Title Sheet:** This is the core analytical engine. Unlike a simple list, it dynamically calculates the **Median Salary** for each role based on user filters. It ensures that the dashboard reflects real-time market averages.
* **🌍 Country Sheet:** Processes geographic data and maps salaries across different regions. 
* **⚙️ Type Sheet:** Raw data for job types was inconsistent. I built a text-search engine using `ISNUMBER(SEARCH(...))` to categorize messy strings into clean categories (Full-time, Contract, etc.).
* **📊 Platform Sheet:** Aggregates job counts for LinkedIn, Indeed, and other boards, linking them directly to the platform bar chart.

### 3. Advanced Formula Breakdown: The Dynamic Median
The "heart" of the project is the **Dynamic Salary Calculator**. For example, in the **Title** sheet, I engineered a multi-criteria array formula that filters thousands of rows of data based on real-time user selections:
<img width="734" height="298" alt="Screenshot (833)" src="https://github.com/user-attachments/assets/476c933f-e3f7-42a7-be91-f1a758e5257d" />
### 💡 How this logic works:

* **Comparative Analysis:** Even though the user selects one specific role in the dashboard, the **Title** sheet calculates the median for *all* job titles (Data Analyst, Scientist, Engineer, etc.) simultaneously. This allows the chart to show how the selected role's salary compares to others in the same market.
* **User-Driven Filters:** The calculation is strictly bound to the **Country** and **Type** selected in the Data Validation dropdowns. If you change the country to "United Kingdom," every median value in the list updates instantly to reflect that specific market.
* **Boolean Filtering:** The `*` symbol in the formula acts as an `AND` operator, ensuring the engine only picks rows that match all criteria (Title, Country, Type, and non-zero salary) at the same time.

---

## 📊 Dashboard Visualization (Salary Calculator Sheet)
All the processed data from the background sheets flows into the **Salary Calculator** sheet, where the final visuals are rendered:

* **Dynamic Charts:** The charts (Salary Distribution, Map, and Platforms) are built directly from these filtered values. As the backend sheets recalculate, the charts on the main dashboard update their shapes and scales automatically.
* **The "Key Metric" Boxes:** At the bottom of the dashboard, I implemented **`XLOOKUP`** to extract specific values for the user's final selection:
    * **Median Salary:** Uses `XLOOKUP` to find the exact salary for the selected role from the **Title** sheet.
    * **Top Platform & Job Count:** Dynamically retrieves which site has the most postings and the total vacancy count for those specific criteria, providing a quick summary for the user.

## 🏁 Project 1: Conclusion
This project demonstrates how to transform a massive, messy dataset into a high-performance, interactive analytical tool. By engineering a custom "backend" with advanced array formulas, I achieved a level of flexibility and "live" interactivity that standard tools cannot provide. This dashboard serves as a bridge between raw data and actionable career insights.

---

## 🛠️ Comprehensive Excel Skills Applied (Project 1)

Throughout this project, I utilized a wide array of advanced Excel techniques to ensure data integrity and dynamic performance:

* **Advanced Dynamic Array Formulas:** Leveraged complex `{MEDIAN(IF(...))}` array logic to perform multi-criteria calculations across thousands of rows.
* **Boolean Logic Engineering:** Used the `(Criteria1)*(Criteria2)` method within formulas to simulate advanced `AND` logic for filtering.
* **Text Mining & Search:** Integrated `ISNUMBER(SEARCH())` functions to clean and categorize non-standardized text data (e.g., extracting job types from messy strings).
* **Dynamic Data Retrieval:** Implemented **`XLOOKUP`** for instant data pulling into key metric summary boxes.
* **Data Validation & UX Design:** Created intuitive dropdown menus as "triggers" for the dashboard’s backend engine.
* **Relational Backend Structure:** Designed a modular multi-sheet architecture (**Title, Country, Type, Platform**) to act as a structured relational database within Excel.
* **Conditional Data Aggregation:** Used `COUNTIFS` to build platform-specific job volume analyses.
* **Dynamic Sorting:** Employed the `SORT(FILTER())` function combination to ensure geographic data always appears in an organized, user-friendly manner.
* **Advanced Visualization:** Customized Bar Charts and Map Charts directly linked to dynamic calculation ranges for real-time visual updates.
