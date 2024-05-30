# Diabetes-Prediction
## Dataset
The dataset used in this example includes the following columns:
- Pregnancies
- Glucose
- BloodPressure
- SkinThickness
- Insulin
- BMI
- DiabetesPedigreeFunction
- Age
- Outcome (Class variable: 0 or 1)

## Objective
First goal is to filter out all records where any independent variable has a value of 0 (excluding the Outcome column).
Second goal is to ..

## Steps to Process Data in Google Colab

### 1. Open Google Colab
Go to [Google Colab](https://colab.research.google.com/) and create a new notebook.

### 2. Upload the CSV File
1. Click on the folder icon on the left sidebar.
2. Click "Upload" and select your CSV file from your local machine.

### 3. Process Data
Copy and paste the following code into a cell in your Colab notebook:

```python
import pandas as pd

# Load the data
file_path = '/content/diabetes.csv'  # Path to the uploaded file in Colab
data = pd.read_csv(file_path)

# Display the first few rows of the data
print(data.head())

# Remove records with any 0 values in independent variables (excluding 'Outcome')
columns_to_check = data.columns.drop('Outcome')
data_filtered = data[(data[columns_to_check] != 0).all(axis=1)]

# Display the filtered data
print(data_filtered.head())

# Save the filtered data to a new CSV file
data_filtered.to_csv('/content/filtered_data.csv', index=False)

# Download the filtered data
from google.colab import files
files.download('/content/filtered_data.csv')
