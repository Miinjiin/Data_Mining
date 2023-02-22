## 1) Saratoga house prices

We used `SaratogaHouses` data to build the optimal pricing model. We
first separated `SaratogaHouses` data into a training and a testing set,
then used the testing set to assess the model’s out-of-sample
performance.

For our best linear model, we added some interaction variables like
`livingArea:lotSize` `livingArea:fuel` `livingArea:centralAir`
`bedrooms:bathrooms` `heating:fuel`. We compared the RMSEs of the
“medium” model and our model to evaluate the performance.

<table>
<tbody>
<tr class="odd">
<td style="text-align: left;">Medium_model_rmse</td>
</tr>
<tr class="even">
<td style="text-align: left;">62568.339</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Model_made_by_us_rmse</td>
</tr>
<tr class="even">
<td style="text-align: left;">62087.762</td>
</tr>
</tbody>
</table>

Looking at above table, our model does a slightly better job at
achieving lower out-of-sample mean-squared error.

    ## [1] 7

To build the best KNN regression model, we first found the optimal K,
**7**, that produces the lowest RMSE value. This value was used in the
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
<td style="text-align: right;">76718.33</td>
<td style="text-align: right;">75484.76</td>
</tr>
<tr class="even">
<td style="text-align: right;">70881.88</td>
<td style="text-align: right;">63432.97</td>
</tr>
<tr class="odd">
<td style="text-align: right;">67626.21</td>
<td style="text-align: right;">73258.19</td>
</tr>
<tr class="even">
<td style="text-align: right;">70579.89</td>
<td style="text-align: right;">64069.57</td>
</tr>
<tr class="odd">
<td style="text-align: right;">66204.00</td>
<td style="text-align: right;">68681.53</td>
</tr>
<tr class="even">
<td style="text-align: right;">71649.52</td>
<td style="text-align: right;">61938.47</td>
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
<td style="text-align: left;">Mean KNN RMSE</td>
<td style="text-align: right;">69060.09</td>
</tr>
<tr class="even">
<td style="text-align: left;">Mean LM RMSE</td>
<td style="text-align: right;">66033.70</td>
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
<th style="text-align: right;">coefficient</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">(Intercept)</td>
<td style="text-align: right;">-0.84</td>
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
<td style="text-align: right;">0.26</td>
</tr>
<tr class="odd">
<td style="text-align: left;">age</td>
<td style="text-align: right;">-0.02</td>
</tr>
<tr class="even">
<td style="text-align: left;">historypoor</td>
<td style="text-align: right;">-1.18</td>
</tr>
<tr class="odd">
<td style="text-align: left;">historyterrible</td>
<td style="text-align: right;">-1.89</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposeedu</td>
<td style="text-align: right;">0.67</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposegoods/repair</td>
<td style="text-align: right;">0.08</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposenewcar</td>
<td style="text-align: right;">0.70</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposeusedcar</td>
<td style="text-align: right;">-1.16</td>
</tr>
<tr class="even">
<td style="text-align: left;">foreigngerman</td>
<td style="text-align: right;">-1.57</td>
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

Below are the predictions on the testing set, which we will use this to
measure out-of-sample performance.

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
<td style="text-align: right;">8298</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">702</td>
</tr>
</tbody>
</table>

</td>
<td>

<table>
<thead>
<tr class="header">
<th style="text-align: right;">Accuracy(%)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">92.2</td>
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
column? That is because the baseline 1 model never predicted children.

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
<td style="text-align: right;">8197</td>
<td style="text-align: right;">101</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">452</td>
<td style="text-align: right;">250</td>
</tr>
</tbody>
</table>

</td>
<td>

<table>
<thead>
<tr class="header">
<th style="text-align: right;">Accuracy(%)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">93.86</td>
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
<td style="text-align: right;">8203</td>
<td style="text-align: right;">95</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">443</td>
<td style="text-align: right;">259</td>
</tr>
</tbody>
</table>

</td>
<td>

<table>
<thead>
<tr class="header">
<th style="text-align: right;">Accuracy(%)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">94.02</td>
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
<td style="text-align: right;">0.7230803</td>
<td style="text-align: right;">0.9800995</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.6639112</td>
<td style="text-align: right;">0.9701493</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.5984338</td>
<td style="text-align: right;">0.9601990</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.5268653</td>
<td style="text-align: right;">0.9427861</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.4587775</td>
<td style="text-align: right;">0.9303483</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.3976506</td>
<td style="text-align: right;">0.9154229</td>
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
<td style="text-align: right;">18.18843</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="even">
<td style="text-align: right;">2</td>
<td style="text-align: right;">14.43807</td>
<td style="text-align: right;">19</td>
</tr>
<tr class="odd">
<td style="text-align: right;">3</td>
<td style="text-align: right;">15.70845</td>
<td style="text-align: right;">15</td>
</tr>
<tr class="even">
<td style="text-align: right;">4</td>
<td style="text-align: right;">20.05566</td>
<td style="text-align: right;">16</td>
</tr>
<tr class="odd">
<td style="text-align: right;">5</td>
<td style="text-align: right;">16.12218</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="even">
<td style="text-align: right;">6</td>
<td style="text-align: right;">20.93835</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="odd">
<td style="text-align: right;">7</td>
<td style="text-align: right;">17.13298</td>
<td style="text-align: right;">15</td>
</tr>
<tr class="even">
<td style="text-align: right;">8</td>
<td style="text-align: right;">21.89252</td>
<td style="text-align: right;">24</td>
</tr>
<tr class="odd">
<td style="text-align: right;">9</td>
<td style="text-align: right;">18.22775</td>
<td style="text-align: right;">18</td>
</tr>
<tr class="even">
<td style="text-align: right;">10</td>
<td style="text-align: right;">21.41741</td>
<td style="text-align: right;">25</td>
</tr>
<tr class="odd">
<td style="text-align: right;">11</td>
<td style="text-align: right;">18.94795</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="even">
<td style="text-align: right;">12</td>
<td style="text-align: right;">20.63054</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="odd">
<td style="text-align: right;">13</td>
<td style="text-align: right;">21.61132</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="even">
<td style="text-align: right;">14</td>
<td style="text-align: right;">20.33701</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="odd">
<td style="text-align: right;">15</td>
<td style="text-align: right;">23.97456</td>
<td style="text-align: right;">23</td>
</tr>
<tr class="even">
<td style="text-align: right;">16</td>
<td style="text-align: right;">22.36013</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="odd">
<td style="text-align: right;">17</td>
<td style="text-align: right;">18.46943</td>
<td style="text-align: right;">15</td>
</tr>
<tr class="even">
<td style="text-align: right;">18</td>
<td style="text-align: right;">25.95919</td>
<td style="text-align: right;">31</td>
</tr>
<tr class="odd">
<td style="text-align: right;">19</td>
<td style="text-align: right;">22.99509</td>
<td style="text-align: right;">22</td>
</tr>
<tr class="even">
<td style="text-align: right;">20</td>
<td style="text-align: right;">22.59296</td>
<td style="text-align: right;">26</td>
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
