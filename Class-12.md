# Linear regression in python

implementing linear regression in Python using Scikit-learn

## Exploring Boston Housing Data Set
1. The first step is to import the required Python libraries into Ipython Notebook.

    ``` 
    %matplotlib inline 
    import numpy as np
    import pandas as pd
    import scipy.stats as stats
    import matplitlib.pyplot as plt
    import sklearn
    
    ```

2. print the feature names of the  data set.

    ```
    data_set.featrue_names

    ```

3. convert boston.data into a pandas data frame.

    ```
    bos= pd.DataFram(boston.data)
    bos.head()
    #after this line of code is excuted the column names will be in numbers so we have to change the column names with feature names

    bos.columns = boston.freature_names
    bos.head()

    # add boston.target to the fram in a column named PRICE

    bos['PRICE'] = boston.target 

    ```

## Scikit Learn
 lets fit  a linear regression model and predict the Boston housing prices. using least squares method (to elemenate coefficients)

    ```
    from sklearn.linear_model import linearRegression
    x=bos.drop('PRICE' ,axis =1)
    lm = LinearRegression()

    ```

### Fitting a Linear Model
 * print the intercept and number of coefficients.

    ``` 
    print 'Estimated intercept coefficient' , lm.intercept_
    print 'Number of coefficients',len(lm.coef_)

    ```

 * construct a data frame that contains features and estimated coefficients.

    ``` 
    pd.DataFram(zip(X.columns,lm.coef_),columns =['features',estumatedCoefficients])


    ```

 * plot a scatter plot between True housing prices and True RM.

        ``` 
            plt.scatter(bos.RM,box.PRICE)
            plt.xlabel("Average number of rooms per dwelling (RM)")
            plt.ylabel("Housing Price")
            plt.title("Relationship between RM and Price")
            plt.show()
        ```


   

this will give us

![img](https://bigdata-madesimple.com/wp-content/uploads/2016/04/Relationship-between-RM-and-Price.png)











.




code snippt recource:

 https://bigdata-madesimple.com/how-to-run-linear-regression-in-python-scikit-learn/