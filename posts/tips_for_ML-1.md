This is a page where i will be putting in things i learned while starting off again in ML.  
I am using scikit-learn to do my ml this time and am trying to go through ML in as small a timeframe as possible.
I have been learning about linear and logistic regression.
The correct ones to use in both the cases are `from sklearn.linear_model    import LinearRegression` and `from sklearn.linear_model import LogisticRegression` which is intiutive.
This is the bit of code that matters
```python
linreg = LinearRegression().fit( X_train , y_train )
linreg.score( X_test , y_test )
```
and 
```python
logreg = LogisticRegression( solver='liblinear',multi_class='ovr',n_jobs=1 )
logreg.fit(X_train, y_train)
```
Post this, we can do a predict and see how the model behaves.

Have a look at this repo to see what i did using the above data.
https://github.com/pankymathur/simple-linear-regression-using-python-only this uses the diabetics set but only the BMI to calculate the blood sugar level.
https://www.kaggle.com/pmarcelino/data-analysis-and-feature-extraction-with-python/notebook - this uses the titanic dataset.

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4MTA5OTM0MzAsLTE5NjUxMzY3ODksNj
U3OTgzODc0XX0=
-->