
# **README**

## **Project Title: Trends in Species Abundance Over Time**

### **Overview**
This project analyzes trends in species abundance and zonation levels over a series of years using a dataset. The analysis aims to understand ecological shifts and the factors influencing species distributions.

### **Requirements**
To run this project, you will need the following Python libraries:
- `pandas`
- `matplotlib`
- `seaborn`


### **Dataset**
The dataset used in this project is in CSV format and contain the following columns:
- **Year**: The year of observation.
- **Species**: The species name.
- **Zonation Level**: The zonation classification.
- **Abundance**: The count or measure of abundance for each species.

Make sure to replace `'dataset - Sheet1.csv'` with the actual path to your dataset file.

### **Code Explanation**

1. **Load the Dataset**
   ```python
   df = pd.read_csv('dataset - Sheet1.csv')  # Replace with your actual file path
   ```

2. **Zonation Analysis**
   - Group the data by `Year` and `Zonation Level` to analyze shifts in abundance.
   ```python
   zonation_analysis = df.groupby(['Year', 'Zonation Level']).agg({'Abundance': 'sum'}).reset_index()
   ```

   - Display the zonation analysis results.
   ```python
   print(zonation_analysis)
   ```

   - Plot the shifts in zonation over the years.
   ```python
   plt.figure(figsize=(12, 6))
   sns.lineplot(data=zonation_analysis, x='Year', y='Abundance', hue='Zonation Level', marker='o')
   plt.title('Trends in Abundance by Zonation Level Over Years')
   plt.xlabel('Year')
   plt.ylabel('Total Abundance')
   plt.legend(title='Zonation Level')
   plt.grid()
   plt.show()
   ```

3. **Abundance Analysis**
   - Group the data by `Year` and `Species` to analyze abundance trends.
   ```python
   abundance_analysis = df.groupby(['Year', 'Species']).agg({'Abundance': 'sum'}).reset_index()
   ```

   - Plot the abundance trends over the years for different species.
   ```python
   plt.figure(figsize=(12, 6))
   sns.lineplot(data=abundance_analysis, x='Year', y='Abundance', hue='Species', marker='o')
   plt.title('Trends in Abundance by Species Over Years')
   plt.xlabel('Year')
   plt.ylabel('Total Abundance')
   plt.legend(title='Species', bbox_to_anchor=(1.05, 1), loc='upper left')
   plt.grid()
   plt.show()
   ```

### **Results**
The analysis provides insights into the trends of species abundance and zonation levels, highlighting ecological shifts over time.

### **Contributing**
If you would like to contribute to this project, please feel free to submit a pull request or open an issue.
