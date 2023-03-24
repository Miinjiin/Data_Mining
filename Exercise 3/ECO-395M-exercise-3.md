## 1) What causes what?

\*\* Question 1 \*\* Why I can’t just get data from a few different
cities and run the regression of “crime” on “police” to understand how
more cops in the streets affect crime?

Running regression is not enough to find causation. The number of cops
can’t explain all about the crime rate. There can be other
factors(confounders) affecting the crime rate, for example, drug/alcohol
regulations, access to weapons, the criminal justice system, income
inequality, and population density. Plus, there exist inherent
differences for each city, and there can be a selection bias problem
from collecting different cities in the sample. If there’s a selection
bias problem, we can’t generalize the result of the regression.

\*\* Question 2 \*\* How UPenn able to isolate this effect?

UPenn added instrumental variable ‘High Alert’ and ‘Midday Ridership’.
In a High Alert day, more cops will be on the street and shops and less
people will be in public who can be targeted as victim. If we see the
table, controlling High Alert, total daily crime lowered by 7. Mid day
Ridership is dummy variable controlling METRO ridership. Including Mid
day Ridership, there’s still a negative relationship between high alert
and crime, total daily crime lowered by 6.

\*\* Question 3 \*\* Why did they have to control for Metro ridership?

To get a true effect of police presence on crime rate in D.C., the
researchers decided to control Metro ridership, as adding this IV
variable can control the probability that the crime rate goes up/down
from the fact that more/less people on the street. We can mitigate the
potential biases caused by METRO ridership usage and can obtain clearer
estimate of causal effect of police presence on crime rate.

\*\* Question 4 \*\* What was that trying to capture?

The first column of the table is about linear model using robust
regression with dependent variable daily total number of crimes in D.C.
Here, on top of two instrumental variable ‘High Alert’ and ‘Midday
ridership’, researchers added ‘District 1’ dummy variable, which
demonstrates that crime happened in the first policy district area.
Interaction term ‘High Alert x District 1’‘s coefficient -2.6
illustrates the differential effect of the high alert on the first
policy district area compared to non-fist policy district area. Holding
all else fixed, this interaction variable is associated with 2.6 less
total daily crime. Interaction term ’High Alert x Other Districts’‘s
coefficient -0.57 implies the differential effect of the high alert on
the other disticts compared to non-other districts. Holding all else
fixed, this interaction variable is associated with 0.57 less total
daily crime. The coefficient of ’Midday ridership’ means, with the METRO
ridership control, it is expected have 6 less total daily crime.

## 2) Tree modeling: dengue cases

\*\* Classification and Regression Trees (CART) to predict dengue cases
\*\*

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%202.CART.1-1.png)

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%202.CART.2-1.png)

\*\* RMSE value for CART \*\*

    ## [1] 28.69914

    ## [1] 29.24436

\*\* Random Forests to predict dengue cases \*\*

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%202.Random_forest.1-1.png)![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%202.Random_forest.1-2.png)

    ## [1] 29.66747

\*\* Gradient Boosted trees to predict dengue cases \*\*

    ## Distribution not specified, assuming gaussian ...

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%202.Gradient_boosted.1-1.png)![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%202.Gradient_boosted.1-2.png)

    ## [1] 39
    ## attr(,"smoother")
    ## Call:
    ## loess(formula = object$oobag.improve ~ x, enp.target = min(max(4, 
    ##     length(x)/10), 50))
    ## 
    ## Number of Observations: 500 
    ## Equivalent Number of Parameters: 39.85 
    ## Residual Standard Error: 0.7734

    ## [1] 30.7305

<table>
<caption>Result RMSE for each model</caption>
<tbody>
<tr class="odd">
<td style="text-align: left;">Tree</td>
<td style="text-align: right;">28.69914</td>
</tr>
<tr class="even">
<td style="text-align: left;">Pruned Tree</td>
<td style="text-align: right;">29.24436</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Random Forest</td>
<td style="text-align: right;">29.66747</td>
</tr>
<tr class="even">
<td style="text-align: left;">Gradient Boosting</td>
<td style="text-align: right;">30.73050</td>
</tr>
</tbody>
</table>

Result RMSE for each model

We can check that the Random Forest is the best performance on the
testing data.

\*\* Partial dependence plots \*\*

With selected best performance model, Random Forest, we will plot the
partial dependence plots to isolate the partial effect of specific
features on the outcome. Will make four partial dependence plots about
`specific_humidity`, `precipitation_amt` and our group’s choices
`min_air_temp_k` and `tdtr_k`. These were chosen from a variable
importance plot made from Random Forest part.

\*\* specific\_humidity \*\*
![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%202.partial_plots.1-1.png)

\*\* precipitation\_amt \*\*
![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%202.partial_plots.2-1.png)

\*\* min\_air\_temp\_k and tdtr\_k \*\*
![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%202.partial_plots.3-1.png)![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%202.partial_plots.3-2.png)

## 3) Predictive model building: green certification

First, I created a new variable called “revenue” by multiplying Rent and
leasing\_rate Next, I split the data into train and test set

I then started out with linear models on green\_train dataset We took
out Rent and leasing\_rate as they are already taken into account. We
also chose to take out LEED and Energystar and collapsed them into a
single “green certified” category.

I improved my linear regression by adding interactions between
Gas\_Costs, Electricity Costs with possible sources of the costs.

We then created a tree model with basic independent variables

Next, we built a pruned tree model

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%203.6-1.png)![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%203.6-2.png)

We then drew tree plots for the simple tree model and the pruned tree
model.

    ## Distribution not specified, assuming gaussian ...

We used random forest and boosting and created more models for
comparison

I tried the random forest model and the boosted model with the
interactions I used earlier, but the tree models without them give me
the lowest rmse model.

<table>
<thead>
<tr class="header">
<th style="text-align: left;">Model</th>
<th style="text-align: right;">RMSE</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">Linear model</td>
<td style="text-align: right;">986.5210</td>
</tr>
<tr class="even">
<td style="text-align: left;">Improved linear model</td>
<td style="text-align: right;">982.4042</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Tree model</td>
<td style="text-align: right;">995.6774</td>
</tr>
<tr class="even">
<td style="text-align: left;">Pruned tree model</td>
<td style="text-align: right;">1015.1652</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Random forest model</td>
<td style="text-align: right;">715.2350</td>
</tr>
<tr class="even">
<td style="text-align: left;">Boosted model</td>
<td style="text-align: right;">868.8011</td>
</tr>
</tbody>
</table>

Ranking the models from the lowest rmse to highest rmse, Random forest
model &gt; Boosted model &gt; Pruned tree model ~ Tree model &gt;
Improved linear model &gt; Linear model

## 4) Predictive model building: California housing

    ## Distribution not specified, assuming gaussian ...

    ## [1] 68462.16

    ## [1] 53186.71

    ## [1] 58374.96

<table>
<thead>
<tr class="header">
<th style="text-align: left;">Model</th>
<th style="text-align: right;">RMSE</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">CART</td>
<td style="text-align: right;">68462.16</td>
</tr>
<tr class="even">
<td style="text-align: left;">Random Forest</td>
<td style="text-align: right;">53186.71</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Gradient-Boosted Tree</td>
<td style="text-align: right;">58374.96</td>
</tr>
</tbody>
</table>

![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%204ggmap-1.png)![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%204ggmap-2.png)![](ECO-395M-exercise-3_files/figure-markdown_strict/problem%204ggmap-3.png)
