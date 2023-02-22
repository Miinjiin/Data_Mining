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
<td style="text-align: left;">76996.377</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Model_made_by_us_rmse</td>
</tr>
<tr class="even">
<td style="text-align: left;">75022.251</td>
</tr>
</tbody>
</table>

Looking at above table, our model does a slightly better job at
achieving lower out-of-sample mean-squared error.

    ## [1] 4

To build the best KNN regression model, we first found the optimal K,
**4**, that produces the lowest RMSE value. This value was used in the
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
<td style="text-align: right;">67657.87</td>
<td style="text-align: right;">64848.56</td>
</tr>
<tr class="even">
<td style="text-align: right;">61499.29</td>
<td style="text-align: right;">62872.17</td>
</tr>
<tr class="odd">
<td style="text-align: right;">66329.25</td>
<td style="text-align: right;">61534.70</td>
</tr>
<tr class="even">
<td style="text-align: right;">71519.28</td>
<td style="text-align: right;">69994.61</td>
</tr>
<tr class="odd">
<td style="text-align: right;">68828.88</td>
<td style="text-align: right;">65332.58</td>
</tr>
<tr class="even">
<td style="text-align: right;">76961.07</td>
<td style="text-align: right;">74182.33</td>
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
<td style="text-align: right;">68475.35</td>
</tr>
<tr class="even">
<td style="text-align: left;">Mean LM RMSE</td>
<td style="text-align: right;">65370.04</td>
</tr>
</tbody>
</table>

For the comparison, we ran 150 random train/test splits. First table
shows the first six results, which shows that the RMSE of our model
beats that of the KNN model overall.

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
<td style="text-align: right;">-1.03</td>
</tr>
<tr class="even">
<td style="text-align: left;">duration</td>
<td style="text-align: right;">0.02</td>
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
<td style="text-align: right;">-1.05</td>
</tr>
<tr class="odd">
<td style="text-align: left;">historyterrible</td>
<td style="text-align: right;">-1.98</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposeedu</td>
<td style="text-align: right;">0.74</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposegoods/repair</td>
<td style="text-align: right;">0.23</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposenewcar</td>
<td style="text-align: right;">1.03</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposeusedcar</td>
<td style="text-align: right;">-0.37</td>
</tr>
<tr class="even">
<td style="text-align: left;">foreigngerman</td>
<td style="text-align: right;">-1.15</td>
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
<td style="text-align: right;">8274</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">726</td>
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
<td style="text-align: right;">91.93</td>
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
<td style="text-align: right;">8166</td>
<td style="text-align: right;">108</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">458</td>
<td style="text-align: right;">268</td>
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
<td style="text-align: right;">93.71</td>
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
<td style="text-align: right;">8170</td>
<td style="text-align: right;">104</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">460</td>
<td style="text-align: right;">266</td>
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
<td style="text-align: right;">93.73</td>
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
<td style="text-align: right;">0.7130737</td>
<td style="text-align: right;">0.9726368</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.6586905</td>
<td style="text-align: right;">0.9651741</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.5973461</td>
<td style="text-align: right;">0.9502488</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.5251251</td>
<td style="text-align: right;">0.9427861</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.4624755</td>
<td style="text-align: right;">0.9278607</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.3952578</td>
<td style="text-align: right;">0.9129353</td>
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
<td style="text-align: right;">20.48039</td>
<td style="text-align: right;">14</td>
</tr>
<tr class="even">
<td style="text-align: right;">2</td>
<td style="text-align: right;">19.31813</td>
<td style="text-align: right;">23</td>
</tr>
<tr class="odd">
<td style="text-align: right;">3</td>
<td style="text-align: right;">15.60131</td>
<td style="text-align: right;">14</td>
</tr>
<tr class="even">
<td style="text-align: right;">4</td>
<td style="text-align: right;">21.34025</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="odd">
<td style="text-align: right;">5</td>
<td style="text-align: right;">20.34982</td>
<td style="text-align: right;">27</td>
</tr>
<tr class="even">
<td style="text-align: right;">6</td>
<td style="text-align: right;">22.09317</td>
<td style="text-align: right;">23</td>
</tr>
<tr class="odd">
<td style="text-align: right;">7</td>
<td style="text-align: right;">18.00993</td>
<td style="text-align: right;">8</td>
</tr>
<tr class="even">
<td style="text-align: right;">8</td>
<td style="text-align: right;">18.35076</td>
<td style="text-align: right;">27</td>
</tr>
<tr class="odd">
<td style="text-align: right;">9</td>
<td style="text-align: right;">20.59454</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="even">
<td style="text-align: right;">10</td>
<td style="text-align: right;">19.14296</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="odd">
<td style="text-align: right;">11</td>
<td style="text-align: right;">21.91410</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="even">
<td style="text-align: right;">12</td>
<td style="text-align: right;">22.78205</td>
<td style="text-align: right;">29</td>
</tr>
<tr class="odd">
<td style="text-align: right;">13</td>
<td style="text-align: right;">21.61899</td>
<td style="text-align: right;">19</td>
</tr>
<tr class="even">
<td style="text-align: right;">14</td>
<td style="text-align: right;">17.60899</td>
<td style="text-align: right;">12</td>
</tr>
<tr class="odd">
<td style="text-align: right;">15</td>
<td style="text-align: right;">19.56421</td>
<td style="text-align: right;">22</td>
</tr>
<tr class="even">
<td style="text-align: right;">16</td>
<td style="text-align: right;">27.11782</td>
<td style="text-align: right;">32</td>
</tr>
<tr class="odd">
<td style="text-align: right;">17</td>
<td style="text-align: right;">16.85600</td>
<td style="text-align: right;">19</td>
</tr>
<tr class="even">
<td style="text-align: right;">18</td>
<td style="text-align: right;">19.61608</td>
<td style="text-align: right;">16</td>
</tr>
<tr class="odd">
<td style="text-align: right;">19</td>
<td style="text-align: right;">21.05781</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="even">
<td style="text-align: right;">20</td>
<td style="text-align: right;">18.58269</td>
<td style="text-align: right;">16</td>
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
