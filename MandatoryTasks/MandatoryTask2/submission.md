# Regression

## Installation steps
- Fork this repository

## Workflow
- Import necessary libraries numpy, pandas, matplotlib etc.

### Dataset
- The dataset used is https://kaggle.com/datasets/222808b5f956447e66f9b533b8010a214b1088c304aa20a28adc66f83877a9d2
- There are 2 datasets train and test.
- Train dataset has 3 columns named w,x and y
- Test dataset has 2 columns w,x
- W and X are input features and y is target feature
- Has 100 Million rows

### Workflow

#### Loading the data from dataset
- Data is loaded as train_df for training dataset and test_df for testing dataset

#### Training the dataset
- Dataset is trained using the algorithm simple Linear Regression

```
from sklearn.linear_model import LinearRegression

regressor = LinearRegression()
regressor.fit(x_train,y_train)  
```

- Then the outputs are predicted from the test set
  
```
y_test_pred = regressor.predict(x_test)
```

#### Visualising the training set results in 3D
- w variable has a small range of variation (maybe it’s nearly constant)
- The data is constrained by some relation like w = constant.


#### Visualising the testing set results in 3D
- The blue points form a very flat, compressed line near 0 on the y_predicted axis.
- This suggests that model’s predictions (y_predicted) are almost constant or near zero,
regardless of input x or w.

- It is a regression moddel so the relation between x,y and w is y = w*x + b

## Story of this task:
- I read the README.MD file of this task it said we have to implement the Regression algorithm for the given dataset.
- I saw the dataset it was very huge, it took a lot of time to load and download the dataset.(storage as well)
- I saw training set and test set data and got to know that in train set all 3 variables(input+ouput) are there
and in test set only 2 variables(only input) are there.
- Then i got the idea that i should predict the output values for the test set data as well.
- I used Linear Regression algorithm to train the training set and predict output values for the test.
- For the visualisation part i tried to use 2D simple matplotlib.pyplot but it didn't give me output.
- So i switched to 3D and plotted using Axes3D from mpl_toolkits.mplot3d
- One more problem was the dataset was huge that is why i couldn't get proper pattern.
- That is why i decided to only plot first 1000 data points from train set and test set.
  


