## 1) Data visualization: flights at ABIA

**Question: What is the best time of year to fly to minimize delays, and
does this change by destination?**

![](ECO-395M-exercise-1_files/figure-markdown_strict/problem%201a-1.png)

**Figure 1:** Line graph showing monthly average delay time for 49,623
flights that departed from AUS in 2008.

Figure 1 shows that the best months to fly from Austin to minimize
delays are September and October. September has the least delays of all
(around two minutes), while October has an average delay of four
minutes, which is significantly less compared to other months. This
makes sense as these months lie between the two busiest travel seasons
of the year, summer vacation (July and August) and Thanksgiving and
Christmas/New Year (November and December)

![](ECO-395M-exercise-1_files/figure-markdown_strict/problem%201b-1.png)

**Figure 2:** Line graph showing monthly average delay time for 22,740
flights that departed from AUS to the six most popular destination
airports in 2008.

Next, we wanted to find out whether the result changes by destination.
We picked six most popular destinations, which are Dallas Love Field
Airport (DAL), Denver International Airport (DEN), Dallas/Fort Worth
International Airport (DFW), George Bush Intercontinental Airport (IAH),
Chicago O’Hare International Airport (ORD), Phoenix Sky Harbor
International Airport (PHX). Figure 2 shows that the overall trend of
delays throughout the year is similar to that shown by Figure 1. In
general, September and October seem to be the months with the least
flight delays.

## 2) Wrangling the Olympics

#### A) What is 95th percentile of heights for female competitiors across Athletics events?

    ## 95% 
    ## 183

95th percentile of heights for female competitors across Athletcis
events is 183cm.

#### B) Which single women’s event had the greatest variability in competitor’s heights across the entire history of the Olympics, as measured by the standard deviation?

<table>
<thead>
<tr class="header">
<th style="text-align: left;">Event</th>
<th style="text-align: right;">Height Variability</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">Rowing Women’s Coxed Fours</td>
<td style="text-align: right;">10.86549</td>
</tr>
</tbody>
</table>

Rowing Women’s Coxed Fours has the greatest variability in women
competitor’s heights across the entire history of the Olympics.

#### C) How has the average age of Olympic swimmers changed over time? Does this trend look different depending on the gender?

![](ECO-395M-exercise-1_files/figure-markdown_strict/problem%202C-1.png)

**Figure 3:** Line graph showing the change in average age of Olympic
swimmers between 1600 - 2016

The change in average age has an overall upward trend for both male and
female Olympic swimmers. For male swimmers, the average age marks its
lowest (mid-teens) in the early 1900’s and goes through a period of
steep hike through 1925. It then rapidly comes back down to late
teens/early twenties and steadily increases over a long period of time.
By 2000, the average male swimmer’s age is approximately mid-twenties.
The female swimmer’s average age displays a somewhat similar of an
upward trend. The average age revolves around early to mid teens between
1925 and 1975, then we see a massive spike that moves the average age
towards early to mid twenties through 2000s. Average age of female
swimmers is certainly lower than that of male swimmers throughout
history, but the rising trend is congruent.

## 3) K-nearest neighbors: cars

### Car trim level 350

![](ECO-395M-exercise-1_files/figure-markdown_strict/problem%203_1.1-1.png)

**Figure 1:** Plot showing RMSE for each value of K (from 2 to 150)

Here, we can see which K value has the lowest RMSE, and this is the
optimal value of K

**Optimal value of K**

    ## [1] 16

**RMSE from the Optimal value of K**

    ## [1] 10268.88

![](ECO-395M-exercise-1_files/figure-markdown_strict/problem%203_1.4-1.png)

**Figure 2:** Plot of the fitted model, predicted price and real price

### Car trim level 65 AMG

![](ECO-395M-exercise-1_files/figure-markdown_strict/problem%203_2.1-1.png)

**Figure 3:** Plot showing RMSE for each value of K (from 2 to 150)

Here, we can see which K value has the lowest RMSE, and this is the
optimal value of K

**Optimal value of K**

    ## [1] 73

**RMSE from the Optimal value of K**

    ## [1] 18330.38

![](ECO-395M-exercise-1_files/figure-markdown_strict/problem%203_2.4-1.png)

**Figure 4:** Plot of the fitted model, predicted price and real price

**Result: Trim 350 yields a larger optimal value of K**

<table>
<thead>
<tr class="header">
<th style="text-align: left;"></th>
<th style="text-align: right;">Trim 350</th>
<th style="text-align: right;">Trim 65 AMG</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">Number of rows</td>
<td style="text-align: right;">416</td>
<td style="text-align: right;">292</td>
</tr>
</tbody>
</table>

Trim 350 has larger optimal K value as it contains more data points than
trim 65 AMG. More data points means lower variance, less chance of
memorizing random noise.
