# Data Science
It is a set of disciplines and practices that handle data in a scientific manner 

Usually, it includes but not limited to these steps:
1. Data acquisition

    The data could be in the form of .CSV files. Excel file (.XLSX) is a typical form, or it could be available by API calls, or someone has done the dirty work already and they are all in DWH(Data WareHouse) or Data Lake.

2. Data cleaning & wrangling

    In the actual working environment, data is rarely ready to be used right away.
    Data could be in the nested structure for storage saving purpose (e.g. Bigquery and NoSQL), could be normalized (like general databases). The data need to be flattened before usage


3. Data Engineering

    Simply put, the point of Data Engineering is building a stable and reliable architecture for data storage and consumption

4. Utilization of data

    From traditional consumption like building an application, doing ad hoc analysis, dashboarding and the recent fancy thing such as Machine Learning.

# Jupyter Lab
JupyterLab enables you to work with documents and activities such as Jupyter notebooks, text editors, terminals, and custom components in a flexible, integrated, and extensible manner

# Numpy
NumPy is a commonly used Python data analysis package. By using NumPy, you can speed up your workflow, and interface with other packages in the Python ecosystem

## Lists Of Lists for CSV Data
Before using NumPy, we’ll first try to work with the data using Python and the csv package
 ``` 
  import csv
  with open('winequality-red.csv', 'r') as f:
    wines = list(csv.reader(f, delimiter=';'))
 ```
after reading the data we can print out the first 3 rows

 ``` 
  print (wines[:3])

 ```

the data is read in a list of file each list is a row from the ssvfile 

now we can extract the 2nd row, convert each element to a float add those elements to a list and divide the sum by the total to get the mean using this code 

 ``` 
    qualities = 
    [float(item[-1])for item in wines[1:]]
    sum(qualities)/len(qualities)
 ```
 