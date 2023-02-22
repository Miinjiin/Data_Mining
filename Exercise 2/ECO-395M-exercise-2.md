## 1) Saratoga house prices

We used `SaratogaHouses` data to build the optimal pricing model. We
first separated `SaratogaHouses` data into a training and a testing set,
then used the testing set to assess the model’s out-of-sample
performance.

For our best linear model, we added some interaction variables like
`livingArea:lotSize` `livingArea:fuel` `livingArea:centralAir`
`bedrooms:bathrooms` `heating:fuel`. We compared the RMSEs of the
“medium” model and our model to evaluate the performance.

    ## [1] 64587

    ## [1] 63713.48

Looking at above table, our model does a slightly better job at
achieving lower out-of-sample mean-squared error.

    ## [1] 5

To build the best KNN regression model, we first found the optimal K,
**5**, that produces the lowest RMSE value. This value was used in the
“horse race” between the two model classes.

<table>
<thead>
<tr class="header">
<th style="text-align: right;">RMSE_KNN</th>
<th style="text-align: right;">RMSE_LM</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">73791.34</td>
<td style="text-align: right;">77557.02</td>
</tr>
<tr class="even">
<td style="text-align: right;">64679.31</td>
<td style="text-align: right;">63406.89</td>
</tr>
<tr class="odd">
<td style="text-align: right;">68180.97</td>
<td style="text-align: right;">66111.83</td>
</tr>
<tr class="even">
<td style="text-align: right;">67107.56</td>
<td style="text-align: right;">63943.32</td>
</tr>
<tr class="odd">
<td style="text-align: right;">64542.44</td>
<td style="text-align: right;">59111.80</td>
</tr>
<tr class="even">
<td style="text-align: right;">74904.54</td>
<td style="text-align: right;">69320.37</td>
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
<td style="text-align: right;">67724.34</td>
</tr>
<tr class="even">
<td style="text-align: left;">V2</td>
<td style="text-align: right;">65120.30</td>
</tr>
</tbody>
</table>

For the comparison, we ran 150 random train/test splits. First table
shows the first six results, which shows that the RMSE of our model
repeatedly beats that of the KNN model.

Looking at the second table, we can observe that our linear model has
the lower **average** out-of-sample RMSE compared to that of the KNN
model.

**Report on findings:** On top of the “medium” model, we added what we
considered to be meaningful interaction variables like
`livingArea:lotSize` `livingArea:fuel` `livingArea:centralAir`
`bedrooms:bathrooms` and `heating:fuel`. We assumed that the
relationships between the two variables in each interaction were
important in their effect on the housing price. For example, the effect
of the living area size on the house price would be different depending
on whether or not the house has a central air. Number of bedrooms would
affect the house price differently based on how many bathrooms there
are. A house with four bedrooms with four bathrooms would certainly be
priced differently compared to one with four bedrooms and one bathroom!
Our inclusion of such interactions in the model proved to be a good
decision as it out-performed both the “medium” model and the KNN model,
achieving the lowest out-of-sample mean-squared error.

## 2) Classification and retrospective sampling

Likelihood that one will default based on their credit
history(Good,Poor,Terrible).

![](ECO-395M-exercise-2_files/figure-markdown_strict/problem%202.1-1.png)

**Plot 1:** Bar plot showing average default probability by credit
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
<td style="text-align: right;">0.21</td>
</tr>
<tr class="odd">
<td style="text-align: left;">age</td>
<td style="text-align: right;">-0.02</td>
</tr>
<tr class="even">
<td style="text-align: left;">historypoor</td>
<td style="text-align: right;">-1.22</td>
</tr>
<tr class="odd">
<td style="text-align: left;">historyterrible</td>
<td style="text-align: right;">-2.03</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposeedu</td>
<td style="text-align: right;">0.83</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposegoods/repair</td>
<td style="text-align: right;">0.08</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposenewcar</td>
<td style="text-align: right;">1.00</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposeusedcar</td>
<td style="text-align: right;">-0.65</td>
</tr>
<tr class="even">
<td style="text-align: left;">foreigngerman</td>
<td style="text-align: right;">-1.72</td>
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
counter-intuitive,** which made us suspect something was not right.

This data set is not appropriate for predicting “high” vs. “low”
probably of default when screening prospective borrowers. Sampling
defaulted loans and matching similar kinds of loans will inevitably lead
to a biased prediction because the majority of samples collected are
borrowers with poor and terrible credit rating as shown in the table
above. Rather, the bank should use a random selection (and/or a much
larger sample size) when collecting samples to better predict the
probability of defaults.

## 3) Children and hotel reservations

### Model building

Here, we will build a predictive model for whether a hotel booking will
have children on it. We start by splitting train/test data with
`hotels_dev.csv`, and making baseline 1 and baseline 2 models as
instructed.

For the best linear model, we added what we considered to be meaningful
interactions, such as `adults:stays_in_weekend_nights`,
`adults:total_of_special_requests`, `adults:average_daily_rate`, and
`average_daily_rate:total_of_special_request`.

Under is the predictions on the testing set. We will use this to measure
out-of-sample performance.

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
<td style="text-align: right;">8291</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">709</td>
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
<td style="text-align: right;">92.12</td>
</tr>
</tbody>
</table>

</td>
</tr>
</tbody>
</table>

**Table set 1:** Left is a Confusion matrix for baseline 1 model that
used only four features. On its right is the out-of-sample accuracy.

Looking at above confusion matrix, one may ask why is there a missing
column? That is because the baseline 1 model never predicted children!

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
<td style="text-align: right;">8192</td>
<td style="text-align: right;">99</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">449</td>
<td style="text-align: right;">260</td>
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
<td style="text-align: right;">93.91</td>
</tr>
</tbody>
</table>

</td>
</tr>
</tbody>
</table>

**Table set 2:** Left table is Confusion matrix for baseline 2 model
that used all possible predictors except for arrival\_date. On its right
is the out-of-sample accuracy.

One can see that baseline 2 model performs better than base line 1
model.

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
<td style="text-align: right;">8196</td>
<td style="text-align: right;">95</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">455</td>
<td style="text-align: right;">254</td>
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
<td style="text-align: right;">93.89</td>
</tr>
</tbody>
</table>

</td>
</tr>
</tbody>
</table>

**Table set 3:** Left table is Confusion matrix for the best linear
model we made with additional interaction variables. On its right is the
out-of-sample accuracy.

Our model has a slightly higher accuracy than baseline 2 model.

### Model validation : STEP 1

Here, we validate our best model by testing it on an entirely fresh
data, `hotels_val.csv`

<table>
<thead>
<tr class="header">
<th style="text-align: right;">ROC_FPR</th>
<th style="text-align: right;">ROC_TPR</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">0.7206874</td>
<td style="text-align: right;">0.9726368</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.6615184</td>
<td style="text-align: right;">0.9626866</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.5975636</td>
<td style="text-align: right;">0.9552239</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.5281705</td>
<td style="text-align: right;">0.9477612</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.4598651</td>
<td style="text-align: right;">0.9328358</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.3978682</td>
<td style="text-align: right;">0.9054726</td>
</tr>
</tbody>
</table>

To produce an ROC curve plot, we first made a dataframe consisting of
False Positive Rate values and True Positive Rate values for each
threshold t. Above are the first six results using head(df) command.

![](ECO-395M-exercise-2_files/figure-markdown_strict/problem%203.2.1.2-1.png)

**Plot 2:** ROC curve (FPR(t) vs TPR(t)) for our best model, using new
dataset `hotels_val.csv`

While working through the problem, we came across a cool package called
`ROCR`. Just for the kicks, we tried generating the ROC curve again
using this package, which generated a similar curve as above.

![](ECO-395M-exercise-2_files/figure-markdown_strict/problem%203.2.2-1.png)

**Plot 2:** ROC curve (using `ROCR` packcage) showing True Positive Rate
against the False Positive Rate for different threshold t. This took
less time and fewer lines of codes. Simple and fast!

### Model validation : STEP 2

Let’s create 20 folds of `hotels_val.csv`. For each fold set, we have
250 bookings showing expected number of children and actual number of
children.

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
<td style="text-align: right;">21.71688</td>
<td style="text-align: right;">24</td>
</tr>
<tr class="even">
<td style="text-align: right;">2</td>
<td style="text-align: right;">22.22189</td>
<td style="text-align: right;">25</td>
</tr>
<tr class="odd">
<td style="text-align: right;">3</td>
<td style="text-align: right;">22.22248</td>
<td style="text-align: right;">22</td>
</tr>
<tr class="even">
<td style="text-align: right;">4</td>
<td style="text-align: right;">19.93273</td>
<td style="text-align: right;">15</td>
</tr>
<tr class="odd">
<td style="text-align: right;">5</td>
<td style="text-align: right;">17.24118</td>
<td style="text-align: right;">14</td>
</tr>
<tr class="even">
<td style="text-align: right;">6</td>
<td style="text-align: right;">16.67087</td>
<td style="text-align: right;">18</td>
</tr>
<tr class="odd">
<td style="text-align: right;">7</td>
<td style="text-align: right;">19.10248</td>
<td style="text-align: right;">16</td>
</tr>
<tr class="even">
<td style="text-align: right;">8</td>
<td style="text-align: right;">20.20428</td>
<td style="text-align: right;">19</td>
</tr>
<tr class="odd">
<td style="text-align: right;">9</td>
<td style="text-align: right;">17.18119</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="even">
<td style="text-align: right;">10</td>
<td style="text-align: right;">21.03606</td>
<td style="text-align: right;">15</td>
</tr>
<tr class="odd">
<td style="text-align: right;">11</td>
<td style="text-align: right;">18.69588</td>
<td style="text-align: right;">24</td>
</tr>
<tr class="even">
<td style="text-align: right;">12</td>
<td style="text-align: right;">18.58087</td>
<td style="text-align: right;">26</td>
</tr>
<tr class="odd">
<td style="text-align: right;">13</td>
<td style="text-align: right;">21.87252</td>
<td style="text-align: right;">28</td>
</tr>
<tr class="even">
<td style="text-align: right;">14</td>
<td style="text-align: right;">19.72789</td>
<td style="text-align: right;">14</td>
</tr>
<tr class="odd">
<td style="text-align: right;">15</td>
<td style="text-align: right;">22.12965</td>
<td style="text-align: right;">19</td>
</tr>
<tr class="even">
<td style="text-align: right;">16</td>
<td style="text-align: right;">18.65868</td>
<td style="text-align: right;">19</td>
</tr>
<tr class="odd">
<td style="text-align: right;">17</td>
<td style="text-align: right;">21.24928</td>
<td style="text-align: right;">14</td>
</tr>
<tr class="even">
<td style="text-align: right;">18</td>
<td style="text-align: right;">22.03036</td>
<td style="text-align: right;">27</td>
</tr>
<tr class="odd">
<td style="text-align: right;">19</td>
<td style="text-align: right;">22.05579</td>
<td style="text-align: right;">25</td>
</tr>
<tr class="even">
<td style="text-align: right;">20</td>
<td style="text-align: right;">19.46903</td>
<td style="text-align: right;">17</td>
</tr>
</tbody>
</table>

**Table 4:** 20 folds each with expected number of children (left) and
actual number of children (right) for comparison.

![](ECO-395M-exercise-2_files/figure-markdown_strict/problem%203.2.4-1.png)
**Plot 3:** Grouped bar plot showing 20 fold sets comparing expected
number of children and actual number of children (Red=expected,
Green=actual).

As one can clearly see from **Table 4** and **Plot 3**, our model does a
pretty accurate job at predicting the total number of bookings with
children in a group of 250 bookings overall.
