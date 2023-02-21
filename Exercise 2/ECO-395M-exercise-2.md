## 1) Saratoga house prices

\*\* Between linear model and K-nearest-neighbor regression model, which
one is better at achieving lower out-of-sample mean-squared error? \*\*

    ## [1] 61933.92

    ## [1] 60887.64

    ## [1] 61214.81

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

![](ECO-395M-exercise-2_files/figure-markdown_strict/problem%202.1-1.png)

**Figure 1:** Bar plot showing average default probability by credit
history.

<table>
<thead>
<tr class="header">
<th></th>
<th style="text-align: right;">.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>(Intercept)</td>
<td style="text-align: right;">-0.61</td>
</tr>
<tr class="even">
<td>duration</td>
<td style="text-align: right;">0.03</td>
</tr>
<tr class="odd">
<td>amount</td>
<td style="text-align: right;">0.00</td>
</tr>
<tr class="even">
<td>installment</td>
<td style="text-align: right;">0.19</td>
</tr>
<tr class="odd">
<td>age</td>
<td style="text-align: right;">-0.02</td>
</tr>
<tr class="even">
<td>historypoor</td>
<td style="text-align: right;">-1.13</td>
</tr>
<tr class="odd">
<td>historyterrible</td>
<td style="text-align: right;">-1.89</td>
</tr>
<tr class="even">
<td>purposeedu</td>
<td style="text-align: right;">0.65</td>
</tr>
<tr class="odd">
<td>purposegoods/repair</td>
<td style="text-align: right;">0.08</td>
</tr>
<tr class="even">
<td>purposenewcar</td>
<td style="text-align: right;">0.80</td>
</tr>
<tr class="odd">
<td>purposeusedcar</td>
<td style="text-align: right;">-0.80</td>
</tr>
<tr class="even">
<td>foreigngerman</td>
<td style="text-align: right;">-1.04</td>
</tr>
</tbody>
</table>

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

    ## Warning: In lm.fit(x, y, offset = offset, singular.ok = singular.ok, ...) :
    ##  extra argument 'family' will be disregarded

    ## Warning: In lm.fit(x, y, offset = offset, singular.ok = singular.ok, ...) :
    ##  extra argument 'family' will be disregarded

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
<td style="text-align: right;">8276</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">724</td>
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
<td style="text-align: right;">91.96</td>
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
<td style="text-align: right;">8156</td>
<td style="text-align: right;">120</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">476</td>
<td style="text-align: right;">248</td>
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
<td style="text-align: right;">93.38</td>
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
<td style="text-align: right;">8153</td>
<td style="text-align: right;">123</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">479</td>
<td style="text-align: right;">245</td>
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
<td style="text-align: right;">93.31</td>
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
<td style="text-align: right;">0.7167718</td>
<td style="text-align: right;">0.9726368</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.6606482</td>
<td style="text-align: right;">0.9626866</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.5940831</td>
<td style="text-align: right;">0.9552239</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.5266478</td>
<td style="text-align: right;">0.9427861</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.4596476</td>
<td style="text-align: right;">0.9253731</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.3933000</td>
<td style="text-align: right;">0.9054726</td>
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
<td style="text-align: right;">16.25783</td>
<td style="text-align: right;">18</td>
</tr>
<tr class="even">
<td style="text-align: right;">2</td>
<td style="text-align: right;">19.87360</td>
<td style="text-align: right;">23</td>
</tr>
<tr class="odd">
<td style="text-align: right;">3</td>
<td style="text-align: right;">19.21082</td>
<td style="text-align: right;">18</td>
</tr>
<tr class="even">
<td style="text-align: right;">4</td>
<td style="text-align: right;">16.23235</td>
<td style="text-align: right;">14</td>
</tr>
<tr class="odd">
<td style="text-align: right;">5</td>
<td style="text-align: right;">19.60883</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="even">
<td style="text-align: right;">6</td>
<td style="text-align: right;">18.81752</td>
<td style="text-align: right;">22</td>
</tr>
<tr class="odd">
<td style="text-align: right;">7</td>
<td style="text-align: right;">18.85148</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="even">
<td style="text-align: right;">8</td>
<td style="text-align: right;">21.35309</td>
<td style="text-align: right;">24</td>
</tr>
<tr class="odd">
<td style="text-align: right;">9</td>
<td style="text-align: right;">21.36310</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="even">
<td style="text-align: right;">10</td>
<td style="text-align: right;">22.11810</td>
<td style="text-align: right;">22</td>
</tr>
<tr class="odd">
<td style="text-align: right;">11</td>
<td style="text-align: right;">22.62715</td>
<td style="text-align: right;">29</td>
</tr>
<tr class="even">
<td style="text-align: right;">12</td>
<td style="text-align: right;">19.55053</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="odd">
<td style="text-align: right;">13</td>
<td style="text-align: right;">19.63405</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="even">
<td style="text-align: right;">14</td>
<td style="text-align: right;">22.58145</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="odd">
<td style="text-align: right;">15</td>
<td style="text-align: right;">20.49343</td>
<td style="text-align: right;">15</td>
</tr>
<tr class="even">
<td style="text-align: right;">16</td>
<td style="text-align: right;">22.05827</td>
<td style="text-align: right;">22</td>
</tr>
<tr class="odd">
<td style="text-align: right;">17</td>
<td style="text-align: right;">19.29131</td>
<td style="text-align: right;">21</td>
</tr>
<tr class="even">
<td style="text-align: right;">18</td>
<td style="text-align: right;">22.81697</td>
<td style="text-align: right;">23</td>
</tr>
<tr class="odd">
<td style="text-align: right;">19</td>
<td style="text-align: right;">21.83196</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="even">
<td style="text-align: right;">20</td>
<td style="text-align: right;">17.42815</td>
<td style="text-align: right;">23</td>
</tr>
</tbody>
</table>

    ##   fold       variable    value
    ## 1    1 expected_child 16.25783
    ## 2    2 expected_child 19.87360
    ## 3    3 expected_child 19.21082
    ## 4    4 expected_child 16.23235
    ## 5    5 expected_child 19.60883
    ## 6    6 expected_child 18.81752

![](ECO-395M-exercise-2_files/figure-markdown_strict/problem%203.2.4-1.png)
**Figure 1:** Generated 20 folds having information of expected number
of bookings with children and actual number of bookings with children.
