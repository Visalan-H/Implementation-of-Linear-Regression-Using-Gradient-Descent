# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
#### Step 1: Start
#### Step 2: Initialize Parameters
#### Step 3: Create Feature Matrix
#### Step 4: Calculate Predictions
#### Step 5: Calculate Errors
#### Step 6: Update Weights
#### Step 7: Repeat
#### Step 8: Stop
## Program:
```python
/*
Program to implement the linear regression using gradient descent.
Developed by: Visalan H
RegisterNumber: 212223240183
*/
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from sklearn.preprocessing import StandardScaler

def linear_regression(X1,y,learning_rate=0.1,num_iters=1000):
    X = np.c_[np.ones(len(X1)),X1]
    theta = np.zeros(X.shape[1]).reshape(-1,1)
    for _ in range(num_iters):
        #Calculate predictions
        predictions = (X).dot(theta).reshape(-1,1)
        #Calculate errors
        errors=(predictions-y).reshape(-1,1)
        #update theta using gradient descent
        theta-=learning_rate*(1/len(X1))*X.T.dot(errors)
    return theta

data=pd.read_csv("50_Startups.csv")
data.head()

#Assuming rhe last column is your target variable 'y' and the preceding columns.
X = (data.iloc[1:,:-2].values)
X1 =X.astype(float)

scaler = StandardScaler()
y = (data.iloc[1:,-1].values).reshape(-1,1)
X1_Scaled = scaler.fit_transform(X1)
Y1_Scaled = scaler.fit_transform(y)
print(X)
print(X1_Scaled)

#learn model Parameters
theta=linear_regression(X1_Scaled,Y1_Scaled)

#predict target calue for a new data point
new_data=np.array([165349.2,136897.8,471784.1]).reshape(-1,1)
new_Scaled=scaler.fit_transform(new_data)
prediction=np.dot(np.append(1,new_Scaled),theta)
prediction= prediction.reshape(-1,1)
pre = scaler.inverse_transform(prediction)
print(prediction)
print(f"Predicted value:{pre}")
```

## Output:
## X values
<img src="https://github.com/user-attachments/assets/fce04054-c4b3-4f17-9c37-d6d56c81e88d" width="400"/>

## X-Scaled values
<img src="https://github.com/user-attachments/assets/f7446a30-204e-4ae6-991f-da72467a6690" width="400"/>

## Predicted Values
<img src="https://github.com/user-attachments/assets/b7643f53-431b-4d5b-a827-8f98baac0a80" width="400"/>

## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
