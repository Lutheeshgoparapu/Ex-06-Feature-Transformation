# Ex-06-Feature-Transformation
# AIM:
To read the given data and perform Feature Transformation process and save the data to a file.

# EXPLANATION:
Feature Transformation is a technique by which we can boost our model performance. Feature transformation is a mathematical transformation in which we apply a mathematical formula to a particular column(feature) and transform the values which are useful for our further analysis.

# ALGORITHM:
## STEP 1
Read the given Data

## STEP 2
Clean the Data Set using Data Cleaning Process

## STEP 3
Apply Feature Transformation techniques to all the features of the data set

## STEP 4
Save the data to the file

# CODE:
```
Name :Goparapu Lutheesh
Register Number : 212221230029
Feature Transformation - Data_to_Transform.csv
```

```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import statsmodels.api as sm
import scipy.stats as stats
df = pd.read_csv("/content/Data_to_Transform.csv")
print(df)
df.head()
df.isnull().sum()
df.info()
df.describe()
df1 = df.copy()
sm.qqplot(df1.HighlyPositiveSkew,fit=True,line='45')
plt.show()
sm.qqplot(df1.HighlyNegativeSkew,fit=True,line='45')
plt.show()
sm.qqplot(df1.ModeratePositiveSkew,fit=True,line='45')
plt.show()
sm.qqplot(df1.ModerateNegativeSkew,fit=True,line='45')
plt.show()
df1['HighlyPositiveSkew'] = np.log(df1.HighlyPositiveSkew)
sm.qqplot(df1.HighlyPositiveSkew,fit=True,line='45')
plt.show()
df2 = df.copy()
df2['HighlyPositiveSkew'] = 1/df2.HighlyPositiveSkew
sm.qqplot(df2.HighlyPositiveSkew,fit=True,line='45')
plt.show()
df3 = df.copy()
df3['HighlyPositiveSkew'] = df3.HighlyPositiveSkew**(1/1.2)
sm.qqplot(df2.HighlyPositiveSkew,fit=True,line='45')
plt.show()
df4 = df.copy()
df4['ModeratePositiveSkew_1'],parameters =stats.yeojohnson(df4.ModeratePositiveSkew)
sm.qqplot(df4.ModeratePositiveSkew_1,fit=True,line='45')
plt.show()
from sklearn.preprocessing import PowerTransformer 
trans = PowerTransformer("yeo-johnson")
df5 = df.copy()
df5['ModerateNegativeSkew_1'] = pd.DataFrame(trans.fit_transform(df5[['ModerateNegativeSkew']]))
sm.qqplot(df5['ModerateNegativeSkew_1'],line='45')
plt.show()
from sklearn.preprocessing import QuantileTransformer
qt = QuantileTransformer(output_distribution = 'normal')
df5['ModerateNegativeSkew_2'] = pd.DataFrame(qt.fit_transform(df5[['ModerateNegativeSkew']]))
sm.qqplot(df5['ModerateNegativeSkew_2'],line='45')
plt.show()
```

# OUTPUT:
## Feature Transformation - Data_to_Transform.csv
![output](https://github.com/RuchithaReddy28/Ex-06-Feature-Transformation/blob/main/z1.png?raw=true)
![output](https://github.com/RuchithaReddy28/Ex-06-Feature-Transformation/blob/main/z2.png?raw=true)
![output](https://github.com/RuchithaReddy28/Ex-06-Feature-Transformation/blob/main/z3.png?raw=true)
![output](https://github.com/RuchithaReddy28/Ex-06-Feature-Transformation/blob/main/z4.png?raw=true)
![output](https://github.com/RuchithaReddy28/Ex-06-Feature-Transformation/blob/main/z5.png?raw=true)
![output](https://github.com/RuchithaReddy28/Ex-06-Feature-Transformation/blob/main/z6.png?raw=true)
![output](https://github.com/RuchithaReddy28/Ex-06-Feature-Transformation/blob/main/z7.png?raw=true)
![output](https://github.com/RuchithaReddy28/Ex-06-Feature-Transformation/blob/main/z8.png?raw=true)
![output](https://github.com/RuchithaReddy28/Ex-06-Feature-Transformation/blob/main/z9.png?raw=true)
![output](https://github.com/RuchithaReddy28/Ex-06-Feature-Transformation/blob/main/z10.png?raw=true)
## Log Transformation
![output](https://github.com/RuchithaReddy28/Ex-06-Feature-Transformation/blob/main/z11.png?raw=true)
Reciprocal Transformation
![output](https://github.com/RuchithaReddy28/Ex-06-Feature-Transformation/blob/main/z12.png?raw=true)
# SquareRoot Transformation
![output](https://github.com/RuchithaReddy28/Ex-06-Feature-Transformation/blob/main/z13.png?raw=true)
# Power Transformation
![output](https://github.com/RuchithaReddy28/Ex-06-Feature-Transformation/blob/main/z14.png?raw=true)
![output](https://github.com/RuchithaReddy28/Ex-06-Feature-Transformation/blob/main/z15.png?raw=true)
# Quantile Transformation
![output](https://github.com/RuchithaReddy28/Ex-06-Feature-Transformation/blob/main/z16.png?raw=true)

# RESULT:
Thus the Feature Transformation for the given datasets had been executed successfully.

