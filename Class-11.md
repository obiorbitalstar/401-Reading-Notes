# Pandas
pandas is a fast, powerful, flexible and easy to use open source data analysis and manipulation tool,
built on top of the Python programming language.

to import pandas into your project: 

 ``` 
 import numpy as np
 import pandas as pd

 ```

## Object creation 

 * Creating a Series by passing a list of values, letting pandas create a default integer index:
    ``` 
    s = pd.Series([1, 3, 5, np.nan, 6, 8])

    ```

* Creating a DataFrame by passing a NumPy array 

    ```
     dates = pd.date_range('20130101', periods=6)

    ```

## Viewing data

to view the top and bottom of a fram :

    ```
    df.head()
    df.tail()
    
    ```
Display the index, columns: 
 ```
  df.index

 ```
## Getting 
* Selecting a single column:

    ```
    df['A']

    ```
* Selecting via [], which slices the rows:

    ```
    df[0:3]

    ```

* Selection by label

    ```
    df.loc[dates[0]]

    ```
* Selecting on a multi-axis by label:

    ```
    df.loc[:, ['A', 'B']]

    ```

## Missing data

   pandas primarily uses the value np.nan to represent missing data

  Reindexing allows you to change/add/delete the index on a specified axis. This returns a copy of the data.

    ```
    df1 = df.reindex(index=dates[0:4], columns=list(df.columns) + ['E'])
    df1.loc[dates[0]:dates[1], 'E'] = 1

    ```
* Filling missing data.
    ```
    df1.fillna(value=5)

    ```

## Operations 

### Stats
    Operations in general exclude missing data.

    Performing a descriptive statistic:

        ``` 
        df.mean()
        
        ```
### Apply 
    Applying functions to the data:

        ```
        df.apply(np.cumsum)

        ```


