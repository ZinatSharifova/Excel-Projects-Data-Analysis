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

### 2. Advanced Formulas (The Engine)
To make the dashboard interactive, I used array formulas and complex logic to filter the raw data in the background.

* **Median Salary Calculation:** I used a combination of `MEDIAN` and `IF` to ensure that only the salaries matching the selected criteria are calculated:
```excel
{=MEDIAN(IF(data_table[job_title]=Selected_Job_Title, data_table[salary]))}
