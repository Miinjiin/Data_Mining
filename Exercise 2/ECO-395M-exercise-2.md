## 1) Saratoga house prices

\*\* Between linear model and K-nearest-neighbor regression model, which
one is better at achieving lower out-of-sample mean-squared error? \*\*

First of all, we built the best linear model for price that we can. To
evaluate the model performance we making, we compared the rmse of the
model with the medium model.

    ## [1] 64487.87

6.5119901^{4}

6.5357641^{4}

    ##  [1] "price"                  "lotSize"                "age"                   
    ##  [4] "livingArea"             "bedrooms"               "fireplaces"            
    ##  [7] "bathrooms"              "rooms"                  "heatinghot air"        
    ## [10] "heatinghot water/steam" "heatingelectric"        "fuelelectric"          
    ## [13] "fueloil"                "centralAirNo"

    ##  [1] "price"                  "lotSize"                "age"                   
    ##  [4] "livingArea"             "bedrooms"               "fireplaces"            
    ##  [7] "bathrooms"              "rooms"                  "heatinghot air"        
    ## [10] "heatinghot water/steam" "heatingelectric"        "fuelelectric"          
    ## [13] "fueloil"                "centralAirNo"

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
<td style="text-align: right;">-0.92</td>
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
<td style="text-align: right;">0.27</td>
</tr>
<tr class="odd">
<td style="text-align: left;">age</td>
<td style="text-align: right;">-0.03</td>
</tr>
<tr class="even">
<td style="text-align: left;">historypoor</td>
<td style="text-align: right;">-0.92</td>
</tr>
<tr class="odd">
<td style="text-align: left;">historyterrible</td>
<td style="text-align: right;">-1.74</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposeedu</td>
<td style="text-align: right;">0.68</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposegoods/repair</td>
<td style="text-align: right;">0.19</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposenewcar</td>
<td style="text-align: right;">1.10</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposeusedcar</td>
<td style="text-align: right;">-0.65</td>
</tr>
<tr class="even">
<td style="text-align: left;">foreigngerman</td>
<td style="text-align: right;">-1.75</td>
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
<td style="text-align: right;">8302</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">698</td>
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
<td style="text-align: right;">92.24</td>
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
<td style="text-align: right;">8183</td>
<td style="text-align: right;">119</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">447</td>
<td style="text-align: right;">251</td>
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
<td style="text-align: right;">93.71</td>
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
<td style="text-align: right;">8193</td>
<td style="text-align: right;">109</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">453</td>
<td style="text-align: right;">245</td>
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
<td style="text-align: right;">93.76</td>
</tr>
</tbody>
</table>

</td>
</tr>
</tbody>
</table>

Model we made has similar result to baseline 2 model

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
<td style="text-align: right;">0.7174244</td>
<td style="text-align: right;">0.9751244</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.6613008</td>
<td style="text-align: right;">0.9651741</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.5966935</td>
<td style="text-align: right;">0.9552239</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.5288231</td>
<td style="text-align: right;">0.9452736</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.4585599</td>
<td style="text-align: right;">0.9278607</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.3937350</td>
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
<td style="text-align: right;">19.94009</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="even">
<td style="text-align: right;">2</td>
<td style="text-align: right;">19.45649</td>
<td style="text-align: right;">23</td>
</tr>
<tr class="odd">
<td style="text-align: right;">3</td>
<td style="text-align: right;">21.27575</td>
<td style="text-align: right;">16</td>
</tr>
<tr class="even">
<td style="text-align: right;">4</td>
<td style="text-align: right;">16.41910</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="odd">
<td style="text-align: right;">5</td>
<td style="text-align: right;">19.03125</td>
<td style="text-align: right;">19</td>
</tr>
<tr class="even">
<td style="text-align: right;">6</td>
<td style="text-align: right;">19.71673</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="odd">
<td style="text-align: right;">7</td>
<td style="text-align: right;">23.04765</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="even">
<td style="text-align: right;">8</td>
<td style="text-align: right;">22.00697</td>
<td style="text-align: right;">22</td>
</tr>
<tr class="odd">
<td style="text-align: right;">9</td>
<td style="text-align: right;">20.09535</td>
<td style="text-align: right;">24</td>
</tr>
<tr class="even">
<td style="text-align: right;">10</td>
<td style="text-align: right;">19.36654</td>
<td style="text-align: right;">16</td>
</tr>
<tr class="odd">
<td style="text-align: right;">11</td>
<td style="text-align: right;">19.53029</td>
<td style="text-align: right;">18</td>
</tr>
<tr class="even">
<td style="text-align: right;">12</td>
<td style="text-align: right;">16.83846</td>
<td style="text-align: right;">25</td>
</tr>
<tr class="odd">
<td style="text-align: right;">13</td>
<td style="text-align: right;">21.75694</td>
<td style="text-align: right;">14</td>
</tr>
<tr class="even">
<td style="text-align: right;">14</td>
<td style="text-align: right;">21.15161</td>
<td style="text-align: right;">22</td>
</tr>
<tr class="odd">
<td style="text-align: right;">15</td>
<td style="text-align: right;">19.85787</td>
<td style="text-align: right;">18</td>
</tr>
<tr class="even">
<td style="text-align: right;">16</td>
<td style="text-align: right;">18.54759</td>
<td style="text-align: right;">25</td>
</tr>
<tr class="odd">
<td style="text-align: right;">17</td>
<td style="text-align: right;">23.94067</td>
<td style="text-align: right;">25</td>
</tr>
<tr class="even">
<td style="text-align: right;">18</td>
<td style="text-align: right;">21.10731</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="odd">
<td style="text-align: right;">19</td>
<td style="text-align: right;">17.40278</td>
<td style="text-align: right;">15</td>
</tr>
<tr class="even">
<td style="text-align: right;">20</td>
<td style="text-align: right;">21.51054</td>
<td style="text-align: right;">21</td>
</tr>
</tbody>
</table>

![](ECO-395M-exercise-2_files/figure-markdown_strict/problem%203.2.4-1.png)
**Figure 1:** Generated 20 folds having information of expected number
of bookings with children and actual number of bookings with children.
(Red=expected, Green=actual)
