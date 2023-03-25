## 1) What causes what?

**Question 1 Why I can’t just get data from a few different cities and
run the regression of “crime” on “police” to understand how more cops in
the streets affect crime?**

Running regression is not enough to find causation. The number of cops
can’t explain all about the crime rate. There can be other
factors(confounders) affecting the crime rate, for example, drug/alcohol
regulations, access to weapons, the criminal justice system, income
inequality, and population density. Plus, there exist inherent
differences for each city, and there can be a selection bias problem
from collecting different cities in the sample. If there’s a selection
bias problem, we can’t generalize the result of the regression.

**Question 2 How UPenn able to isolate this effect?**

UPenn added instrumental variable ‘High Alert’ and ‘Midday Ridership’.
In a High Alert day, more cops will be on the street and shops and less
people will be in public who can be targeted as victim. If we see the
table, controlling High Alert, total daily crime lowered by 7. Mid day
Ridership is dummy variable controlling METRO ridership. Including Mid
day Ridership, there’s still a negative relationship between high alert
and crime, total daily crime lowered by 6.

**Question 3 Why did they have to control for Metro ridership?**

To get a true effect of police presence on crime rate in D.C., the
researchers decided to control Metro ridership, as adding this IV
variable can control the probability that the crime rate goes up/down
from the fact that more/less people on the street. We can mitigate the
potential biases caused by METRO ridership usage and can obtain clearer
estimate of causal effect of police presence on crime rate.

**Question 4 What was that trying to capture?**

The first column of the table is about linear model using robust
regression with the dependent variable daily total number of crimes in
D.C. Here, on top of two instrumental variables ‘High Alert’ and ‘Midday
ridership’, researchers added ‘District 1’ dummy variable, which
demonstrates that crime happened in the first policy district area.
Interaction term ‘High Alert x District 1’‘s coefficient -2.6
illustrates the differential effect of the high alert on the first
policy district area compared to non-first policy district area. Holding
all else fixed, this interaction variable is associated with 2.6 less
total daily crime. Interaction term ’High Alert x Other Districts’‘s
coefficient -0.57 implies the differential effect of the high alert on
the other districts compared to non-other districts. Holding all else
fixed, this interaction variable is associated with 0.57 less total
daily crime. The coefficient of ’Midday ridership’ means, with the METRO
ridership control, it is expected to have 6 less total daily crime.

## 2) Tree modeling: dengue cases

#### Classification and Regression Trees (CART) to predict dengue cases

After dropping missing values from `dengue.csv`, I created base model
regressing total\_cases for all other variables, and with `rpart()`
function, plotted the result tree. This is un-pruned tree which allows
tree to grow its maximum size, includes all possible splits in the
training data.

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%202.CART.1-1.png)

To perform cross-validation, I used prune function given during the
class and adopted in my base model to evaluate performance.

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%202.CART.2-1.png)

Out-of-sample RMSEs for un-pruned CART and pruned CART is,

    ## [1] 28.8792

    ## [1] 28.28074

Result shows pruned CART gives a little bit higher RMSE compared to
un-pruned CART. This is due to the fact that pruned CART has higher bias
and lower variance as it is less flexible then un-pruned CART.

#### Random Forests to predict dengue cases

I created base model regressing total\_cases for all other variables and
plotted a variable importance plot.

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%202.Random_forest.1-1.png)

Will use this plot later to pick the variable for partial dependence
plot.

Cross validation is not strictly needed for building a random forest
model, as random forest combines multiple decision trees. The randomness
of random forest eliminates need for cross validation.

Out-of-sample RMSEs for random forests is,

    ## [1] 26.58218

#### Gradient Boosted trees to predict dengue cases

After fitting tree for gradient boosted trees model, for cross
validation, I added `cv.folds()` in `gbm` package. I searched common
choice for the number of folds is between 5 and 10, so I chose 8. I
plotted error curve, which is deviance plot.

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%202.Gradient_boosted.1-1.png)

    ## [1] 53

The green line is our cross validated error. The x-axis of error curve
is number of iterations and y-axis of error curve is deviance of the
model, which measures goodness of the fit. The blue dashed line is the
best number of iteration minimizing error.

Out-of-sample RMSEs for Gradient boosted tree is,

    ## [1] 26.79056

##### Checking model performance with out-of-sample RMSEs for each models

<table>
<thead>
<tr>
<th style="text-align:left;">
Model
</th>
<th style="text-align:right;">
RMSE
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Un-pruned Tree
</td>
<td style="text-align:right;">
28.87920
</td>
</tr>
<tr>
<td style="text-align:left;">
Pruned Tree
</td>
<td style="text-align:right;">
28.28074
</td>
</tr>
<tr>
<td style="text-align:left;">
Random Forest
</td>
<td style="text-align:right;">
26.58218
</td>
</tr>
<tr>
<td style="text-align:left;">
Gradient Boosting
</td>
<td style="text-align:right;">
26.79056
</td>
</tr>
</tbody>
</table>

We can check that the Random Forest is the best performance on the
testing data.

#### Partial dependence plots

With selected best performance model, Random Forest, we will plot the
partial dependence plots to isolate the partial effect of specific
features on the outcome. Will make three partial dependence plots about
`specific_humidity`, `precipitation_amt` and our group’s choice
`min_air_temp_k`. This variable was chosen from a variable importance
plot made from Random Forest part.

##### `specific_humidity`

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%202.partial_plots.1-1.png)

##### `precipitation_amt`

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%202.partial_plots.2-1.png)

##### `min_air_temp_k`

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%202.partial_plots.3-1.png)

Plots shows increasing graph, we can interpret this these features has a
positive effect on predicted outcome.

## 3) Predictive model building: green certification

1.  Overview This question attempts to build the best predictive model
    for revenue per square foot per calender year and to use this model
    to possibly quantify the average change in rental income per square
    foot associated with green certification, holding other features of
    the building constant.

2.  Modeling First, I created a new variable called “revenue” by
    multiplying Rent and leasing\_rate Next, I split the data into train
    and test set

We started out by fitting a linear regression model to predict revenue
that included every variable in the data set as predictors.  
We took out Rent and leasing\_rate as they are already taken into
account as revenue. We also chose to take out LEED and Energystar and
collapsed them into a single “green certified” category.

We improved our linear regression model by adding interactions between
Gas\_Costs, Electricity Costs with possible sources of the costs.
Specifically, we figured that gas and electricity costs are associated
with number of heating/cooling degree days, precipitation, city market
rent, stories, age, amenities, renovation status by correlation tests.

We then created a CART model with basic independent variables

Next, we built a pruned tree model

We then drew tree plots for the simple tree model and the pruned tree
model.

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%203.6-1.png)![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%203.6-2.png)

We used random forest and boosting and created more models for
comparison

We tried the random forest model and the gradient-boosted model with the
interactions I used earlier, but the tree models without them give me
the lowest rmse model.

We then drew a variable importance plot of random forest model. The plot
shows that City\_Market\_Rent, Size, and age contribute the most to our
prediction.

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%203.8-1.png)

1.  Conclusion

We fit linear models, tree models, random forests models and boosted
random forests models. As we develop more sophisticated models, we find
that the predictive power of the models get better and better. However,
testing on the test data set, based on the out-of-sample rmse values, we
find that the random forest model perform the best above all.

<table>
<thead>
<tr>
<th style="text-align:left;">
Model
</th>
<th style="text-align:right;">
RMSE
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Linear model
</td>
<td style="text-align:right;">
1202.4009
</td>
</tr>
<tr>
<td style="text-align:left;">
Improved linear model
</td>
<td style="text-align:right;">
1189.5189
</td>
</tr>
<tr>
<td style="text-align:left;">
Tree model
</td>
<td style="text-align:right;">
1119.1228
</td>
</tr>
<tr>
<td style="text-align:left;">
Pruned tree model
</td>
<td style="text-align:right;">
1169.8178
</td>
</tr>
<tr>
<td style="text-align:left;">
Random forest model
</td>
<td style="text-align:right;">
853.0619
</td>
</tr>
<tr>
<td style="text-align:left;">
Boosted model
</td>
<td style="text-align:right;">
860.2004
</td>
</tr>
</tbody>
</table>

## 4) Predictive model building: California housing

#### Report Detailing The Method

To build the best predictive model for `medianhouseValue`, we compared
CART, random forests, and gradient-boosted trees using all of the
available features from the dataset. As one can see from below table
comparing the RMSE of each model, random forest has the best overall
out-of-sample accuracy of our proposed model.

<table>
<thead>
<tr>
<th style="text-align:left;">
Model
</th>
<th style="text-align:right;">
RMSE
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
CART
</td>
<td style="text-align:right;">
69646.40
</td>
</tr>
<tr>
<td style="text-align:left;">
Random Forest
</td>
<td style="text-align:right;">
52600.44
</td>
</tr>
<tr>
<td style="text-align:left;">
Gradient-Boosted Tree
</td>
<td style="text-align:right;">
57416.56
</td>
</tr>
</tbody>
</table>

Next, we plot below three figures, showing the actual median house value
from the original data, predictions and residuals using the model. In
plotting the figures, we first used `ggmap` to import the map of the
state of California. We can see that the actual median values are the
highest around San Francisco and Los Angeles areas, indicated by the
lighter blue colors. Our prediction using random forest is pretty
accurate, and the residuals are small.

**Plot A:**

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%204ggmap-1.png)

**Plot B:**

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%204plot2-1.png)

**Plot C:**

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%204plot3-1.png)
