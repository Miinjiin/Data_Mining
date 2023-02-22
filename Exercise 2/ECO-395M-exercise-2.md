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

    ## [1] 75884.96

    ## [1] 73112.16

Top one is the RMSE is for the “medium\_model” from class, while below
is the RMSE of the best linear model we made. Our model does a slightly
better job at achieving lower out-of-sample mean-squared error.

    ## [1] 6

To build the best KNN regression model, we first found the optimal K
that produces the lowest RMSE value is `best_k`. This value was used in
the “horse race” between the two model classes.

<table>
<thead>
<tr class="header">
<th style="text-align: right;">RMSE_KNN</th>
<th style="text-align: right;">RMSE_LM</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">73452.58</td>
<td style="text-align: right;">64079.39</td>
</tr>
<tr class="even">
<td style="text-align: right;">68756.83</td>
<td style="text-align: right;">65203.82</td>
</tr>
<tr class="odd">
<td style="text-align: right;">69118.02</td>
<td style="text-align: right;">66799.08</td>
</tr>
<tr class="even">
<td style="text-align: right;">63103.13</td>
<td style="text-align: right;">58444.00</td>
</tr>
<tr class="odd">
<td style="text-align: right;">72802.88</td>
<td style="text-align: right;">63724.80</td>
</tr>
<tr class="even">
<td style="text-align: right;">67973.02</td>
<td style="text-align: right;">67352.36</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th style="text-align: left;"></th>
<th style="text-align: right;">x</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">V1</td>
<td style="text-align: right;">68380.92</td>
</tr>
<tr class="even">
<td style="text-align: left;">V2</td>
<td style="text-align: right;">65365.52</td>
</tr>
</tbody>
</table>

After running 150 random train/test splits, we can observe that our
linear model has the lower average out-of-sample RMSE compared to that
of the KNN model.

**Report on findings:** On top of the “medium” model, we added what we
considred to be meaningful interaction variables like
`livingArea:lotSize` `livingArea:fuel` `livingArea:centralAir`
`bedrooms:bathrooms` and `heating:fuel`. We assumed that the
relationship between the two variables in each interaction were
important in their effect on the housing price. For example, the effect
of the living area size on the house price would be different depending
on whether or not the house has a central air. Number of bedrooms would
affect the house price differently based on how many bathrooms there
are. A house with Four bedrooms with four bathrooms would certainly be
priced differently compared to one with four bedrooms and one bathroom!
Our inclusion of such interactions in the model proved to be a good
decision as it out-performed both the “medium” model and the KNN model,
achieving the lowest out-of-sample mean-squared error.

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
<td style="text-align: right;">-0.76</td>
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
<td style="text-align: right;">0.25</td>
</tr>
<tr class="odd">
<td style="text-align: left;">age</td>
<td style="text-align: right;">-0.02</td>
</tr>
<tr class="even">
<td style="text-align: left;">historypoor</td>
<td style="text-align: right;">-0.94</td>
</tr>
<tr class="odd">
<td style="text-align: left;">historyterrible</td>
<td style="text-align: right;">-1.72</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposeedu</td>
<td style="text-align: right;">0.45</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposegoods/repair</td>
<td style="text-align: right;">-0.03</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposenewcar</td>
<td style="text-align: right;">0.62</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposeusedcar</td>
<td style="text-align: right;">-1.45</td>
</tr>
<tr class="even">
<td style="text-align: left;">foreigngerman</td>
<td style="text-align: right;">-1.08</td>
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
borrowers with poor and terrible credit rating as shown above. Rather,
the bank should use a random selection when collecting samples to better
predict the probability of defaults.

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
<td style="text-align: right;">8303</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">697</td>
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
<td style="text-align: right;">92.26</td>
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
<td style="text-align: right;">8171</td>
<td style="text-align: right;">132</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">428</td>
<td style="text-align: right;">269</td>
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
<td style="text-align: right;">93.78</td>
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
<td style="text-align: right;">8175</td>
<td style="text-align: right;">128</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">428</td>
<td style="text-align: right;">269</td>
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
<td style="text-align: right;">93.82</td>
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
<td style="text-align: right;">0.7169893</td>
<td style="text-align: right;">0.9776119</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.6619534</td>
<td style="text-align: right;">0.9651741</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.5973461</td>
<td style="text-align: right;">0.9552239</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.5362193</td>
<td style="text-align: right;">0.9427861</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.4605177</td>
<td style="text-align: right;">0.9303483</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.3998260</td>
<td style="text-align: right;">0.9054726</td>
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
<td style="text-align: right;">29.49568</td>
<td style="text-align: right;">39</td>
</tr>
<tr class="even">
<td style="text-align: right;">2</td>
<td style="text-align: right;">22.10430</td>
<td style="text-align: right;">19</td>
</tr>
<tr class="odd">
<td style="text-align: right;">3</td>
<td style="text-align: right;">23.40812</td>
<td style="text-align: right;">23</td>
</tr>
<tr class="even">
<td style="text-align: right;">4</td>
<td style="text-align: right;">21.19100</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="odd">
<td style="text-align: right;">5</td>
<td style="text-align: right;">21.36449</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="even">
<td style="text-align: right;">6</td>
<td style="text-align: right;">21.34957</td>
<td style="text-align: right;">25</td>
</tr>
<tr class="odd">
<td style="text-align: right;">7</td>
<td style="text-align: right;">20.16118</td>
<td style="text-align: right;">18</td>
</tr>
<tr class="even">
<td style="text-align: right;">8</td>
<td style="text-align: right;">23.03348</td>
<td style="text-align: right;">27</td>
</tr>
<tr class="odd">
<td style="text-align: right;">9</td>
<td style="text-align: right;">18.86738</td>
<td style="text-align: right;">18</td>
</tr>
<tr class="even">
<td style="text-align: right;">10</td>
<td style="text-align: right;">21.10968</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="odd">
<td style="text-align: right;">11</td>
<td style="text-align: right;">19.86514</td>
<td style="text-align: right;">15</td>
</tr>
<tr class="even">
<td style="text-align: right;">12</td>
<td style="text-align: right;">16.32529</td>
<td style="text-align: right;">12</td>
</tr>
<tr class="odd">
<td style="text-align: right;">13</td>
<td style="text-align: right;">19.08155</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="even">
<td style="text-align: right;">14</td>
<td style="text-align: right;">21.31933</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="odd">
<td style="text-align: right;">15</td>
<td style="text-align: right;">17.38988</td>
<td style="text-align: right;">15</td>
</tr>
<tr class="even">
<td style="text-align: right;">16</td>
<td style="text-align: right;">21.32542</td>
<td style="text-align: right;">29</td>
</tr>
<tr class="odd">
<td style="text-align: right;">17</td>
<td style="text-align: right;">20.02768</td>
<td style="text-align: right;">18</td>
</tr>
<tr class="even">
<td style="text-align: right;">18</td>
<td style="text-align: right;">17.81370</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="odd">
<td style="text-align: right;">19</td>
<td style="text-align: right;">14.37723</td>
<td style="text-align: right;">18</td>
</tr>
<tr class="even">
<td style="text-align: right;">20</td>
<td style="text-align: right;">12.38989</td>
<td style="text-align: right;">12</td>
</tr>
</tbody>
</table>

![](ECO-395M-exercise-2_files/figure-markdown_strict/problem%203.2.4-1.png)
**Figure 1:** Generated 20 folds having information of expected number
of bookings with children and actual number of bookings with children.
(Red=expected, Green=actual)
