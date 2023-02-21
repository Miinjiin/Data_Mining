## 1) Saratoga house prices

\*\* Between linear model and K-nearest-neighbor regression model, which
one is better at achieving lower out-of-sample mean-squared error? \*\*

    ## [1] 65288.39

    ## [1] 64516.35

    ## [1] 65401.06

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
<td style="text-align: right;">-0.98</td>
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
<td style="text-align: right;">-1.95</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposeedu</td>
<td style="text-align: right;">1.02</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposegoods/repair</td>
<td style="text-align: right;">0.23</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposenewcar</td>
<td style="text-align: right;">1.02</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposeusedcar</td>
<td style="text-align: right;">-0.83</td>
</tr>
<tr class="even">
<td style="text-align: left;">foreigngerman</td>
<td style="text-align: right;">-0.94</td>
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

    ## 'data.frame':    45000 obs. of  22 variables:
    ##  $ hotel                         : chr  "City_Hotel" "City_Hotel" "Resort_Hotel" "Resort_Hotel" ...
    ##  $ lead_time                     : int  217 2 95 143 136 67 56 80 6 130 ...
    ##  $ stays_in_weekend_nights       : int  1 0 2 2 1 2 0 0 2 1 ...
    ##  $ stays_in_week_nights          : int  3 1 5 6 4 2 3 4 2 2 ...
    ##  $ adults                        : int  2 2 2 2 2 2 0 2 2 2 ...
    ##  $ children                      : int  0 0 0 0 0 0 1 0 1 0 ...
    ##  $ meal                          : chr  "BB" "BB" "BB" "HB" ...
    ##  $ market_segment                : chr  "Offline_TA/TO" "Direct" "Online_TA" "Online_TA" ...
    ##  $ distribution_channel          : chr  "TA/TO" "Direct" "TA/TO" "TA/TO" ...
    ##  $ is_repeated_guest             : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ previous_cancellations        : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ previous_bookings_not_canceled: int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ reserved_room_type            : chr  "A" "D" "A" "A" ...
    ##  $ assigned_room_type            : chr  "A" "K" "A" "A" ...
    ##  $ booking_changes               : int  0 0 2 0 0 0 0 0 0 0 ...
    ##  $ deposit_type                  : chr  "No_Deposit" "No_Deposit" "No_Deposit" "No_Deposit" ...
    ##  $ days_in_waiting_list          : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ customer_type                 : chr  "Transient-Party" "Transient" "Transient" "Transient" ...
    ##  $ average_daily_rate            : num  80.8 170 8 81 157.6 ...
    ##  $ required_car_parking_spaces   : chr  "none" "none" "none" "none" ...
    ##  $ total_of_special_requests     : int  1 3 2 1 4 1 1 1 1 0 ...
    ##  $ arrival_date                  : chr  "2016-09-01" "2017-08-25" "2016-11-19" "2016-04-26" ...

Under is the predictions on the testing set. We will use this to measure
out-of-sample performance.

**Table1:** Confusion matrix for baseline 1 model, a small model that
used only four features.

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
<td style="text-align: right;">8284</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">716</td>
</tr>
</tbody>
</table>

We can check it never predicted children.

Percentage of out-of-sample correct classifications is,

<table>
<thead>
<tr class="header">
<th style="text-align: right;">x</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">92.04</td>
</tr>
</tbody>
</table>

**Table2:** Confusion matrix for baseline 2 model, a big model that used
all possible predictors expect arrival\_date.

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
<td style="text-align: right;">8178</td>
<td style="text-align: right;">106</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">449</td>
<td style="text-align: right;">267</td>
</tr>
</tbody>
</table>

Percentage of out-of-sample correct classifications is,

<table>
<thead>
<tr class="header">
<th style="text-align: right;">x</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">93.83</td>
</tr>
</tbody>
</table>

Having better result than baseline 1 model

**Table3:** Confusion matrix for best linear model we made, adding
meaningful interaction variables.

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
<td style="text-align: right;">8185</td>
<td style="text-align: right;">99</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">458</td>
<td style="text-align: right;">258</td>
</tr>
</tbody>
</table>

Percentage of out-of-sample correct classifications is,

<table>
<thead>
<tr class="header">
<th style="text-align: right;">x</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">93.81</td>
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
<td style="text-align: right;">0.7211225</td>
<td style="text-align: right;">0.9776119</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.6617359</td>
<td style="text-align: right;">0.9626866</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.5984338</td>
<td style="text-align: right;">0.9552239</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.5325212</td>
<td style="text-align: right;">0.9452736</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.4611703</td>
<td style="text-align: right;">0.9303483</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.3980857</td>
<td style="text-align: right;">0.9129353</td>
</tr>
</tbody>
</table>

To make ROC curve plot, we made a dataframe for False Positive Rate
value and True Postive Rate value for each threshold t.

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
<td style="text-align: right;">26.44073</td>
<td style="text-align: right;">32</td>
</tr>
<tr class="even">
<td style="text-align: right;">2</td>
<td style="text-align: right;">23.02324</td>
<td style="text-align: right;">24</td>
</tr>
<tr class="odd">
<td style="text-align: right;">3</td>
<td style="text-align: right;">23.41067</td>
<td style="text-align: right;">25</td>
</tr>
<tr class="even">
<td style="text-align: right;">4</td>
<td style="text-align: right;">22.68622</td>
<td style="text-align: right;">19</td>
</tr>
<tr class="odd">
<td style="text-align: right;">5</td>
<td style="text-align: right;">20.74658</td>
<td style="text-align: right;">22</td>
</tr>
<tr class="even">
<td style="text-align: right;">6</td>
<td style="text-align: right;">19.39443</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="odd">
<td style="text-align: right;">7</td>
<td style="text-align: right;">19.46407</td>
<td style="text-align: right;">18</td>
</tr>
<tr class="even">
<td style="text-align: right;">8</td>
<td style="text-align: right;">23.17621</td>
<td style="text-align: right;">19</td>
</tr>
<tr class="odd">
<td style="text-align: right;">9</td>
<td style="text-align: right;">19.65619</td>
<td style="text-align: right;">16</td>
</tr>
<tr class="even">
<td style="text-align: right;">10</td>
<td style="text-align: right;">18.62772</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="odd">
<td style="text-align: right;">11</td>
<td style="text-align: right;">17.28727</td>
<td style="text-align: right;">13</td>
</tr>
<tr class="even">
<td style="text-align: right;">12</td>
<td style="text-align: right;">19.89755</td>
<td style="text-align: right;">23</td>
</tr>
<tr class="odd">
<td style="text-align: right;">13</td>
<td style="text-align: right;">19.47573</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="even">
<td style="text-align: right;">14</td>
<td style="text-align: right;">18.70615</td>
<td style="text-align: right;">19</td>
</tr>
<tr class="odd">
<td style="text-align: right;">15</td>
<td style="text-align: right;">19.62264</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="even">
<td style="text-align: right;">16</td>
<td style="text-align: right;">16.99710</td>
<td style="text-align: right;">18</td>
</tr>
<tr class="odd">
<td style="text-align: right;">17</td>
<td style="text-align: right;">18.01732</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="even">
<td style="text-align: right;">18</td>
<td style="text-align: right;">17.70746</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="odd">
<td style="text-align: right;">19</td>
<td style="text-align: right;">18.98224</td>
<td style="text-align: right;">22</td>
</tr>
<tr class="even">
<td style="text-align: right;">20</td>
<td style="text-align: right;">18.68049</td>
<td style="text-align: right;">19</td>
</tr>
</tbody>
</table>

![](ECO-395M-exercise-2_files/figure-markdown_strict/problem%203.2.4-1.png)
**Figure 1:** Generated 20 folds having information of expected number
of bookings with children and actual number of bookings with children.
