#### Libraries Used<br><br>
[pandas](https://pandas.pydata.org/docs/reference/index.html)<br>
[numpy](https://numpy.org/doc/stable/reference/index.html)<br>
[matplotlib](https://matplotlib.org/stable/api/index)<br>
[seaborn](https://seaborn.pydata.org/api.html)<br>
[sklearn](https://scikit-learn.org/stable/index.html)<br>
[itertools](https://docs.python.org/3/library/itertools.html)<br>
[collections.abc](https://docs.python.org/3/library/collections.abc.html)<br>
[typing](https://docs.python.org/3/library/typing.html)<br>
<br><br>
#### Solution Explanation
<br><br>
The dataset that was given was non-numeric. So, the first thing that needed to be resolved was mapping all
non-numeric values into distinct numerical identifiers for each column. The most practical way I saw this
being resolved was to create a mapping for each individual column based on the amount of elements in the set.<br><br>

Once the numerical conversion was handled, the next step was to determine the independent and dependent variables(s).
Identifying the independent and dependent variables was made simple, since the prompt was to
try to train a model to predict whether a mushroom was poisonous or edible, as governed by the actual data in the 'class' column.
So, I considered the class as the only dependent variable and all other features as independent.<br><br>

With this, I plotted all dependent variables individually against the independent variable using matplotlib,
to see if a trend could be got by visualization. I saw that aside from a few graphs, a logistic function seemed to fit the plot;
and if the points' coordinates were inverted, the logit function would fit. Both of these fell under a logistic regression
ideal. So, I went with that model.<br><br>

To train the model, I chose an 80%-20% split between train data and test data and used sklearn to train_test_split the numerical
data to do so. With the training data intact, I trained a model a single time with 80% of the data, and tested against the other
20% (independent variables), then compared it to the actual dependent results of that 20% using a confusion matrix.
It came out to about **92%** accuracy in terms of the model correctly predicting whether a mushroom was edible or not.<br><br>

Next I analyzed the failures of that training session. How many of the failures were attributed to the worser scenario
of the model predicting a mushroom was edible when it was poisonous, versus predicting a mushroom was poisonous when it was
edible? Thankfully, majority of the failures were attributed to the latter scenario.<br><br>

To ensure the accuracy model, I re-trained the model 50, 100, and 500 times. Each time randomly sampling 80% of the data once more
and calculating the accuracy score after training. Then by taking the average between the accuracy scores gathered in a given trial
set, I found that there was very little ambiguity between training the model 1, 50, 100, or 500 times. All accuracy scores hovered
around the same **92%**.<br><br>
