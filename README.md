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
       # INCLUDE YOUR CODING AND OUTPUT SCREENSHOTS HERE
import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df

# OUTPUT
<img width="484" height="447" alt="image" src="https://github.com/user-attachments/assets/c354d55f-2b47-40f0-96b8-f0138e3472b4" />

# CODING
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])

# OUTPUT
<img width="266" height="237" alt="image" src="https://github.com/user-attachments/assets/a6d161e0-c8d2-4fd0-b61b-8cdd6eb9d288" />

# CODING
df['bo2']=e1.fit_transform(df[["ord_2"]])
df

# OUTPUT
<img width="475" height="441" alt="image" src="https://github.com/user-attachments/assets/d8aedcca-d546-42fb-83fb-6e05b637c4e4" />

# CODING
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc

# OUTPUT
<img width="504" height="435" alt="image" src="https://github.com/user-attachments/assets/b6c62655-fc69-4ea2-9cab-aefcc99da4e1" />

# CODING
from sklearn.preprocessing import OneHotEncoder
import pandas as pd

ohe = OneHotEncoder(sparse_output=False)   # use sparse_output instead of sparse
df2 = df.copy()
enc = pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]),
                   columns=ohe.get_feature_names_out(["nom_0"]))  # add column names
df2 = pd.concat([df2, enc], axis=1)
df2

# OUTPUT
<img width="799" height="451" alt="image" src="https://github.com/user-attachments/assets/ddeea582-491b-426e-a90a-699d3c8c8405" />

# CODING
pd.get_dummies(df2,columns=["nom_0"])

# OUTPUT
<img width="1101" height="438" alt="image" src="https://github.com/user-attachments/assets/d4238ec7-a972-47ee-bb22-d1c6675bceab" />

# CODING
from category_encoders import BinaryEncoder
import pandas as pd

df = pd.read_csv("data.csv")
be = BinaryEncoder()
nd = be.fit_transform(df[['Ord_2']])   # Pass as DataFrame, not Series
dfb = pd.concat([df, nd], axis=1)
dfb

# OUTPUT
<img width="923" height="443" alt="image" src="https://github.com/user-attachments/assets/d6b3d307-9b3f-4bd6-b4b0-684835e1c71d" />

# CODING
from category_encoders import TargetEncoder
te=TargetEncoder()
CC=df.copy()
new=te.fit_transform(X=CC["City"],y=CC["Target"])
CC=pd.concat([CC,new],axis=1)
CC

#OUTPUT
<img width="737" height="452" alt="image" src="https://github.com/user-attachments/assets/871cdd68-00c5-4a66-ad7f-ecb7008f682e" />








# RESULT:
       # INCLUDE YOUR RESULT HERE

       
