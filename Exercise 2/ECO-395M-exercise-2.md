## 1) Saratoga house prices

\*\* Between linear model and K-nearest-neighbor regression model, which
one is better at achieving lower out-of-sample mean-squared error? \*\*

    ## [1] 70563.19

    ## [1] 70385.55

    ## [1] 71098.82

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
<th style="text-align: left;"></th>
<th style="text-align: right;">.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">(Intercept)</td>
<td style="text-align: right;">-0.54</td>
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
<td style="text-align: right;">0.22</td>
</tr>
<tr class="odd">
<td style="text-align: left;">age</td>
<td style="text-align: right;">-0.02</td>
</tr>
<tr class="even">
<td style="text-align: left;">historypoor</td>
<td style="text-align: right;">-1.20</td>
</tr>
<tr class="odd">
<td style="text-align: left;">historyterrible</td>
<td style="text-align: right;">-2.08</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposeedu</td>
<td style="text-align: right;">0.89</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposegoods/repair</td>
<td style="text-align: right;">0.16</td>
</tr>
<tr class="even">
<td style="text-align: left;">purposenewcar</td>
<td style="text-align: right;">0.93</td>
</tr>
<tr class="odd">
<td style="text-align: left;">purposeusedcar</td>
<td style="text-align: right;">-0.66</td>
</tr>
<tr class="even">
<td style="text-align: left;">foreigngerman</td>
<td style="text-align: right;">-1.37</td>
</tr>
</tbody>
</table>

    ## data frame with 0 columns and 1 row

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

    ## Warning: In lm.fit(x, y, offset = offset, singular.ok = singular.ok, ...) :
    ##  extra argument 'family' will be disregarded

    ##                  (Intercept)  market_segmentComplementary 
    ##                       -0.025                        0.084 
    ##      market_segmentCorporate         market_segmentDirect 
    ##                        0.013                        0.113 
    ##         market_segmentGroups  market_segmentOffline_TA/TO 
    ##                        0.008                        0.023 
    ##      market_segmentOnline_TA                       adults 
    ##                        0.079                        0.018 
    ##           customer_typeGroup       customer_typeTransient 
    ##                       -0.008                        0.020 
    ## customer_typeTransient-Party            is_repeated_guest 
    ##                       -0.007                       -0.039

    ## Warning: In lm.fit(x, y, offset = offset, singular.ok = singular.ok, ...) :
    ##  extra argument 'family' will be disregarded

    ##                  (Intercept)  market_segmentComplementary 
    ##                       -0.025                        0.084 
    ##      market_segmentCorporate         market_segmentDirect 
    ##                        0.013                        0.113 
    ##         market_segmentGroups  market_segmentOffline_TA/TO 
    ##                        0.008                        0.023 
    ##      market_segmentOnline_TA                       adults 
    ##                        0.079                        0.018 
    ##           customer_typeGroup       customer_typeTransient 
    ##                       -0.008                        0.020 
    ## customer_typeTransient-Party            is_repeated_guest 
    ##                       -0.007                       -0.039

    ##  [1] "hotel"                          "lead_time"                     
    ##  [3] "stays_in_weekend_nights"        "stays_in_week_nights"          
    ##  [5] "adults"                         "children"                      
    ##  [7] "meal"                           "market_segment"                
    ##  [9] "distribution_channel"           "is_repeated_guest"             
    ## [11] "previous_cancellations"         "previous_bookings_not_canceled"
    ## [13] "reserved_room_type"             "assigned_room_type"            
    ## [15] "booking_changes"                "deposit_type"                  
    ## [17] "days_in_waiting_list"           "customer_type"                 
    ## [19] "average_daily_rate"             "required_car_parking_spaces"   
    ## [21] "total_of_special_requests"      "arrival_date"

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
<td style="text-align: right;">8235</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">765</td>
</tr>
</tbody>
</table>

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
<td style="text-align: right;">8134</td>
<td style="text-align: right;">101</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">499</td>
<td style="text-align: right;">266</td>
</tr>
</tbody>
</table>

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
<td style="text-align: right;">8140</td>
<td style="text-align: right;">95</td>
</tr>
<tr class="even">
<td style="text-align: left;">1</td>
<td style="text-align: right;">501</td>
<td style="text-align: right;">264</td>
</tr>
</tbody>
</table>

### Model validation : STEP 1

<table>
<thead>
<tr class="header">
<th style="text-align: right;">roc_tpr</th>
<th style="text-align: right;">roc_fpr</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: right;">0.9753086</td>
<td style="text-align: right;">0.7344940</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.9753086</td>
<td style="text-align: right;">0.6811752</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.9753086</td>
<td style="text-align: right;">0.6180631</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.9506173</td>
<td style="text-align: right;">0.5244831</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.9506173</td>
<td style="text-align: right;">0.4526659</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.9382716</td>
<td style="text-align: right;">0.4036997</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.9135802</td>
<td style="text-align: right;">0.3460283</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.8641975</td>
<td style="text-align: right;">0.3014146</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.8518519</td>
<td style="text-align: right;">0.2459195</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.8024691</td>
<td style="text-align: right;">0.2067465</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.7777778</td>
<td style="text-align: right;">0.1849837</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.7407407</td>
<td style="text-align: right;">0.1545158</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.7283951</td>
<td style="text-align: right;">0.1284004</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.6913580</td>
<td style="text-align: right;">0.1109902</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.6543210</td>
<td style="text-align: right;">0.0935800</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.6543210</td>
<td style="text-align: right;">0.0837867</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.6419753</td>
<td style="text-align: right;">0.0729053</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.6419753</td>
<td style="text-align: right;">0.0696409</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.6419753</td>
<td style="text-align: right;">0.0620239</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.6296296</td>
<td style="text-align: right;">0.0565832</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.5802469</td>
<td style="text-align: right;">0.0522307</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.5679012</td>
<td style="text-align: right;">0.0500544</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.5555556</td>
<td style="text-align: right;">0.0457018</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.5555556</td>
<td style="text-align: right;">0.0446137</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.5555556</td>
<td style="text-align: right;">0.0424374</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.5308642</td>
<td style="text-align: right;">0.0348205</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.5308642</td>
<td style="text-align: right;">0.0315560</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.5308642</td>
<td style="text-align: right;">0.0315560</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.5308642</td>
<td style="text-align: right;">0.0304679</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.5185185</td>
<td style="text-align: right;">0.0282916</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.5185185</td>
<td style="text-align: right;">0.0272035</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.5185185</td>
<td style="text-align: right;">0.0261153</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.5061728</td>
<td style="text-align: right;">0.0250272</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.4814815</td>
<td style="text-align: right;">0.0239391</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.4814815</td>
<td style="text-align: right;">0.0239391</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.4691358</td>
<td style="text-align: right;">0.0217628</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.4691358</td>
<td style="text-align: right;">0.0217628</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.4567901</td>
<td style="text-align: right;">0.0206746</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.4567901</td>
<td style="text-align: right;">0.0206746</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.4567901</td>
<td style="text-align: right;">0.0206746</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.4444444</td>
<td style="text-align: right;">0.0206746</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.4444444</td>
<td style="text-align: right;">0.0206746</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.4444444</td>
<td style="text-align: right;">0.0206746</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.4444444</td>
<td style="text-align: right;">0.0206746</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.4444444</td>
<td style="text-align: right;">0.0206746</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.4320988</td>
<td style="text-align: right;">0.0195865</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.3827160</td>
<td style="text-align: right;">0.0195865</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.3827160</td>
<td style="text-align: right;">0.0195865</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.3580247</td>
<td style="text-align: right;">0.0195865</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.3456790</td>
<td style="text-align: right;">0.0184984</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.3456790</td>
<td style="text-align: right;">0.0152339</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.3333333</td>
<td style="text-align: right;">0.0141458</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.3209877</td>
<td style="text-align: right;">0.0119695</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.3086420</td>
<td style="text-align: right;">0.0119695</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.2839506</td>
<td style="text-align: right;">0.0119695</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.2716049</td>
<td style="text-align: right;">0.0108814</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.2592593</td>
<td style="text-align: right;">0.0097933</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.2469136</td>
<td style="text-align: right;">0.0087051</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.2469136</td>
<td style="text-align: right;">0.0065288</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.2469136</td>
<td style="text-align: right;">0.0065288</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.2469136</td>
<td style="text-align: right;">0.0065288</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.2469136</td>
<td style="text-align: right;">0.0054407</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.2469136</td>
<td style="text-align: right;">0.0054407</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.2469136</td>
<td style="text-align: right;">0.0054407</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.2222222</td>
<td style="text-align: right;">0.0043526</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.1975309</td>
<td style="text-align: right;">0.0043526</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.1851852</td>
<td style="text-align: right;">0.0043526</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.1728395</td>
<td style="text-align: right;">0.0043526</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.1604938</td>
<td style="text-align: right;">0.0032644</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.1481481</td>
<td style="text-align: right;">0.0010881</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.1481481</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.1234568</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.0987654</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.0987654</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.0864198</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.0740741</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.0617284</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.0617284</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.0617284</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.0493827</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.0493827</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.0370370</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.0370370</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.0370370</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.0370370</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.0246914</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.0123457</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.0123457</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="odd">
<td style="text-align: right;">0.0123457</td>
<td style="text-align: right;">0.0000000</td>
</tr>
<tr class="even">
<td style="text-align: right;">0.0123457</td>
<td style="text-align: right;">0.0000000</td>
</tr>
</tbody>
</table>

![](ECO-395M-exercise-2_files/figure-markdown_strict/problem%203.2.1.2-1.png)

![](ECO-395M-exercise-2_files/figure-markdown_strict/problem%203.2.2-1.png)

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
<td style="text-align: right;">24.68700</td>
<td style="text-align: right;">24</td>
</tr>
<tr class="even">
<td style="text-align: right;">2</td>
<td style="text-align: right;">18.98599</td>
<td style="text-align: right;">14</td>
</tr>
<tr class="odd">
<td style="text-align: right;">3</td>
<td style="text-align: right;">18.50322</td>
<td style="text-align: right;">25</td>
</tr>
<tr class="even">
<td style="text-align: right;">4</td>
<td style="text-align: right;">19.43633</td>
<td style="text-align: right;">16</td>
</tr>
<tr class="odd">
<td style="text-align: right;">5</td>
<td style="text-align: right;">20.31182</td>
<td style="text-align: right;">23</td>
</tr>
<tr class="even">
<td style="text-align: right;">6</td>
<td style="text-align: right;">20.82018</td>
<td style="text-align: right;">19</td>
</tr>
<tr class="odd">
<td style="text-align: right;">7</td>
<td style="text-align: right;">22.42749</td>
<td style="text-align: right;">22</td>
</tr>
<tr class="even">
<td style="text-align: right;">8</td>
<td style="text-align: right;">22.73323</td>
<td style="text-align: right;">28</td>
</tr>
<tr class="odd">
<td style="text-align: right;">9</td>
<td style="text-align: right;">21.65066</td>
<td style="text-align: right;">19</td>
</tr>
<tr class="even">
<td style="text-align: right;">10</td>
<td style="text-align: right;">17.26559</td>
<td style="text-align: right;">20</td>
</tr>
<tr class="odd">
<td style="text-align: right;">11</td>
<td style="text-align: right;">21.00333</td>
<td style="text-align: right;">25</td>
</tr>
<tr class="even">
<td style="text-align: right;">12</td>
<td style="text-align: right;">22.35651</td>
<td style="text-align: right;">17</td>
</tr>
<tr class="odd">
<td style="text-align: right;">13</td>
<td style="text-align: right;">22.29650</td>
<td style="text-align: right;">23</td>
</tr>
<tr class="even">
<td style="text-align: right;">14</td>
<td style="text-align: right;">14.25525</td>
<td style="text-align: right;">14</td>
</tr>
<tr class="odd">
<td style="text-align: right;">15</td>
<td style="text-align: right;">17.95936</td>
<td style="text-align: right;">19</td>
</tr>
<tr class="even">
<td style="text-align: right;">16</td>
<td style="text-align: right;">17.94640</td>
<td style="text-align: right;">12</td>
</tr>
<tr class="odd">
<td style="text-align: right;">17</td>
<td style="text-align: right;">24.09850</td>
<td style="text-align: right;">25</td>
</tr>
<tr class="even">
<td style="text-align: right;">18</td>
<td style="text-align: right;">21.71719</td>
<td style="text-align: right;">19</td>
</tr>
<tr class="odd">
<td style="text-align: right;">19</td>
<td style="text-align: right;">16.53248</td>
<td style="text-align: right;">18</td>
</tr>
<tr class="even">
<td style="text-align: right;">20</td>
<td style="text-align: right;">17.01295</td>
<td style="text-align: right;">20</td>
</tr>
</tbody>
</table>

    ##   fold       variable    value
    ## 1    1 expected_child 24.68700
    ## 2    2 expected_child 18.98599
    ## 3    3 expected_child 18.50322
    ## 4    4 expected_child 19.43633
    ## 5    5 expected_child 20.31182
    ## 6    6 expected_child 20.82018

![](ECO-395M-exercise-2_files/figure-markdown_strict/problem%203.2.4-1.png)
