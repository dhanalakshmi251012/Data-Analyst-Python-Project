# Data-Analyst-Python-Project
# 🛌 Data Analysis of Human Health and Lifestyle – Insights for a Healthier Life
## Project Overview:
- This project analyzes health and lifestyle data to identify factors affecting sleep quality and overall well-being. The analysis explores the impact of occupation, physical activity, and stress on sleep disorders, providing data-driven recommendations for healthier living.

## Objective:

- Explore correlations between lifestyle factors (physical activity, stress, BMI) and health outcomes.
Investigate the impact of different occupations on sleep quality and disorder prevalence.
Develop insights and recommendations to mitigate sleep disorders and promote healthier lifestyles.

## Dataset:

- Records: 374 entries
- Features: 13 attributes including age, gender, occupation, sleep duration, quality of sleep, physical activity, stress, BMI, blood pressure, heart rate, daily steps, and sleep disorders.
## 🛠️ Technologies & Tools:
Python – Data analysis and scripting
Pandas – Data manipulation and preprocessing
Matplotlib – Data visualization and plotting
📊 Data Preprocessing:
python
Copy code
import pandas as pd  
import matplotlib.pyplot as plt  

# Load Dataset  
data = pd.read_csv("Sleep_health_and_lifestyle_dataset.csv")  

# Inspect the Data  
print(data.info())  
print(data.head())  

# Fill Missing Values  
data['Sleep Disorder'].fillna('Normal', inplace=True)  
🔍 Key Analyses:
1. Sleep Disorder Distribution (Pie Chart):
python
Copy code
plt.figure(figsize=(8, 6))  
data["Sleep Disorder"].value_counts().plot.pie(autopct="%.1f%%", startangle=90)  
plt.title("Sleep Disorder Distribution")  
plt.ylabel("")  
plt.show()  
🔸 Insight:

58.5% of individuals do not suffer from any sleep disorder.
Sleep Apnea and Insomnia account for approximately 20.9% and 20.6% respectively.
2. Occupation Analysis (Bar Chart):
python
Copy code
occupation = data.groupby("Sleep Disorder")["Occupation"].value_counts().unstack()  
occupation.plot(kind='bar', figsize=(10, 7))  
plt.title("Sleep Disorders by Occupation")  
plt.xlabel("Sleep Disorder")  
plt.ylabel("Count")  
plt.show()  
🔸 Insight:

Nurses and doctors show a higher prevalence of Sleep Apnea.
Salespersons are more likely to experience Insomnia compared to other professions.
3. Gender-based Sleep Disorder Analysis (Bar Chart):
python
Copy code
gender = data.groupby("Sleep Disorder")["Gender"].value_counts()  
gender.plot(kind='bar', color=["#1f77b4", "#ff7f0e"], figsize=(8, 6))  
plt.title("Sleep Disorder by Gender")  
plt.xlabel("Sleep Disorder - Gender")  
plt.ylabel("Count")  
plt.show()  
🔸 Insight:

Female participants show higher instances of Sleep Apnea, while males are more affected by Insomnia.
4. Physical Activity and Sleep Quality Correlation:
python
Copy code
plt.figure(figsize=(10, 5))  
plt.scatter(data["Physical Activity Level"], data["Quality of Sleep"], color='skyblue')  
plt.title("Physical Activity vs Quality of Sleep")  
plt.xlabel("Physical Activity Level (minutes)")  
plt.ylabel("Quality of Sleep")  
plt.grid(True)  
plt.show()  
🔸 Insight:

Individuals with ≥60 minutes of physical activity exhibit higher sleep quality.
📈 Health Insights and Recommendations:
Maintain Adequate Sleep: Aim for 7-9 hours of sleep per day.
Engage in Physical Activity: At least 60 minutes daily reduces the risk of sleep disorders.
Manage Stress: Keep stress levels below 6 for better sleep quality.
Healthy BMI: Maintain a normal BMI through diet and regular activity.
Increase Daily Steps: Walk a minimum of 6000 steps/day to enhance overall health.
🏆 Results:
python
Copy code
healthy = data[(data["Quality of Sleep"] >= 7) &   
               (data["Physical Activity Level"] >= 60) &   
               (data["Stress Level"] <= 5)]  
print(healthy.describe())  
82 individuals met all the criteria for good health (adequate sleep, low stress, and sufficient physical activity).
Average daily steps for this group: 7634 steps.
Conclusion:
This project highlights the importance of lifestyle factors in maintaining good health and preventing sleep disorders. The analysis provides actionable insights that can be applied to improve sleep quality, manage stress, and promote overall well-being.
