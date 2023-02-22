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

<table>
<tbody>
<tr class="odd">
<td style="text-align: left;">Medium_model_rmse</td>
</tr>
<tr class="even">
<td style="text-align: left;">63566.995</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Model_made_by_us_rmse</td>
</tr>
<tr class="even">
<td style="text-align: left;">63058.906</td>
</tr>
</tbody>
</table>

Top one is the RMSE is for the “medium\_model” from class, while below
is the RMSE of the best linear model we made. Our model does a slightly
better job at achieving lower out-of-sample mean-squared error.

    ## [1] 21

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
<td style="text-align: right;">65990.07</td>
<td style="text-align: right;">63068.07</td>
</tr>
<tr class="even">
<td style="text-align: right;">67470.48</td>
<td style="text-align: right;">64442.49</td>
</tr>
<tr class="odd">
<td style="text-align: right;">77053.86</td>
<td style="text-align: right;">71463.72</td>
</tr>
<tr class="even">
<td style="text-align: right;">72922.43</td>
<td style="text-align: right;">63631.60</td>
</tr>
<tr class="odd">
<td style="text-align: right;">72199.71</td>
<td style="text-align: right;">65798.19</td>
</tr>
<tr class="even">
<td style="text-align: right;">72389.32</td>
<td style="text-align: right;">70106.63</td>
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
<td style="text-align: right;">71554.98</td>
</tr>
<tr class="even">
<td style="text-align: left;">Mean LM RMSE</td>
<td style="text-align: right;">65495.27</td>
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
<th style="text-align: right;">coefficient</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">(Intercept)</td>
<td style="text-align: right;">-0.97</td>
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
<td style="text-align: right;">0.18</td>
</tr>
<tr class="odd">
<td style="text-align: left;">age</td>
<td style="text-align: right;">-0.01</td>
</tr>
<tr class="even">
<td style="text-align: left;">historypoor</td>
<td style="text-align: right;">-1.02</td>
</tr>
<tr class="odd">
<td style="text-align: left;">historyterrible</td>
<td style="text-align: right;">-1.68</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposeedu</td>
<td style="text-align: right;">0.35</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposegoods/repair</td>
<td style="text-align: right;">0.07</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposenewcar</td>
<td style="text-align: right;">0.77</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposeusedcar</td>
<td style="text-align: right;">-0.69</td>
</tr>
<tr class="even">
<td style="text-align: left;">foreigngerman</td>
<td style="text-align: right;">-1.58</td>
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
<td style="text-align: right;">8184</td>
<td style="text-align: right;">114</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">458</td>
<td style="text-align: right;">244</td>
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
<td style="text-align: right;">93.64</td>
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
<td style="text-align: right;">8189</td>
<td style="text-align: right;">109</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">467</td>
<td style="text-align: right;">235</td>
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
<td style="text-align: right;">93.6</td>
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
<td style="text-align: right;">0.7198173</td>
<td style="text-align: right;">0.9726368</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.6641288</td>
<td style="text-align: right;">0.9676617</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.5997390</td>
<td style="text-align: right;">0.9527363</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.5268653</td>
<td style="text-align: right;">0.9427861</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.4583424</td>
<td style="text-align: right;">0.9253731</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.3887318</td>
<td style="text-align: right;">0.9029851</td>
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
<td style="text-align: right;">26.88582</td>
<td style="text-align: right;">27</td>
</tr>
<tr class="even">
<td style="text-align: right;">2</td>
<td style="text-align: right;">18.09452</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="odd">
<td style="text-align: right;">3</td>
<td style="text-align: right;">25.09315</td>
<td style="text-align: right;">24</td>
</tr>
<tr class="even">
<td style="text-align: right;">4</td>
<td style="text-align: right;">20.58579</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="odd">
<td style="text-align: right;">5</td>
<td style="text-align: right;">22.09823</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="even">
<td style="text-align: right;">6</td>
<td style="text-align: right;">19.00764</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="odd">
<td style="text-align: right;">7</td>
<td style="text-align: right;">18.81545</td>
<td style="text-align: right;">22</td>
</tr>
<tr class="even">
<td style="text-align: right;">8</td>
<td style="text-align: right;">18.56033</td>
<td style="text-align: right;">15</td>
</tr>
<tr class="odd">
<td style="text-align: right;">9</td>
<td style="text-align: right;">16.15241</td>
<td style="text-align: right;">15</td>
</tr>
<tr class="even">
<td style="text-align: right;">10</td>
<td style="text-align: right;">21.22386</td>
<td style="text-align: right;">15</td>
</tr>
<tr class="odd">
<td style="text-align: right;">11</td>
<td style="text-align: right;">17.41258</td>
<td style="text-align: right;">24</td>
</tr>
<tr class="even">
<td style="text-align: right;">12</td>
<td style="text-align: right;">18.27971</td>
<td style="text-align: right;">22</td>
</tr>
<tr class="odd">
<td style="text-align: right;">13</td>
<td style="text-align: right;">18.39141</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="even">
<td style="text-align: right;">14</td>
<td style="text-align: right;">20.18885</td>
<td style="text-align: right;">18</td>
</tr>
<tr class="odd">
<td style="text-align: right;">15</td>
<td style="text-align: right;">18.16207</td>
<td style="text-align: right;">18</td>
</tr>
<tr class="even">
<td style="text-align: right;">16</td>
<td style="text-align: right;">17.15280</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="odd">
<td style="text-align: right;">17</td>
<td style="text-align: right;">18.29203</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="even">
<td style="text-align: right;">18</td>
<td style="text-align: right;">22.11956</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="odd">
<td style="text-align: right;">19</td>
<td style="text-align: right;">23.33099</td>
<td style="text-align: right;">22</td>
</tr>
<tr class="even">
<td style="text-align: right;">20</td>
<td style="text-align: right;">22.15281</td>
<td style="text-align: right;">21</td>
</tr>
</tbody>
</table>

![](ECO-395M-exercise-2_files/figure-markdown_strict/problem%203.2.4-1.png)
**Figure 1:** Generated 20 folds having information of expected number
of bookings with children and actual number of bookings with children.
(Red=expected, Green=actual)
