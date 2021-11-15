# Linear Regressions

## How to Run Linear Regression in Python

- you can do linear regression using numpy, scipy, stats model and sckit learn.
- Scikit-learn is a powerful Python module for machine learning.
- Scikit has functions for regression, classification, clustering, model selection and dimensionality reduction.
- Imports:
	```
	Import scipy.stats as stats 
	Import sklearn
	```
- convert boston.data into a pandas data frame:
	```
	bos = pd.DataFrame(boston.data)  
	bos.head()
	```
- Import linear regression:
	```
	From sklearn.linear_model import LinearRegression
	```
- Type LinearRegression and the press <tab> key to get a list of functions available inside linear regression object.
	
- Some important functions when fitting linear regression model:
	```
	lm.fit() -> fits a linear model
	lm.predict() -> Predict Y using the linear model with estimated coefficients
	lm.score() -> Returns the coefficient of determination (R^2). A measure of how well observed outcomes are replicated by the model, as the proportion of total variation of outcomes explained by the model.
	```
- Create a scatter plot: plt.scatter(X, Y)
- Scikit learn provides a function called train_test_split:  divide your data sets randomly. 
- Residual plots are a good way to visualize the errors in your data