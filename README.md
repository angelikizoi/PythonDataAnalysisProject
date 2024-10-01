# Overview

Welcome to my analysis of the data job market, focusing on data analyst roles. This project was created out of a desire to navigate and understand the Greek job market more effectively. It delves into the top-paying and in-demand skills to help find optimal job opportunities for data analysts.

The data sourced from [Luke Barousse's Python Course](https://lukebarousse.com/python) which provides a foundation for my analysis, containing detailed information on job titles, salaries, locations, and essential skills. Through a series of Python scripts, I explore key questions such as the most demanded skills, salary trends, and the intersection of demand and salary in data analytics.

# The Questions

Below are the questions I want to answer in my project:

1. What are the skills most in demand for the top 3 most popular data roles?
2. How are in-demand skills trending for Data Analysts?
3. How well do jobs and skills pay for Data Analysts?
4. What are the optimal skills for data analysts to learn? (High Demand AND High Paying) 

# Tools I Used

For my deep dive into the data analyst job market, I harnessed the power of several key tools:

- **Python:** The backbone of my analysis, allowing me to analyze the data and find critical insights.I also used the following Python libraries:
    - **Pandas Library:** This was used to analyze the data. 
    - **Matplotlib Library:** I visualized the data.
    - **Seaborn Library:** Helped me create more advanced visuals. 
- **Jupyter Notebooks:** The tool I used to run my Python scripts which let me easily include my notes and analysis.
- **Visual Studio Code:** My go-to for executing my Python scripts.
- **Git & GitHub:** Essential for version control and sharing my Python code and analysis, ensuring collaboration and project tracking.

# Data Preparation and Cleanup

This section outlines the steps taken to prepare the data for analysis, ensuring accuracy and usability.

## Import & Clean Up Data

I start by importing necessary libraries and loading the dataset, followed by initial data cleaning tasks to ensure data quality.

```python
# Importing Libraries
import ast
import pandas as pd
import seaborn as sns
from datasets import load_dataset
import matplotlib.pyplot as plt  

# Loading Data
dataset = load_dataset('lukebarousse/data_jobs')
df = dataset['train'].to_pandas()

# Data Cleanup
df['job_posted_date'] = pd.to_datetime(df['job_posted_date'])
df['job_skills'] = df['job_skills'].apply(lambda x: ast.literal_eval(x) if pd.notna(x) else x)
```

## Filter Greek Jobs

To focus my analysis on the Greek job market, I apply filters to the dataset, narrowing down to roles based in the United States.

```python
df_gr = df[df['job_country'] == 'Greece']

```


# The Analysis

Each Jupyter notebook for this project aimed at investigating specific aspects of the data job market. Here’s how I approached each question:

## 1.What are the skills most in demand for the top 3 most popular data roles?

To find the most demanded skills for the top 3 most popular data roles. I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills I should pay attention to depending on the role I'm targeting.

View my notebook with detailed steps here: 
[2_Skill_Demand.ipynb](Project\2_Skill_Demand.ipynb)

### Results
![Visualisation of Top Skills for Data Nerds](Project\images\skill_demand_all_data_roles.png)

### Insights
- SQL is the most requested skill for Data Analysts and Data Engineers, with it in over half the job postings for both roles. For Data Scientists, Python is the most sought-after skill, appearing in 74% of job postings.
- Data Engineers require more specialized technical skills (AWS, Azure, Spark) compared to Data Analysts and Data Scientists who are expected to be proficient in more general data management and analysis tools (Excel, Tableau).
- Python is a versatile skill, highly demanded across all three roles, but most prominently for Data Scientists (74%) and Data Engineers (65%).

## 2. How are in-demand skills trending for Data Analysts?
To find how skills are trending in 2023 for Data Analysts, I filtered data analyst positions and grouped the skills by the month of the job postings. This got me the top 5 skills of data analysts by month, showing how popular skills were throughout 2023.

View my notebook with detailed steps here: 
[3_Skills_trend.ipynb](Project\3_Skills_trend.ipynb)

### Results
![Trending Top Skills for Data Analysts in Greece](Project\images\skill_trend_data_analysts.png)

### Insights
- The skills with the most steady demand over the course of 2023 are SQL and Excel, making them core skills for data analysts in Greece.
- Python also shows a solid presence but may be more role-specific.
- Power BI and SAS, while important, appear to fluctuate more depending on specific job requirements or market conditions.

## 3. How well do jobs and skills pay for Data Analysts?
To identify the highest-paying roles and skills, I only got jobs in Greece and looked at their median salary. But first I looked at the salary distributions of common data jobs like Data Scientist, Data Engineer, and Data Analyst, to get an idea of which jobs are paid the most. 


View my notebook with detailed steps here: 
[4_Salary_Analysis.ipynb](Project\4_Salary_Analysis.ipynb)

### Salary Analysis for Data Nerds

#### Results
![Salary Distribution in Greece](Project\images\salary_jobs.png)

#### Insights
- Machine Learning Engineers and Senior Data Scientists are the highest earners, with median salaries exceeding $140K and going up to nearly $200K.
- Data Engineers also command high salaries, with medians around $110K.
- Data Scientists are well-paid but not as much as the Senior positions, with a median around $100K.
- Data Analysts and Software Engineers have the lowest medians, around $70K, but still represent good earning potential in the data and tech industries.
- Outliers are present, particularly for Data Scientist, which suggests that there may be lower-paying opportunities in this role compared to the higher-paying positions.

### Highest Paid and Most In-Demand Skills for Data Analysts

Next, I narrowed my analysis and focused only on data analyst roles. I looked at the highest-paid skills and the most in-demand skills. I used two bar charts to showcase these.

#### Results
![The Highest Paid and Most In-Demand Skills for Data Analysts in Greece](Project\images\demanded_paid_skills.png)

#### Insights
- Cloud technologies and backend development: Skills such as AWS, Express, Kubernetes, and Docker appear to be the highest-paying, reflecting the growing importance of infrastructure and deployment in data roles.
- Programming languages: Java, R, and Python are highly relevant for both demand and pay, signaling their foundational role in data analysis and software engineering.
- Traditional data analysis tools: Skills such as SQL, Power BI, and Excel remain critical, although they are associated with lower median salaries compared to more technically complex skills.

## 4. What is the most optimal skill to learn for Data Analysts?

To identify the most optimal skills to learn ( the ones that are the highest paid and highest in demand) I calculated the percent of skill demand and the median salary of these skills. To easily identify which are the most optimal skills to learn. 
View my notebook with detailed steps here: 
[5_Optimal_Skills.ipynb](Project\5_Optimal_Skills.ipynb)

### Results
![Most Optimal Skills for Data Analysts in Greece](Project\images\optimal_skills.png)

### Insights
- Technology: Java is the standout technology skill, offering one of the highest median salaries. SAS, while still relevant in specific industries, has a lower demand, and its future in mainstream data analytics could be fading in favor of more modern tools.
- Programming: Python and R are both vital programming languages for data analysts. Python’s high demand reflects its versatility, while R's high salary potential makes it ideal for professionals targeting specialized fields like academia or research.
- Analyst Tools: Power BI and Tableau are essential for data visualization, but Power BI offers a higher salary and more demand compared to Tableau. Both are crucial for transforming raw data into easily understandable insights.
- Cloud: Azure reflects the rising importance of cloud computing for data storage, integration, and analytics. As businesses continue to adopt cloud infrastructure, skills like Azure will only grow in demand.
- Other: SQL remains a core skill for any data analyst, with the highest demand. Its ability to query and manipulate databases ensures that it remains highly relevant across various industries.

# What I Learned

Throughout this project, I deepened my understanding of the data analyst job market and enhanced my technical skills in Python, especially in data manipulation and visualization. Here are a few specific things I learned:

- **Advanced Python Usage**: Utilizing libraries such as Pandas for data manipulation, Seaborn and Matplotlib for data visualization, and other libraries helped me perform complex data analysis tasks more efficiently.
- **Data Cleaning Importance**: I learned that thorough data cleaning and preparation are crucial before any analysis can be conducted, ensuring the accuracy of insights derived from the data.
- **Strategic Skill Analysis**: The project emphasized the importance of aligning one's skills with market demand. Understanding the relationship between skill demand, salary, and job availability allows for more strategic career planning in the tech industry.


# Insights

This project provided several general insights into the data job market for analysts:

- **Skill Demand and Salary Correlation**: There is a clear correlation between the demand for specific skills and the salaries these skills command. Advanced and specialized skills like Python often lead to higher salaries.
- **Market Trends**: There are changing trends in skill demand, highlighting the dynamic nature of the data job market. Keeping up with these trends is essential for career growth in data analytics.
- **Economic Value of Skills**: Understanding which skills are both in-demand and well-compensated can guide data analysts in prioritizing learning to maximize their economic returns.


# Challenges I Faced

This project was not without its challenges, but it provided good learning opportunities:

- **Data Inconsistencies**: Handling missing or inconsistent data entries requires careful consideration and thorough data-cleaning techniques to ensure the integrity of the analysis.
- **Complex Data Visualization**: Designing effective visual representations of complex datasets was challenging but critical for conveying insights clearly and compellingly.
- **Balancing Breadth and Depth**: Deciding how deeply to dive into each analysis while maintaining a broad overview of the data landscape required constant balancing to ensure comprehensive coverage without getting lost in details.


# Conclusion

This exploration into the data analyst job market has been incredibly informative, highlighting the critical skills and trends that shape this evolving field. The insights I got enhance my understanding and provide actionable guidance for anyone looking to advance their career in data analytics. As the market continues to change, ongoing analysis will be essential to stay ahead in data analytics. This project is a good foundation for future explorations and underscores the importance of continuous learning and adaptation in the data field.