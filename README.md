
# Overview

The following analysis focuses on data provided by **The Old Bailey Proceedings Online Project**, published by the University of Sheffield. The project makes available a digitised collection of all surviving editions from 1674 to 1913 of the trials that took place at Old Bailey, one of the main criminal courts in London.

The analysis was created out of desire to discover and explore **criminal patterns over the time**, discoursing through gender, age, occupation, punishment categories and offense categories over the defendant and victim of the trials.

The original data can be found in [Old Baileys](https://www.oldbaileyonline.org/about/data) website.
## 🔎 Questions Explored  

1. 📈 **Crime Trends Over Time:**  
   - Has the number of crimes increased or decreased over the century? 

2. 🔍 **Most Common Crimes & Punishments:**  
   - What are the most frequently committed crimes?  
   - What are the most common punishments?  
   - Have these patterns changed over the years?  

3. 👥 **Demographics & Crime:**  
   - How do gender, age, and occupation relate to crime?  
   - Have these relationships evolved over time?  

4. ⚖️ **Crimes & Victims:**  
   - Is there a connection between the type of crime committed and its victims?  

## 🛠️ Tools

- **Python:** Used for data analysis and extracting insights.
    - **Pandas Library:** Data analysis.
    - **Matplotlib Library:** Data visualization.
- **Jupyter Notebooks:** For running scripts.
- **Visual Studio Code**
- **Git & GitHub:** For version control and project tracking.
## 📥 Data Download and Cleanup  

The **`0_Dataset.ipynb`** notebook is responsible for **downloading, extracting, and processing** the trial records dataset.  

### Steps Performed:  

1. **Download and Extraction**  
   - Retrieves the dataset from the Old Bailey website.  
   - Unzips and organizes the files into directories.  

2. **Data Processing**  
   - Identifies all XML files containing trial records.  
   - Extracts key trial details using the `process_trials_on_file` function:  
     - **Trial ID.**  
     - **Trial date.**  
     - **Defendant details**: age, gender, and occupation  
     - **Victim gender.**  
     -  **Verdict**: category and subcategory.  
     - **Offence**: category and subcategory.  
     - **Punishment**: category  subcategory. 
    - Stores the extracted trial data as dictionaries in the `trials_data` list.  

3. **Data Cleanup**

   - **Converts list to DataFrame**: The `trials_data` list is converted into a pandas DataFrame.  
   - **Replaces specific values with NaN**: The `mask` function replaces empty lists (`[]`), empty strings (`' '`), and the string `'indeterminate'` with `NaN`.  
   - **Removes duplicates**: Duplicate rows are removed using `drop_duplicates()`.  
   - **Converts date column to datetime**: The `trial_date` column is converted to pandas datetime format.
   - **Exports to JSON format**: The cleaned dataset is saved as a JSON file using the `save_to_json` function.  
