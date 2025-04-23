## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
```
     import pandas as pd
df=pd.read_csv("/content/Encoding Data.csv")
df
```
![image](https://github.com/user-attachments/assets/1bada278-5599-436c-b4ea-958091238d77)
# ORDINAL ENCODER
```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])
```
# LABEL ENCODER
```
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(df[["ord_2"]])
dfc
```
![image](https://github.com/user-attachments/assets/c50dba69-4468-45ea-8890-e44e74a3c56e)
```
df2=pd.concat([df,enc],axis=1)
df2
```

![image](https://github.com/user-attachments/assets/2a2b96fc-bf1f-41e7-baed-4d34a5301288)
```
pip install --upgrade category_encoders
```
# BinaryEncoder

![image](https://github.com/user-attachments/assets/9cb84dbc-e190-45ab-beba-6a148c6c7c21)
```
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
dfb=pd.concat([df,nd],axis=1)
dfb1=df.copy()
dfb
```

![image](https://github.com/user-attachments/assets/c378d657-7739-427d-8969-b4a3bfeefb54)
# TARGET ENCODER
```
from category_encoders import TargetEncoder
te=TargetEncoder()
cc=df.copy()
new=te.fit_transform(X=cc["City"],y=cc["Target"])
cc=pd.concat([cc,new],axis=1)
cc
```
# FEATURE ENGINEERING

![image](https://github.com/user-attachments/assets/1512a40e-f55f-4456-93fd-a02bc2ede577)
```
df.skew()
```

![image](https://github.com/user-attachments/assets/efb5d971-2bce-45d6-bb2b-0673eec1b99d)
```
df["Highly Positive Skew"]=np.log(df["Highly Positive Skew"])
df
```

![image](https://github.com/user-attachments/assets/d1e6e9a4-0f8f-4bda-955d-b5b4122cc5d5)
```
df["Moderate Positive Skew"]=np.reciprocal(df["Moderate Positive Skew"])
df
```

![image](https://github.com/user-attachments/assets/62910b5f-d846-4787-bf41-a1cc1ad20dc0)
#POWER TRANSFORMATION

![image](https://github.com/user-attachments/assets/d3cae296-4fc9-4a19-9343-dfa11ec02ccd)
```
df["Moderate Negative Skew_yeojohnson"],parameter=stats.yeojohnson(df["Moderate Negative Skew"])
df
```

![image](https://github.com/user-attachments/assets/b88039fb-f8e6-4c25-93b9-de7a86c377ae)
```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```

![image](https://github.com/user-attachments/assets/d5dc2b0f-c586-469d-aa89-49eb5e2ae362)
```
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
```

![image](https://github.com/user-attachments/assets/2a5cc166-64c1-4b28-a607-f91462d48411)
```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```

![image](https://github.com/user-attachments/assets/58e9e14a-e412-4fd2-bbc5-eeb4ab403e9b)

# RESULT:
       # INCLUDE YOUR RESULT HERE

       
