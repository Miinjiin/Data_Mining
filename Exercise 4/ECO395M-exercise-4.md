## 1) Clustering and PCA

## K-means Clustering

    ##  fixed.acidity    volatile.acidity  citric.acid     residual.sugar  
    ##  Min.   : 3.800   Min.   :0.0800   Min.   :0.0000   Min.   : 0.600  
    ##  1st Qu.: 6.400   1st Qu.:0.2300   1st Qu.:0.2500   1st Qu.: 1.800  
    ##  Median : 7.000   Median :0.2900   Median :0.3100   Median : 3.000  
    ##  Mean   : 7.215   Mean   :0.3397   Mean   :0.3186   Mean   : 5.443  
    ##  3rd Qu.: 7.700   3rd Qu.:0.4000   3rd Qu.:0.3900   3rd Qu.: 8.100  
    ##  Max.   :15.900   Max.   :1.5800   Max.   :1.6600   Max.   :65.800  
    ##    chlorides       free.sulfur.dioxide total.sulfur.dioxide    density      
    ##  Min.   :0.00900   Min.   :  1.00      Min.   :  6.0        Min.   :0.9871  
    ##  1st Qu.:0.03800   1st Qu.: 17.00      1st Qu.: 77.0        1st Qu.:0.9923  
    ##  Median :0.04700   Median : 29.00      Median :118.0        Median :0.9949  
    ##  Mean   :0.05603   Mean   : 30.53      Mean   :115.7        Mean   :0.9947  
    ##  3rd Qu.:0.06500   3rd Qu.: 41.00      3rd Qu.:156.0        3rd Qu.:0.9970  
    ##  Max.   :0.61100   Max.   :289.00      Max.   :440.0        Max.   :1.0390  
    ##        pH          sulphates         alcohol         quality     
    ##  Min.   :2.720   Min.   :0.2200   Min.   : 8.00   Min.   :3.000  
    ##  1st Qu.:3.110   1st Qu.:0.4300   1st Qu.: 9.50   1st Qu.:5.000  
    ##  Median :3.210   Median :0.5100   Median :10.30   Median :6.000  
    ##  Mean   :3.219   Mean   :0.5313   Mean   :10.49   Mean   :5.818  
    ##  3rd Qu.:3.320   3rd Qu.:0.6000   3rd Qu.:11.30   3rd Qu.:6.000  
    ##  Max.   :4.010   Max.   :2.0000   Max.   :14.90   Max.   :9.000  
    ##     color          
    ##  Length:6497       
    ##  Class :character  
    ##  Mode  :character  
    ##                    
    ##                    
    ## 

![](ECO395M-exercise-4_files/figure-markdown_strict/1.1.1-1.png)

![](ECO395M-exercise-4_files/figure-markdown_strict/1.1.2-1.png)

![](ECO395M-exercise-4_files/figure-markdown_strict/1.1.3-1.png)

![](ECO395M-exercise-4_files/figure-markdown_strict/1.1.4-1.png)

![](ECO395M-exercise-4_files/figure-markdown_strict/1.1.5-1.png)

## PCA

<table>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
PC1
</th>
<th style="text-align:right;">
PC2
</th>
<th style="text-align:right;">
PC3
</th>
<th style="text-align:right;">
PC4
</th>
<th style="text-align:right;">
PC5
</th>
<th style="text-align:right;">
PC6
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
fixed.acidity
</td>
<td style="text-align:right;">
-0.2387989
</td>
<td style="text-align:right;">
0.3363545
</td>
<td style="text-align:right;">
-0.4343013
</td>
<td style="text-align:right;">
0.1643462
</td>
<td style="text-align:right;">
-0.1474804
</td>
<td style="text-align:right;">
-0.2045537
</td>
</tr>
<tr>
<td style="text-align:left;">
volatile.acidity
</td>
<td style="text-align:right;">
-0.3807575
</td>
<td style="text-align:right;">
0.1175497
</td>
<td style="text-align:right;">
0.3072594
</td>
<td style="text-align:right;">
0.2127849
</td>
<td style="text-align:right;">
0.1514560
</td>
<td style="text-align:right;">
-0.4921431
</td>
</tr>
<tr>
<td style="text-align:left;">
citric.acid
</td>
<td style="text-align:right;">
0.1523884
</td>
<td style="text-align:right;">
0.1832994
</td>
<td style="text-align:right;">
-0.5905697
</td>
<td style="text-align:right;">
-0.2643003
</td>
<td style="text-align:right;">
-0.1553487
</td>
<td style="text-align:right;">
0.2276338
</td>
</tr>
<tr>
<td style="text-align:left;">
residual.sugar
</td>
<td style="text-align:right;">
0.3459199
</td>
<td style="text-align:right;">
0.3299142
</td>
<td style="text-align:right;">
0.1646884
</td>
<td style="text-align:right;">
0.1674430
</td>
<td style="text-align:right;">
-0.3533619
</td>
<td style="text-align:right;">
-0.2334778
</td>
</tr>
<tr>
<td style="text-align:left;">
chlorides
</td>
<td style="text-align:right;">
-0.2901126
</td>
<td style="text-align:right;">
0.3152580
</td>
<td style="text-align:right;">
0.0166791
</td>
<td style="text-align:right;">
-0.2447439
</td>
<td style="text-align:right;">
0.6143911
</td>
<td style="text-align:right;">
0.1609764
</td>
</tr>
<tr>
<td style="text-align:left;">
free.sulfur.dioxide
</td>
<td style="text-align:right;">
0.4309140
</td>
<td style="text-align:right;">
0.0719326
</td>
<td style="text-align:right;">
0.1342239
</td>
<td style="text-align:right;">
-0.3572789
</td>
<td style="text-align:right;">
0.2235323
</td>
<td style="text-align:right;">
-0.3400514
</td>
</tr>
</tbody>
</table>

    ## Importance of first k=6 (out of 11) components:
    ##                           PC1    PC2    PC3     PC4     PC5     PC6
    ## Standard deviation     1.7407 1.5792 1.2475 0.98517 0.84845 0.77930
    ## Proportion of Variance 0.2754 0.2267 0.1415 0.08823 0.06544 0.05521
    ## Cumulative Proportion  0.2754 0.5021 0.6436 0.73187 0.79732 0.85253

![](ECO395M-exercise-4_files/figure-markdown_strict/1.2.2-1.png)

![](ECO395M-exercise-4_files/figure-markdown_strict/1.2.3-1.png)

## 2) Market segmentation

Method to be used is `K-means clustering`. With this method, we will be
able to detect interesting market segments that seem to be exceptional
within NutrientH20’s social-media audience.

Read the `social_marketing.csv` and let’s take a look for the 36
different categories
<table class=" lightable-minimal" style="font-family: &quot;Trebuchet MS&quot;, verdana, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
36 different categories of interest
</caption>
<tbody>
<tr>
<td style="text-align:left;">
chatter
</td>
<td style="text-align:left;">
current\_events
</td>
<td style="text-align:left;">
travel
</td>
<td style="text-align:left;">
photo\_sharing
</td>
<td style="text-align:left;">
uncategorized
</td>
<td style="text-align:left;">
tv\_film
</td>
</tr>
<tr>
<td style="text-align:left;">
sports\_fandom
</td>
<td style="text-align:left;">
politics
</td>
<td style="text-align:left;">
food
</td>
<td style="text-align:left;">
family
</td>
<td style="text-align:left;">
home\_and\_garden
</td>
<td style="text-align:left;">
music
</td>
</tr>
<tr>
<td style="text-align:left;">
news
</td>
<td style="text-align:left;">
online\_gaming
</td>
<td style="text-align:left;">
shopping
</td>
<td style="text-align:left;">
health\_nutrition
</td>
<td style="text-align:left;">
college\_uni
</td>
<td style="text-align:left;">
sports\_playing
</td>
</tr>
<tr>
<td style="text-align:left;">
cooking
</td>
<td style="text-align:left;">
eco
</td>
<td style="text-align:left;">
computers
</td>
<td style="text-align:left;">
business
</td>
<td style="text-align:left;">
outdoors
</td>
<td style="text-align:left;">
crafts
</td>
</tr>
<tr>
<td style="text-align:left;">
automotive
</td>
<td style="text-align:left;">
art
</td>
<td style="text-align:left;">
religion
</td>
<td style="text-align:left;">
beauty
</td>
<td style="text-align:left;">
parenting
</td>
<td style="text-align:left;">
dating
</td>
</tr>
<tr>
<td style="text-align:left;">
school
</td>
<td style="text-align:left;">
personal\_fitness
</td>
<td style="text-align:left;">
fashion
</td>
<td style="text-align:left;">
small\_business
</td>
<td style="text-align:left;">
spam
</td>
<td style="text-align:left;">
adult
</td>
</tr>
</tbody>
</table>

With K-means clustering, we can cluster these categories, for example,
“physical wellness” can be one cluster containing `personal_fitness`,
`health_nutrition`, `outdoors`.

As mentioned in the question, we can check there are categories like
`spam`, `adult`, `uncategorized`, and I will remove `spam` and `adult`
to clean our dataset.

\`\`\`{2.1.1.2, message=FALSE, echo=FALSE, warning=FALSE}

# drop first column, which user has labeled as random 9-digit code

X=data\[,-1\] \# drop spam and adult column which slip through the data
X=X\[,-(35:36)\] \# center and scale X=scale(X, center=TRUE, scale=TRUE)
\# Extract the centers and scales from the rescaled data (which are
named attributes) mu = attr(X,“scaled:center”) sigma =
attr(X,“scaled:scale”)

\`\`\`

After cleaning/centering/scaling the data, I will start with correlation
plot for k-means clustering, as correlation plot can visualize which
categories in the dataset are strongly correlated each other, and also
can identify which categories have similar scales.

![](ECO395M-exercise-4_files/figure-markdown_strict/2.1.2-1.png)

As there’s so many variables, I will sort highest correlations.
![](ECO395M-exercise-4_files/figure-markdown_strict/2.1.3-1.png)
<table class=" lightable-minimal" style="font-family: &quot;Trebuchet MS&quot;, verdana, sans-serif; margin-left: auto; margin-right: auto;">
<caption>
Highest correlation among categories
</caption>
<thead>
<tr>
<th style="text-align:left;">
Var1
</th>
<th style="text-align:left;">
Var2
</th>
<th style="text-align:right;">
Freq
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
free.sulfur.dioxide
</td>
<td style="text-align:left;">
total.sulfur.dioxide
</td>
<td style="text-align:right;">
0.7209341
</td>
</tr>
<tr>
<td style="text-align:left;">
density
</td>
<td style="text-align:left;">
alcohol
</td>
<td style="text-align:right;">
-0.6867454
</td>
</tr>
</tbody>
</table>

As you can see, `health_nutrition` and `personal_fitness` has the
highest correlation and this is exactly what I thought would be in the
same cluster - “physical wellness”.

We’ve finished previewing for k-means clustering with correlation plot,
and we’ll start analyzing with k-means clustering.

### K-means clustering

First, will start from choosing optimal K, the amount of clusters. Below
is Elbow plot. Elbow plot used to determine the optimal number of
clustering. The plot displays within-cluster sum of squares(WSS) as a
function of the number of clusters.

![](ECO395M-exercise-4_files/figure-markdown_strict/2.2.1-1.png)

10 seems to me to be the elbow point, so we’ll use 10 for k.

We can get surface-level information about market segments for
NutrientH20.

<table class="kable_wrapper lightable-minimal table" style="font-family: &quot;Trebuchet MS&quot;, verdana, sans-serif; margin-left: auto; margin-right: auto; width: auto !important; ">
<tbody>
<tr>
<td>
<table>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
cluster1
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
total.sulfur.dioxide
</td>
<td style="text-align:right;">
117.545709
</td>
</tr>
<tr>
<td style="text-align:left;">
free.sulfur.dioxide
</td>
<td style="text-align:right;">
24.000933
</td>
</tr>
<tr>
<td style="text-align:left;">
alcohol
</td>
<td style="text-align:right;">
10.395134
</td>
</tr>
<tr>
<td style="text-align:left;">
fixed.acidity
</td>
<td style="text-align:right;">
7.372854
</td>
</tr>
<tr>
<td style="text-align:left;">
residual.sugar
</td>
<td style="text-align:right;">
4.212313
</td>
</tr>
</tbody>
</table>
</td>
<td>
<table>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
cluster2
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
total.sulfur.dioxide
</td>
<td style="text-align:right;">
35.481203
</td>
</tr>
<tr>
<td style="text-align:left;">
free.sulfur.dioxide
</td>
<td style="text-align:right;">
11.812030
</td>
</tr>
<tr>
<td style="text-align:left;">
fixed.acidity
</td>
<td style="text-align:right;">
11.313158
</td>
</tr>
<tr>
<td style="text-align:left;">
alcohol
</td>
<td style="text-align:right;">
10.616416
</td>
</tr>
<tr>
<td style="text-align:left;">
pH
</td>
<td style="text-align:right;">
3.142669
</td>
</tr>
</tbody>
</table>
</td>
<td>
<table>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
cluster3
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
total.sulfur.dioxide
</td>
<td style="text-align:right;">
130.168344
</td>
</tr>
<tr>
<td style="text-align:left;">
free.sulfur.dioxide
</td>
<td style="text-align:right;">
32.718680
</td>
</tr>
<tr>
<td style="text-align:left;">
alcohol
</td>
<td style="text-align:right;">
10.632696
</td>
</tr>
<tr>
<td style="text-align:left;">
fixed.acidity
</td>
<td style="text-align:right;">
6.311689
</td>
</tr>
<tr>
<td style="text-align:left;">
pH
</td>
<td style="text-align:right;">
3.375112
</td>
</tr>
</tbody>
</table>
</td>
<td>
<table>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
cluster4
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
total.sulfur.dioxide
</td>
<td style="text-align:right;">
164.095580
</td>
</tr>
<tr>
<td style="text-align:left;">
free.sulfur.dioxide
</td>
<td style="text-align:right;">
41.548985
</td>
</tr>
<tr>
<td style="text-align:left;">
residual.sugar
</td>
<td style="text-align:right;">
14.499403
</td>
</tr>
<tr>
<td style="text-align:left;">
alcohol
</td>
<td style="text-align:right;">
9.276563
</td>
</tr>
<tr>
<td style="text-align:left;">
fixed.acidity
</td>
<td style="text-align:right;">
7.129630
</td>
</tr>
</tbody>
</table>
</td>
<td>
<table>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
cluster5
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
total.sulfur.dioxide
</td>
<td style="text-align:right;">
46.865140
</td>
</tr>
<tr>
<td style="text-align:left;">
free.sulfur.dioxide
</td>
<td style="text-align:right;">
15.791985
</td>
</tr>
<tr>
<td style="text-align:left;">
alcohol
</td>
<td style="text-align:right;">
10.222540
</td>
</tr>
<tr>
<td style="text-align:left;">
fixed.acidity
</td>
<td style="text-align:right;">
7.279262
</td>
</tr>
<tr>
<td style="text-align:left;">
pH
</td>
<td style="text-align:right;">
3.379644
</td>
</tr>
</tbody>
</table>
</td>
<td>
<table>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
cluster6
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
total.sulfur.dioxide
</td>
<td style="text-align:right;">
54.350844
</td>
</tr>
<tr>
<td style="text-align:left;">
free.sulfur.dioxide
</td>
<td style="text-align:right;">
17.142589
</td>
</tr>
<tr>
<td style="text-align:left;">
alcohol
</td>
<td style="text-align:right;">
10.516135
</td>
</tr>
<tr>
<td style="text-align:left;">
fixed.acidity
</td>
<td style="text-align:right;">
8.385178
</td>
</tr>
<tr>
<td style="text-align:left;">
pH
</td>
<td style="text-align:right;">
3.293189
</td>
</tr>
</tbody>
</table>
</td>
<td>
<table>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
cluster7
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
total.sulfur.dioxide
</td>
<td style="text-align:right;">
137.403670
</td>
</tr>
<tr>
<td style="text-align:left;">
free.sulfur.dioxide
</td>
<td style="text-align:right;">
39.839450
</td>
</tr>
<tr>
<td style="text-align:left;">
alcohol
</td>
<td style="text-align:right;">
9.468807
</td>
</tr>
<tr>
<td style="text-align:left;">
fixed.acidity
</td>
<td style="text-align:right;">
6.966055
</td>
</tr>
<tr>
<td style="text-align:left;">
residual.sugar
</td>
<td style="text-align:right;">
4.346789
</td>
</tr>
</tbody>
</table>
</td>
<td>
<table>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
cluster8
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
total.sulfur.dioxide
</td>
<td style="text-align:right;">
181.576327
</td>
</tr>
<tr>
<td style="text-align:left;">
free.sulfur.dioxide
</td>
<td style="text-align:right;">
52.929203
</td>
</tr>
<tr>
<td style="text-align:left;">
alcohol
</td>
<td style="text-align:right;">
9.823138
</td>
</tr>
<tr>
<td style="text-align:left;">
residual.sugar
</td>
<td style="text-align:right;">
8.487113
</td>
</tr>
<tr>
<td style="text-align:left;">
fixed.acidity
</td>
<td style="text-align:right;">
6.777102
</td>
</tr>
</tbody>
</table>
</td>
<td>
<table>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
cluster9
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
total.sulfur.dioxide
</td>
<td style="text-align:right;">
108.803172
</td>
</tr>
<tr>
<td style="text-align:left;">
free.sulfur.dioxide
</td>
<td style="text-align:right;">
29.220149
</td>
</tr>
<tr>
<td style="text-align:left;">
alcohol
</td>
<td style="text-align:right;">
12.266076
</td>
</tr>
<tr>
<td style="text-align:left;">
fixed.acidity
</td>
<td style="text-align:right;">
6.600280
</td>
</tr>
<tr>
<td style="text-align:left;">
residual.sugar
</td>
<td style="text-align:right;">
3.272901
</td>
</tr>
</tbody>
</table>
</td>
<td>
<table>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
cluster10
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
total.sulfur.dioxide
</td>
<td style="text-align:right;">
52.625000
</td>
</tr>
<tr>
<td style="text-align:left;">
free.sulfur.dioxide
</td>
<td style="text-align:right;">
15.041667
</td>
</tr>
<tr>
<td style="text-align:left;">
alcohol
</td>
<td style="text-align:right;">
9.420833
</td>
</tr>
<tr>
<td style="text-align:left;">
fixed.acidity
</td>
<td style="text-align:right;">
8.441667
</td>
</tr>
<tr>
<td style="text-align:left;">
pH
</td>
<td style="text-align:right;">
3.064583
</td>
</tr>
</tbody>
</table>
</td>
</tr>
</tbody>
</table>
Above is the table for the highest five categories for each clusters in
total of 10 clusters. It appears that there are distinct groups of
categories in each clusters. Cluster with college\_uni, online\_gaming,
sports\_playing in top 5 categories will explain NutrientH20’s
social-media audience is male college students whose in their early 20s.
Cluster with news, politics, automotive, sports\_fandom in top 5
categories will explain NutrientH20’s social-media audience can be guys
in their 30s, 40s. Cluster with health\_nutrition, personal\_fitness,
outdoors in top 5 categories will explain NutrientH20’s social-media
audience is people interested in exercise and health. With this result,
NutrientH20 can do marketing through gyms, product advertisements in
men’s magazines, or selling products in college vending machines.

## 3) Association rules for grocery purchases

### Analysis

`groceries.txt` file contains a total of 9,835 unique shopping baskets.
We frst went through some data wrangling process before conducting
Market Basket Analysis using the “arules” package. As for the
thresholds, we chose support of .001, confidence of .5, and maxlen of
10. A relatively low support of .001 was chosen because we wanted to
capture as many items as possible from the dataset. Confidence of .5 was
chosen to sort out weak associations. Lastly, we limited the maximum
number of items per item set to be 10 to account for as many possible
grocery combinations as possible. Running the algorithm using the above
threshold resulted in 5,668 rules, which we thought was enough for this
analysis. Below are two plots showing the resulting rules; the first is
plotted between support and lift, while the second is between support
and confidence.

![](ECO395M-exercise-4_files/figure-markdown_strict/problem%203-1-1.png)![](ECO395M-exercise-4_files/figure-markdown_strict/problem%203-1-2.png)

### Findings

Below is a table that shows the top ten rules with the highest
confidence. Confidence shows the probability of having item(s) on the
RHS given those on the LHS are purchased. You can see that out of the
top ten rules, the most frequent RHS items are `whole milk` and
`other vegetables`. However, the association rules here are not very
interesting nor revealing. Take
`{canned fish,hygiene articles} -> {whole milk}` as an example.
Intuitively, buying canned fish and hygiene articles doesn’t seem to
have anything to do with buying whole milk. However, this this is still
at the top of the list simply because whole milk gets bought the most
frequently when people go grocery shopping, regardless of what other
items they purchase. To see more relevant and revealing association
rules, let’s look at a list with the highest lift.

<table>
<caption>
Top 10 rules with the highest confidence
</caption>
<thead>
<tr>
<th style="text-align:left;">
LHS
</th>
<th style="text-align:left;">
RHS
</th>
<th style="text-align:right;">
support
</th>
<th style="text-align:right;">
confidence
</th>
<th style="text-align:right;">
coverage
</th>
<th style="text-align:right;">
lift
</th>
<th style="text-align:right;">
count
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
{rice,sugar}
</td>
<td style="text-align:left;">
{whole milk}
</td>
<td style="text-align:right;">
0.0012200
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
0.0012200
</td>
<td style="text-align:right;">
3.914047
</td>
<td style="text-align:right;">
12
</td>
</tr>
<tr>
<td style="text-align:left;">
{canned fish,hygiene articles}
</td>
<td style="text-align:left;">
{whole milk}
</td>
<td style="text-align:right;">
0.0011183
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
0.0011183
</td>
<td style="text-align:right;">
3.914047
</td>
<td style="text-align:right;">
11
</td>
</tr>
<tr>
<td style="text-align:left;">
{butter,rice,root vegetables}
</td>
<td style="text-align:left;">
{whole milk}
</td>
<td style="text-align:right;">
0.0010167
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
0.0010167
</td>
<td style="text-align:right;">
3.914047
</td>
<td style="text-align:right;">
10
</td>
</tr>
<tr>
<td style="text-align:left;">
{flour,root vegetables,whipped/sour cream}
</td>
<td style="text-align:left;">
{whole milk}
</td>
<td style="text-align:right;">
0.0017283
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
0.0017283
</td>
<td style="text-align:right;">
3.914047
</td>
<td style="text-align:right;">
17
</td>
</tr>
<tr>
<td style="text-align:left;">
{butter,domestic eggs,soft cheese}
</td>
<td style="text-align:left;">
{whole milk}
</td>
<td style="text-align:right;">
0.0010167
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
0.0010167
</td>
<td style="text-align:right;">
3.914047
</td>
<td style="text-align:right;">
10
</td>
</tr>
<tr>
<td style="text-align:left;">
{citrus fruit,root vegetables,soft cheese}
</td>
<td style="text-align:left;">
{other vegetables}
</td>
<td style="text-align:right;">
0.0010167
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
0.0010167
</td>
<td style="text-align:right;">
5.168681
</td>
<td style="text-align:right;">
10
</td>
</tr>
<tr>
<td style="text-align:left;">
{butter,hygiene articles,pip fruit}
</td>
<td style="text-align:left;">
{whole milk}
</td>
<td style="text-align:right;">
0.0010167
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
0.0010167
</td>
<td style="text-align:right;">
3.914047
</td>
<td style="text-align:right;">
10
</td>
</tr>
<tr>
<td style="text-align:left;">
{hygiene articles,root vegetables,whipped/sour cream}
</td>
<td style="text-align:left;">
{whole milk}
</td>
<td style="text-align:right;">
0.0010167
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
0.0010167
</td>
<td style="text-align:right;">
3.914047
</td>
<td style="text-align:right;">
10
</td>
</tr>
<tr>
<td style="text-align:left;">
{hygiene articles,pip fruit,root vegetables}
</td>
<td style="text-align:left;">
{whole milk}
</td>
<td style="text-align:right;">
0.0010167
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
0.0010167
</td>
<td style="text-align:right;">
3.914047
</td>
<td style="text-align:right;">
10
</td>
</tr>
<tr>
<td style="text-align:left;">
{cream cheese ,domestic eggs,sugar}
</td>
<td style="text-align:left;">
{whole milk}
</td>
<td style="text-align:right;">
0.0011183
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
0.0011183
</td>
<td style="text-align:right;">
3.914047
</td>
<td style="text-align:right;">
11
</td>
</tr>
</tbody>
</table>

Below is a table showing the top ten rules with the highest lift. Lift
is different from confidence in that it is the ratio between confidence
and expected confidence. In other words, lift measures the relative
strength of association between LHS and RHS. It takes care of the high
frequency issue of whole milk purchase we observed above. Lift &gt; 1
indicates that the association rule improves the chances of outcome,
where as lift &lt; 1 reveals that the model lowers the chance of the
outcome. Lift = 1 does not have any effect on the outcome. The result
here is much more interesting and informative.

`{popcorn,soda} -> {salty snack}` Here, it seems like people are getting
ready for a movie night. People who buy popcorn and soda are likely to
buy other salty snacks. Thus, the model makes sense.

`{ham,processed cheese} -> {white bread}`These are ingredients to make a
quick sandwich. People who buy ham and processed cheese are likely to
buy white bread to make a sandwich. Hence, the rule makes sense again.

<table>
<caption>
Top 10 rules with the highest lift
</caption>
<thead>
<tr>
<th style="text-align:left;">
LHS
</th>
<th style="text-align:left;">
RHS
</th>
<th style="text-align:right;">
support
</th>
<th style="text-align:right;">
confidence
</th>
<th style="text-align:right;">
coverage
</th>
<th style="text-align:right;">
lift
</th>
<th style="text-align:right;">
count
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
{Instant food products,soda}
</td>
<td style="text-align:left;">
{hamburger meat}
</td>
<td style="text-align:right;">
0.0012200
</td>
<td style="text-align:right;">
0.6315789
</td>
<td style="text-align:right;">
0.0019317
</td>
<td style="text-align:right;">
18.99759
</td>
<td style="text-align:right;">
12
</td>
</tr>
<tr>
<td style="text-align:left;">
{popcorn,soda}
</td>
<td style="text-align:left;">
{salty snack}
</td>
<td style="text-align:right;">
0.0012200
</td>
<td style="text-align:right;">
0.6315789
</td>
<td style="text-align:right;">
0.0019317
</td>
<td style="text-align:right;">
16.69949
</td>
<td style="text-align:right;">
12
</td>
</tr>
<tr>
<td style="text-align:left;">
{baking powder,flour}
</td>
<td style="text-align:left;">
{sugar}
</td>
<td style="text-align:right;">
0.0010167
</td>
<td style="text-align:right;">
0.5555556
</td>
<td style="text-align:right;">
0.0018300
</td>
<td style="text-align:right;">
16.40974
</td>
<td style="text-align:right;">
10
</td>
</tr>
<tr>
<td style="text-align:left;">
{ham,processed cheese}
</td>
<td style="text-align:left;">
{white bread}
</td>
<td style="text-align:right;">
0.0019317
</td>
<td style="text-align:right;">
0.6333333
</td>
<td style="text-align:right;">
0.0030500
</td>
<td style="text-align:right;">
15.04702
</td>
<td style="text-align:right;">
19
</td>
</tr>
<tr>
<td style="text-align:left;">
{Instant food products,whole milk}
</td>
<td style="text-align:left;">
{hamburger meat}
</td>
<td style="text-align:right;">
0.0015250
</td>
<td style="text-align:right;">
0.5000000
</td>
<td style="text-align:right;">
0.0030500
</td>
<td style="text-align:right;">
15.03976
</td>
<td style="text-align:right;">
15
</td>
</tr>
<tr>
<td style="text-align:left;">
{curd,other vegetables,whipped/sour cream,yogurt}
</td>
<td style="text-align:left;">
{cream cheese }
</td>
<td style="text-align:right;">
0.0010167
</td>
<td style="text-align:right;">
0.5882353
</td>
<td style="text-align:right;">
0.0017283
</td>
<td style="text-align:right;">
14.83560
</td>
<td style="text-align:right;">
10
</td>
</tr>
<tr>
<td style="text-align:left;">
{domestic eggs,processed cheese}
</td>
<td style="text-align:left;">
{white bread}
</td>
<td style="text-align:right;">
0.0011183
</td>
<td style="text-align:right;">
0.5238095
</td>
<td style="text-align:right;">
0.0021350
</td>
<td style="text-align:right;">
12.44490
</td>
<td style="text-align:right;">
11
</td>
</tr>
<tr>
<td style="text-align:left;">
{other vegetables,tropical fruit,white bread,yogurt}
</td>
<td style="text-align:left;">
{butter}
</td>
<td style="text-align:right;">
0.0010167
</td>
<td style="text-align:right;">
0.6666667
</td>
<td style="text-align:right;">
0.0015250
</td>
<td style="text-align:right;">
12.03180
</td>
<td style="text-align:right;">
10
</td>
</tr>
<tr>
<td style="text-align:left;">
{hamburger meat,whipped/sour cream,yogurt}
</td>
<td style="text-align:left;">
{butter}
</td>
<td style="text-align:right;">
0.0010167
</td>
<td style="text-align:right;">
0.6250000
</td>
<td style="text-align:right;">
0.0016267
</td>
<td style="text-align:right;">
11.27982
</td>
<td style="text-align:right;">
10
</td>
</tr>
<tr>
<td style="text-align:left;">
{domestic eggs,other vegetables,tropical fruit,whole milk,yogurt}
</td>
<td style="text-align:left;">
{butter}
</td>
<td style="text-align:right;">
0.0010167
</td>
<td style="text-align:right;">
0.6250000
</td>
<td style="text-align:right;">
0.0016267
</td>
<td style="text-align:right;">
11.27982
</td>
<td style="text-align:right;">
10
</td>
</tr>
</tbody>
</table>

The last plot is a graph-visualization representing the association
rules. Each item in the LHS is connected with to the RHS item, and the
arrows indicate the direction of the relationship. To avoid over-crowded
plot, we have limited to rules with lift &gt; 10.

![](ECO395M-exercise-4_files/figure-markdown_strict/problem%203-4-1.png)
