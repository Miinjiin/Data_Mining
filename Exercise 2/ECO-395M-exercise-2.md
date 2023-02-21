## 1) Saratoga house prices

\*\* Between linear model and K-nearest-neighbor regression model, which
one is better at achieving lower out-of-sample mean-squared error? \*\*

We will use `SaratogaHouses` data to build optimal pricing model.
Separating data from SaratogaHouses data into a training set and testing
set, and will use testing set for assessing model’s out-of-sample
performance.

First of all, we made the best linear model for price by adding some
meaningful interaction variables like `livingArea:lotSize`
`livingArea:fuel` `livingArea:centralAir` `bedrooms:bathrooms`
`heating:fuel` To evaluate the model performance we making, we compared
the rmse of the model with the medium model.

    ## [1] 62075.44

    ## [1] 60675.85

Top one is rmse is for medium\_rmse, below one is rmse for model we
made. Our model seems to do better at achieving lower out-ot-sample
mean-squared error.

    ## [1] 25

After running the RMSE for different levels of K, we found that
consistently one of the lowest estimators for Price given our KNN
estimate is K=15. We will use K=10 as our value in the bakeoff against
the the linear model.

## 2) Classification and retrospective sampling

Likelihood that one will default based on their credit
history(Good,Poor,Terrible).

![](ECO-395M-exercise-2_files/figure-markdown_strict/problem%202.1-1.png)

**Figure 1:** Bar plot showing average default probability by credit
history.

<table class="kable_wrapper">
<tbody>
<tr>
<td>

<table>
<thead>
<tr class="header">
<th style="text-align: left;"></th>
<th style="text-align: right;">.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">(Intercept)</td>
<td style="text-align: right;">-0.43</td>
</tr>
<tr class="even">
<td style="text-align: left;">duration</td>
<td style="text-align: right;">0.03</td>
</tr>
<tr class="odd">
<td style="text-align: left;">amount</td>
<td style="text-align: right;">0.00</td>
</tr>
<tr class="even">
<td style="text-align: left;">installment</td>
<td style="text-align: right;">0.20</td>
</tr>
<tr class="odd">
<td style="text-align: left;">age</td>
<td style="text-align: right;">-0.02</td>
</tr>
<tr class="even">
<td style="text-align: left;">historypoor</td>
<td style="text-align: right;">-1.27</td>
</tr>
<tr class="odd">
<td style="text-align: left;">historyterrible</td>
<td style="text-align: right;">-1.96</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposeedu</td>
<td style="text-align: right;">0.51</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposegoods/repair</td>
<td style="text-align: right;">0.09</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposenewcar</td>
<td style="text-align: right;">0.89</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposeusedcar</td>
<td style="text-align: right;">-0.74</td>
</tr>
<tr class="even">
<td style="text-align: left;">foreigngerman</td>
<td style="text-align: right;">-1.03</td>
</tr>
</tbody>
</table>

</td>
<td>

<table>
<thead>
<tr class="header">
<th style="text-align: left;">history</th>
<th style="text-align: right;">count</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">good</td>
<td style="text-align: right;">89</td>
</tr>
<tr class="even">
<td style="text-align: left;">poor</td>
<td style="text-align: right;">618</td>
</tr>
<tr class="odd">
<td style="text-align: left;">terrible</td>
<td style="text-align: right;">293</td>
</tr>
</tbody>
</table>

</td>
</tr>
</tbody>
</table>

The bar plot shows that a borrower with a ‘good’ credit rating history
has the highest probability of defaulting on a loan, followed by ‘poor,’
and ‘terrible.’ Similar result is again found in the logistic regression
model, which shows that ‘historyterrible’ and ‘historybad’ are more
negatively correlated with ‘Default,’ than the intercept (historygood).
Both results indicate that a borrower with a good credit history is more
likely to default on his/her loan, which is **highly
counter-intuitive.**

This data set is not appropriate for predicting “high” vs. “low”
probably of default when screening prospective borrowers. Sampling
defaulted loans and matching similar kinds of loans will inevitably lead
to a biased prediction because the majority of samples collected are
borrowers with poor and terrible credit rating **as shown above.**
Rather, the bank should use a random selection when collecting samples
to better predict the probability of defaults.

## 3) Children and hotel reservations

### Model building

We will build predictive model for whether a hotel booking will have
children on it.

Starting by spliting train/test data with `hotels_dev.csv`, and making
baseline 1 and baseline 2 with the requirements given.

For best linear model, we added some meaningful interaction variables.

Under is the predictions on the testing set. We will use this to measure
out-of-sample performance.

**Table1:** Left table is Confusion matrix for baseline 1 model, a small
model that used only four features. Right table is Percentage of
out-of-sample correct classifications.

<table class="kable_wrapper">
<tbody>
<tr>
<td>

<table>
<thead>
<tr class="header">
<th style="text-align: left;"></th>
<th style="text-align: right;">0</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">0</td>
<td style="text-align: right;">8223</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">777</td>
</tr>
</tbody>
</table>

</td>
<td>

<table>
<thead>
<tr class="header">
<th style="text-align: right;">x</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">91.37</td>
</tr>
</tbody>
</table>

</td>
</tr>
</tbody>
</table>

We can check it never predicted children.

**Table2:** Left table is Confusion matrix for baseline 2 model, a big
model that used all possible predictors expect arrival\_date. Right
table is Percentage of out-of-sample correct classifications

<table class="kable_wrapper">
<tbody>
<tr>
<td>

<table>
<thead>
<tr class="header">
<th style="text-align: left;"></th>
<th style="text-align: right;">0</th>
<th style="text-align: right;">1</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">0</td>
<td style="text-align: right;">8121</td>
<td style="text-align: right;">102</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">506</td>
<td style="text-align: right;">271</td>
</tr>
</tbody>
</table>

</td>
<td>

<table>
<thead>
<tr class="header">
<th style="text-align: right;">x</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">93.24</td>
</tr>
</tbody>
</table>

</td>
</tr>
</tbody>
</table>

Having better result than baseline 1 model

**Table3:** Left table is Confusion matrix for best linear model we
made, adding meaningful interaction variables. Right table is Percentage
of out-of-sample correct classifications.

<table class="kable_wrapper">
<tbody>
<tr>
<td>

<table>
<thead>
<tr class="header">
<th style="text-align: left;"></th>
<th style="text-align: right;">0</th>
<th style="text-align: right;">1</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">0</td>
<td style="text-align: right;">8124</td>
<td style="text-align: right;">99</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">510</td>
<td style="text-align: right;">267</td>
</tr>
</tbody>
</table>

</td>
<td>

<table>
<thead>
<tr class="header">
<th style="text-align: right;">x</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">93.23</td>
</tr>
</tbody>
</table>

</td>
</tr>
</tbody>
</table>

Model we made has slightly higher result to baseline 2 model

### Model validation : STEP 1

Validating the model by testing with entirely fresh data,
`hotels_val.csv`

<table>
<thead>
<tr class="header">
<th style="text-align: right;">ROC_FPR</th>
<th style="text-align: right;">ROC_TPR</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">0.7152491</td>
<td style="text-align: right;">0.9751244</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.6591255</td>
<td style="text-align: right;">0.9651741</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.5927779</td>
<td style="text-align: right;">0.9527363</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.5220796</td>
<td style="text-align: right;">0.9427861</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.4511638</td>
<td style="text-align: right;">0.9278607</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.3824233</td>
<td style="text-align: right;">0.9079602</td>
</tr>
</tbody>
</table>

To make ROC curve plot, we made a dataframe for False Positive Rate
value and True Postive Rate value for each threshold t (shows only parts
of the rows with head(df))

![](ECO-395M-exercise-2_files/figure-markdown_strict/problem%203.2.1.2-1.png)

**Figure 1:** ROC curve(TPR(t)vsFPR(t)) for our best model, using new
dataset `hotels_val.csv`

We tried generating ROC with R package `ROCR`
![](ECO-395M-exercise-2_files/figure-markdown_strict/problem%203.2.2-1.png)

**Figure 2:** Using ROCR package, plot shows True Positive Rate against
the False Postive Rate for different threshold t. This took less time!
Simple and Fast!

### Model validation : STEP 2

Let’s create 20 folds of `hotels_val.csv`. For each fold set, we will
have 250 bookings and will get expected number of childrens and actual
number of childrens. Will compare this expected vs actual number of
children.

**Table 1:** Generated 20 folds each having information of expected
number of bookings with children and actual number of bookings with
children

<table>
<thead>
<tr class="header">
<th style="text-align: right;">fold</th>
<th style="text-align: right;">expected_child</th>
<th style="text-align: right;">actual_child</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">1</td>
<td style="text-align: right;">20.16261</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="even">
<td style="text-align: right;">2</td>
<td style="text-align: right;">19.16444</td>
<td style="text-align: right;">14</td>
</tr>
<tr class="odd">
<td style="text-align: right;">3</td>
<td style="text-align: right;">22.51007</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="even">
<td style="text-align: right;">4</td>
<td style="text-align: right;">20.89343</td>
<td style="text-align: right;">22</td>
</tr>
<tr class="odd">
<td style="text-align: right;">5</td>
<td style="text-align: right;">25.01210</td>
<td style="text-align: right;">33</td>
</tr>
<tr class="even">
<td style="text-align: right;">6</td>
<td style="text-align: right;">17.80914</td>
<td style="text-align: right;">16</td>
</tr>
<tr class="odd">
<td style="text-align: right;">7</td>
<td style="text-align: right;">19.74355</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="even">
<td style="text-align: right;">8</td>
<td style="text-align: right;">21.60908</td>
<td style="text-align: right;">22</td>
</tr>
<tr class="odd">
<td style="text-align: right;">9</td>
<td style="text-align: right;">16.50885</td>
<td style="text-align: right;">14</td>
</tr>
<tr class="even">
<td style="text-align: right;">10</td>
<td style="text-align: right;">20.55729</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="odd">
<td style="text-align: right;">11</td>
<td style="text-align: right;">22.24002</td>
<td style="text-align: right;">25</td>
</tr>
<tr class="even">
<td style="text-align: right;">12</td>
<td style="text-align: right;">17.79279</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="odd">
<td style="text-align: right;">13</td>
<td style="text-align: right;">20.24186</td>
<td style="text-align: right;">19</td>
</tr>
<tr class="even">
<td style="text-align: right;">14</td>
<td style="text-align: right;">23.78311</td>
<td style="text-align: right;">23</td>
</tr>
<tr class="odd">
<td style="text-align: right;">15</td>
<td style="text-align: right;">18.50537</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="even">
<td style="text-align: right;">16</td>
<td style="text-align: right;">16.03320</td>
<td style="text-align: right;">15</td>
</tr>
<tr class="odd">
<td style="text-align: right;">17</td>
<td style="text-align: right;">19.34155</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="even">
<td style="text-align: right;">18</td>
<td style="text-align: right;">17.87163</td>
<td style="text-align: right;">13</td>
</tr>
<tr class="odd">
<td style="text-align: right;">19</td>
<td style="text-align: right;">22.00828</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="even">
<td style="text-align: right;">20</td>
<td style="text-align: right;">20.21167</td>
<td style="text-align: right;">25</td>
</tr>
</tbody>
</table>

![](ECO-395M-exercise-2_files/figure-markdown_strict/problem%203.2.4-1.png)
**Figure 1:** Generated 20 folds having information of expected number
of bookings with children and actual number of bookings with children.
(Red=expected, Green=actual)
