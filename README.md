
# Overview

With over **two centuries** of trial records, the *Old Bailey Proceedings Project*, published by the University of Sheffield, provides a rich dataset for analyzing historical crime trends between 1674 and 1913 at Old Bailey, one of London's main criminal courts.

This analysis is driven by the desire to explore criminal patterns over time, examining how *gender, age, punishments, and offenses shaped more than 190.000 trials.

The original data can be found in [Old Baileys](https://www.oldbaileyonline.org/about/data) website.
## 🔎 Questions Explored  

1. **Crime Trends Over Time:**  

   - Has crime increased or decreased over the years?
    - What major shifts occurred in different crime types?

2. **Most Common Crimes & Punishments:**  
   - What were the most frequently committed crimes?  
   - What were the most common punishments?  
   - Have these patterns changed over the years?  

3. **Demographics & Crime:**  
   - How do gender and age relate to crime?  
   - Have these relationships evolved over time?  


## 🛠️ Tools

- **Python:** Used for data analysis and extracting insights.
    - **Pandas Library:** Data analysis.
    - **Matplotlib Library:** Data visualization.
- **Jupyter Notebooks:** For running scripts.
- **Visual Studio Code**
- **Git & GitHub:** For version control and project tracking.

## 📥 Data Collection & Preprocessing 

The dataset was collected, processed, and cleaned using the *`0_Data_Download.ipynb`* notebook.

### Methodology:  

1. **Download and Extraction**  
   - Retrieves the dataset from the Old Bailey website.  
   - Unzips and organizes the files into directories.  

2. **Data Processing**  
   - Identifies all XML files containing trial records.  
   - Extracts following trial details using the `extract_trial_data` function:  
     - **Trial ID.**  
     - **Trial date.**  
     - **Defendant details**: age, gender, and occupation  
     - **Victim gender.**  
     -  **Verdict**: category and subcategory.  
     - **Offence**: category and subcategory.  
     - **Punishment**: category  subcategory. 
    - Stores the extracted trial data as dictionaries in the `trial_records` list.  

3. **Data Cleanup**

   - **Converts list to DataFrame**: The `trial_records` list is converted into a pandas DataFrame.  
   - **Replaces specific values with NaN**: The `mask` function replaces empty lists (`[]`), empty strings (`' '`), and the string `'indeterminate'` with `NaN`.  
   - **Removes duplicates**: Duplicate rows are removed using `drop_duplicates()`.  
   - **Converts date column to datetime**: The `trial_date` column is converted to pandas datetime format.
   - **Exports to JSON format**: The cleaned dataset is saved as a JSON file using the `save_to_json` function.  

## Crime Trends Over Time: Has the Number of Crimes Increased or Decreased?

This section explores how the number of trials recorded at the Old Bailey evolved over time, from 1674 to 1913.

### Methodology:  

1.  The dataset's trial_date column was used to create three new columns: trial_day, trial_month, and trial_year.  

2. The number of trials was plotted for each day, month, and year to observe trends.



### 📅 Trials Per Year

This visualization presents the evolution of criminal trials at the Old Bailey from 1674 to 1913

#### Visualization:

```
trials_per_year = df_timestamp['trial_year'].value_counts().sort_index()
plt.plot(trials_per_year.index, trials_per_year.values)
plt.xlabel('Year')
plt.ylabel('Trial count')
plt.title('Number of trials per year')
plt.show()
```
<p align="center">
  <img src="images\trials_per_year.png" />
</p>


#### Insights:

The number of trials per year at the Old Bailey was influenced by a range of historical, legal, and social factors, which can be divided into three distinct periods:
   - **1674–1778**: the relatively low number of recorded trials, along with a noticeable drop in the early 18th century, can be attributed to the **inconsistency and incompleteness of early editions** of the Proceedings, with many sessions missing from the records. However, as the Proceedings gained popularity, **public demand likely drove improvements in documentation**, contributing to a gradual increase in recorded trials leading up to the late 18th century.

   - **1778-1850**: the number of recorded trials grew significantly as the Proceedings evolved into an **official legal record**, ensuring that all cases heard at the Old Bailey were documented. Additionally, major conflicts such as the **American War of Independence (1775–1783) and the Napoleonic Wars (1803–1815)** contributed to post-war crime surges, leading to spikes in trial numbers. **Social instability, economic hardship**, and concerns over public order likely played roles in the sustained increase in prosecutions throughout the early 19th century.

   - **1850–1913**: from the mid-19th century onward, the number of recorded trials began to eventually decline, influenced by **legal reforms and changes in crime patterns**. The gradual **reduction in capital offenses** reduced the number of severe trials. With fewer subscribers and diminishing commercial viability, the Proceedings were discontinued in April 1913.
   
   










### 📅 Trials Per Month

This visualization illustrates the distribution of trials across different months throughout the recorded period.

#### Visualization:

```
trials_per_month = df_timestamp['trial_month'].value_counts().sort_index()
plt.plot(trials_per_month.index, trials_per_month.values)
plt.xlabel('Month')
plt.ylabel('Trial count')
plt.title('Number of trials per month')
plt.show()
```
<p align="center">
  <img src="images\trials_per_month.png" />
</p>


#### Insights:

- Major spikes in trial activity in September, which can be explained by Old Bailey's legal calendar, that began in November and ended in October. The court possibly aimed to clear cases before the end of the legal cycle.
- Wars, economic crises, and crime trends might have influenced the other spikes in January and April.

### 📅 Trials Per Day

This visualization represents the distribution of trials based on the day of the month.

#### Visualization:

```
trials_per_day = df_timestamp['trial_day'].value_counts().sort_index()
plt.plot(trials_per_day.index, trials_per_day.values)
plt.xlabel('Day')
plt.ylabel('Trial count')
plt.title('Most common trial days')
plt.show()
```
<p align="center">
  <img src="images/trials_per_day.png" />
</p>


#### Insights:

- The number of trials tends to increase around the middle of the month, suggesting that court sessions were more active during this period.

