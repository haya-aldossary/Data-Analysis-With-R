---
title: "TASI (Tadawul All Share Index) Exploration by Haya"
output: html_document
---

# title: "TASI (Tadawul All Share Index) Exploration by Haya"










```
## Error in parse_block(g[-1], g[1], params.src): duplicate label 'setup'
```

```
## Error in readLines(con): cannot open the connection
```


# History behind TASI.csv:

This data is collected by DirectFN Pro software (v 0.10.003.09) which is a client-server based real-time market information dissemination and trade solution, targeted at active traders and sophisticated investors and connects to  Regional and International stock exchanges. [Press here to visit](http://download.mubasher.net/downloads/en/download.aspx).

# Data wrangling and cleaning:

I have did a little improvement in headers name to be understandable and also avoid problematical characters like ( .%$& etc.).

to change some headers name. ex: %.Ch to Change_Percentage




As I mentioned before this data is auto generated so no NA or Mismatching data.

# A stream-of-consciousness analysis and exploration of the data.

This report explores a dataset containing changing points of the main index in Saudi Arabia stock market (TASI) and observation for approximately 6378 days from  1994 to 2017. every row in the data set give a detailed summary of TASI index in a selected day.  It contains 10 headers ( variable ) as following:

```
##  [1] "Date"              "Open"              "High"             
##  [4] "Low"               "Closed"            "Change_Percentage"
##  [7] "Change"            "Previous_Closed"   "Volume"           
## [10] "Turnover"
```

```
## 'data.frame':	6378 obs. of  10 variables:
##  $ Date             : Factor w/ 6378 levels "1994/01/26","1994/01/29",..: 1 2 3 4 5 6 7 8 9 10 ...
##  $ Open             : num  1752 1752 1751 1753 1752 ...
##  $ High             : num  1752 1752 1753 1753 1752 ...
##  $ Low              : num  1752 1751 1751 1752 1750 ...
##  $ Closed           : num  1752 1751 1753 1752 1750 ...
##  $ Change_Percentage: num  100 -0.05 0.1 -0.02 -0.15 -0.01 -0.12 -0.29 -0.57 -0.04 ...
##  $ Change           : num  1751.71 -0.8 1.68 -0.33 -2.56 ...
##  $ Previous_Closed  : num  0 1752 1751 1753 1752 ...
##  $ Volume           : int  312907 204831 180425 212105 176595 253727 64461 285281 249268 198632 ...
##  $ Turnover         : num  59195719 43518035 34072368 42559328 40531385 ...
```
A quick details of the meaning of each variables :

1-  *Date:*  A particular data of trading except weekend and holidays.
2-  *Open:* Opining point.
3-  *High:* Highest point.
4-  *Low:* Lowest point
5-  *Closed:* Closing point
6-  *Change_Percentage:* Change percentage.
7-  *Change:* Change points.
8-  *Previous_Closed:* Previous close.
9-  *Volume:* Total quantity of shares or contracts traded for a specified security. It can be measured on any type of security traded during a trading day
10- *Turnover:* Total price amount of sale and buy.




Also, I have converted the data format to %y-%m-%d just to avoid any error later on. furthermore, I have changed weekly break point to Sunday as it is in Kingdom of Saudi Arabia.

convert date variable from factor to date format:




using sapply() to get MEAN OF DF (TASI) or summary() can be used to get full STATISTICAL summary.


```
##       Date                 Open            High            Low       
##  Min.   :1994-01-26   Min.   : 1141   Min.   : 1143   Min.   : 1141  
##  1st Qu.:1999-06-30   1st Qu.: 1893   1st Qu.: 1897   1st Qu.: 1887  
##  Median :2004-10-22   Median : 5533   Median : 5602   Median : 5455  
##  Mean   :2005-03-16   Mean   : 5313   Mean   : 5351   Mean   : 5268  
##  3rd Qu.:2010-11-28   3rd Qu.: 7436   3rd Qu.: 7484   3rd Qu.: 7351  
##  Max.   :2017-04-12   Max.   :20635   Max.   :20967   Max.   :20369  
##      Closed      Change_Percentage     Change      Previous_Closed
##  Min.   : 1141   Min.   : -9.8     Min.   :-1458   Min.   :    0  
##  1st Qu.: 1894   1st Qu.: -0.4     1st Qu.:  -12   1st Qu.: 1853  
##  Median : 5535   Median :  0.1     Median :    2   Median : 5465  
##  Mean   : 5314   Mean   :  0.0     Mean   :    1   Mean   : 5281  
##  3rd Qu.: 7438   3rd Qu.:  0.5     3rd Qu.:   21   3rd Qu.: 7382  
##  Max.   :20635   Max.   :100.0     Max.   : 1752   Max.   :20635  
##      Volume            Turnover            Year          
##  Min.   :2.55e+03   Min.   :6.51e+04   Length:6378       
##  1st Qu.:1.25e+06   1st Qu.:1.52e+08   Class :character  
##  Median :3.19e+07   Median :2.64e+09   Mode  :character  
##  Mean   :1.01e+08   Mean   :4.07e+09                     
##  3rd Qu.:1.85e+08   3rd Qu.:5.84e+09                     
##  Max.   :1.01e+09   Max.   :4.63e+10                     
##     Month               Day           
##  Length:6378        Length:6378       
##  Class :character   Class :character  
##  Mode  :character   Mode  :character  
##                                       
##                                       
## 
```


![plot of chunk unnamed-chunk-8](figure/unnamed-chunk-8-1.png)

![plot of chunk unnamed-chunk-9](figure/unnamed-chunk-9-1.png)
![plot of chunk unnamed-chunk-10](figure/unnamed-chunk-10-1.png)

![plot of chunk unnamed-chunk-11](figure/unnamed-chunk-11-1.png)



![plot of chunk unnamed-chunk-12](figure/unnamed-chunk-12-1.png)


# Comparing between changing percentage per year:
![plot of chunk unnamed-chunk-13](figure/unnamed-chunk-13-1.png)
![plot of chunk unnamed-chunk-14](figure/unnamed-chunk-14-1.png)![plot of chunk unnamed-chunk-14](figure/unnamed-chunk-14-2.png)

from the pervious charts I noticed the following:
bar plot
- Highest change in TASI was in 2003-2004-2005 and lowest change in 2006 and 2008
- Low turnover in trinding in 2001 and 2002 which lead to very little increased in index change.
- Many outliers and Overlapping data-points
box plot:
- TASI reached the Highest points during 2005 and 2006.
- TASI reached the lowest points during 1995,1996 and 1994 respectively.
- very high value in colume (Change) in 1994

Investigating my thoughts through statistic.


```
## TASI$Year: 1994
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##     -58      -7      -1       5       3    1750 
## -------------------------------------------------------- 
## TASI$Year: 1995
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -39.6    -3.8    -0.4     0.3     3.9    49.3 
## -------------------------------------------------------- 
## TASI$Year: 1996
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -31.00   -2.82    0.25    0.55    4.00   23.10 
## -------------------------------------------------------- 
## TASI$Year: 1997
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -51.8    -3.3     1.5     1.4     6.3    30.6 
## -------------------------------------------------------- 
## TASI$Year: 1998
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -66.9    -8.9    -0.8    -1.8     6.6    46.8 
## -------------------------------------------------------- 
## TASI$Year: 1999
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -37.0    -5.1     1.8     2.1     8.4    61.9 
## -------------------------------------------------------- 
## TASI$Year: 2000
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -53.8    -5.8     0.8     0.8     7.4    57.4 
## -------------------------------------------------------- 
## TASI$Year: 2001
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -115.0    -6.5     1.8     0.6     8.1    54.2 
## -------------------------------------------------------- 
## TASI$Year: 2002
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -72.7    -9.1     0.0     0.3     8.7   123.0 
## -------------------------------------------------------- 
## TASI$Year: 2003
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -292     -11       5       6      24     328 
## -------------------------------------------------------- 
## TASI$Year: 2004
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -447     -10      14      13      42     388 
## -------------------------------------------------------- 
## TASI$Year: 2005
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -511     -50      30      28     102     528 
## -------------------------------------------------------- 
## TASI$Year: 2006
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -1460    -176      23     -33     152    1030 
## -------------------------------------------------------- 
## TASI$Year: 2007
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -521     -49      19      14      75     518 
## -------------------------------------------------------- 
## TASI$Year: 2008
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -1000     -93      -5     -25      68     551 
## -------------------------------------------------------- 
## TASI$Year: 2009
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -235.0   -36.5     7.1     5.3    50.9   249.0 
## -------------------------------------------------------- 
## TASI$Year: 2010
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -417     -22       4       2      30     314 
## -------------------------------------------------------- 
## TASI$Year: 2011
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -431     -22       2      -1      32     387 
## -------------------------------------------------------- 
## TASI$Year: 2012
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -294.0   -24.6     5.5     1.4    32.4   234.0 
## -------------------------------------------------------- 
## TASI$Year: 2013
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -332     -15       8       7      32     221 
## -------------------------------------------------------- 
## TASI$Year: 2014
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -706     -24       9      -1      43     682 
## -------------------------------------------------------- 
## TASI$Year: 2015
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -550     -62       3      -6      52     518 
## -------------------------------------------------------- 
## TASI$Year: 2016
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -318     -41       3       0      52     195 
## -------------------------------------------------------- 
## TASI$Year: 2017
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -113.0   -26.6     3.0    -1.5    27.4   114.0
```

In trading January 1994, I noticed that the rate of changing in TASI index is 100%! very intersting value. Zooming to that month:


```
##       Date                 Open           High           Low      
##  Min.   :1994-01-26   Min.   :1751   Min.   :1752   Min.   :1751  
##  1st Qu.:1994-01-28   1st Qu.:1752   1st Qu.:1752   1st Qu.:1751  
##  Median :1994-01-29   Median :1752   Median :1752   Median :1751  
##  Mean   :1994-01-29   Mean   :1752   Mean   :1752   Mean   :1751  
##  3rd Qu.:1994-01-30   3rd Qu.:1752   3rd Qu.:1753   3rd Qu.:1752  
##  Max.   :1994-01-31   Max.   :1753   Max.   :1753   Max.   :1752  
##      Closed     Change_Percentage     Change     Previous_Closed
##  Min.   :1751   Min.   :  0.0     Min.   :  -1   Min.   :   0   
##  1st Qu.:1752   1st Qu.:  0.0     1st Qu.:   0   1st Qu.:1313   
##  Median :1752   Median :  0.0     Median :   1   Median :1751   
##  Mean   :1752   Mean   : 25.0     Mean   : 438   Mean   :1314   
##  3rd Qu.:1752   3rd Qu.: 25.1     3rd Qu.: 439   3rd Qu.:1752   
##  Max.   :1753   Max.   :100.0     Max.   :1752   Max.   :1753   
##      Volume          Turnover            Year              Month          
##  Min.   :180425   Min.   :34072368   Length:4           Length:4          
##  1st Qu.:198730   1st Qu.:40437588   Class :character   Class :character  
##  Median :208468   Median :43038682   Mode  :character   Mode  :character  
##  Mean   :227567   Mean   :44836362                                        
##  3rd Qu.:237306   3rd Qu.:47437456                                        
##  Max.   :312907   Max.   :59195719                                        
##      Day           
##  Length:4          
##  Class :character  
##  Mode  :character  
##                    
##                    
## 
```

![plot of chunk unnamed-chunk-17](figure/unnamed-chunk-17-1.png)

So, The reason behind the high value in January 1994 is TASI index increasd 100% points. changing the scale is not enough to refine plot as the onther values are too small comparing with day 26
lets get the info of that row: 

```
##         Date Open High  Low Closed X..Chg. Change Prev..Closed Volume
## 1 1994/01/26 1752 1752 1752   1752     100   1752            0 312907
##   Turnover Year Month Day
## 1 59195719 1994    01  26
```
It is impossible increased where Open and Closed columns values are equal! Changes column represent the change between open and closed point. In this row open = 1751.71 and closed = 1751.71 ->  1751.71 - 1751.71 = 0 NOT 1751.71 and the actual percentage change = 0% NOT 100% as shown !!! 
I decide to remove ((after I did a random chicking with no similar problem at result.))
![plot of chunk unnamed-chunk-19](figure/unnamed-chunk-19-1.png)


![plot of chunk unnamed-chunk-20](figure/unnamed-chunk-20-1.png)

After did some investigation about the high data on January 1994, now it is clear that the 1994 was Reaping profits where the TASI index taking clearly negative way comparitively with the volume of increasing.





```
## TASI$Year: 1994
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##     -58      -7      -1       5       3    1750 
## -------------------------------------------------------- 
## TASI$Year: 1995
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -39.6    -3.8    -0.4     0.3     3.9    49.3 
## -------------------------------------------------------- 
## TASI$Year: 1996
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -31.00   -2.82    0.25    0.55    4.00   23.10 
## -------------------------------------------------------- 
## TASI$Year: 1997
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -51.8    -3.3     1.5     1.4     6.3    30.6 
## -------------------------------------------------------- 
## TASI$Year: 1998
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -66.9    -8.9    -0.8    -1.8     6.6    46.8 
## -------------------------------------------------------- 
## TASI$Year: 1999
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -37.0    -5.1     1.8     2.1     8.4    61.9 
## -------------------------------------------------------- 
## TASI$Year: 2000
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -53.8    -5.8     0.8     0.8     7.4    57.4 
## -------------------------------------------------------- 
## TASI$Year: 2001
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -115.0    -6.5     1.8     0.6     8.1    54.2 
## -------------------------------------------------------- 
## TASI$Year: 2002
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -72.7    -9.1     0.0     0.3     8.7   123.0 
## -------------------------------------------------------- 
## TASI$Year: 2003
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -292     -11       5       6      24     328 
## -------------------------------------------------------- 
## TASI$Year: 2004
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -447     -10      14      13      42     388 
## -------------------------------------------------------- 
## TASI$Year: 2005
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -511     -50      30      28     102     528 
## -------------------------------------------------------- 
## TASI$Year: 2006
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -1460    -176      23     -33     152    1030 
## -------------------------------------------------------- 
## TASI$Year: 2007
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -521     -49      19      14      75     518 
## -------------------------------------------------------- 
## TASI$Year: 2008
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -1000     -93      -5     -25      68     551 
## -------------------------------------------------------- 
## TASI$Year: 2009
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -235.0   -36.5     7.1     5.3    50.9   249.0 
## -------------------------------------------------------- 
## TASI$Year: 2010
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -417     -22       4       2      30     314 
## -------------------------------------------------------- 
## TASI$Year: 2011
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -431     -22       2      -1      32     387 
## -------------------------------------------------------- 
## TASI$Year: 2012
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -294.0   -24.6     5.5     1.4    32.4   234.0 
## -------------------------------------------------------- 
## TASI$Year: 2013
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -332     -15       8       7      32     221 
## -------------------------------------------------------- 
## TASI$Year: 2014
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -706     -24       9      -1      43     682 
## -------------------------------------------------------- 
## TASI$Year: 2015
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -550     -62       3      -6      52     518 
## -------------------------------------------------------- 
## TASI$Year: 2016
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -318     -41       3       0      52     195 
## -------------------------------------------------------- 
## TASI$Year: 2017
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -113.0   -26.6     3.0    -1.5    27.4   114.0
```


from 2003 until 2005 TASI index was mostly in positive way :


![plot of chunk unnamed-chunk-22](figure/unnamed-chunk-22-1.png)


It is shown highly increased in most months in the period from 2003 to 2005. In next part we are going to investegate the larger increased which is in March 2005 and the larger decreased in October 2003.



```
## [1] "statistic"   "parameter"   "p.value"     "estimate"    "null.value" 
## [6] "alternative" "method"      "data.name"   "conf.int"
```

```
##   cor 
## 0.076
```

```
## [1] "statistic"   "parameter"   "p.value"     "estimate"    "null.value" 
## [6] "alternative" "method"      "data.name"   "conf.int"
```

```
##   cor 
## 0.027
```

```
## [1] "statistic"   "parameter"   "p.value"     "estimate"    "null.value" 
## [6] "alternative" "method"      "data.name"   "conf.int"
```

```
##  cor 
## 0.55
```

```
## [1] "statistic"   "parameter"   "p.value"     "estimate"    "null.value" 
## [6] "alternative" "method"      "data.name"   "conf.int"
```

```
##    cor 
## -0.014
```
Correlation between Turnover, Volume, pervious closed and change :
correlation between Turnover and Change = 0.076 -> good but too small
correlation between Volumn and Change = 0.027 -> good but too small
correlation between Volume and  Turnover = 0.55 -> very good correlation.
correlation between pervious closed and Change = 0.076 -> No correlation.


![plot of chunk unnamed-chunk-24](figure/unnamed-chunk-24-1.png)

Next plot is investegate the causes of the fast changes in TASI 2006. Regarding to the correlation between change and volume, I will check the Month aginest the Volume then volume aginest the change. 

![plot of chunk unnamed-chunk-25](figure/unnamed-chunk-25-1.png)

![plot of chunk unnamed-chunk-26](figure/unnamed-chunk-26-1.png)
# Final Plots and Summary:


From the pervious part, It is clear that, in 2006 highly decreases and increases ocuured which is very observed through the distribution amonge the 3 first quarters. 



```
##       Date                 Open            High            Low       
##  Min.   :2006-01-01   Min.   : 7666   Min.   : 7756   Min.   : 7499  
##  1st Qu.:2006-03-26   1st Qu.:10674   1st Qu.:10912   1st Qu.:10417  
##  Median :2006-06-18   Median :11639   Median :11762   Median :11471  
##  Mean   :2006-06-24   Mean   :13009   Mean   :13198   Mean   :12724  
##  3rd Qu.:2006-09-18   3rd Qu.:16382   3rd Qu.:16734   3rd Qu.:15800  
##  Max.   :2006-12-27   Max.   :20635   Max.   :20967   Max.   :20369  
##      Closed      Change_Percentage     Change      Previous_Closed
##  Min.   : 7666   Min.   :-9.60     Min.   :-1458   Min.   :    0  
##  1st Qu.:10635   1st Qu.:-1.60     1st Qu.: -176   1st Qu.:10674  
##  Median :11627   Median : 0.19     Median :   23   Median :11639  
##  Mean   :12976   Mean   :-0.23     Mean   :  -33   Mean   :12977  
##  3rd Qu.:16368   3rd Qu.: 1.29     3rd Qu.:  152   3rd Qu.:16382  
##  Max.   :20635   Max.   : 9.85     Max.   : 1025   Max.   :20635  
##      Volume            Turnover            Year          
##  Min.   :5.54e+04   Min.   :2.18e+06   Length:267        
##  1st Qu.:7.06e+07   1st Qu.:1.09e+10   Class :character  
##  Median :1.93e+08   Median :1.70e+10   Mode  :character  
##  Mean   :1.85e+08   Mean   :1.84e+10                     
##  3rd Qu.:2.66e+08   3rd Qu.:2.37e+10                     
##  Max.   :4.79e+08   Max.   :4.63e+10                     
##     Month               Day           
##  Length:267         Length:267        
##  Class :character   Class :character  
##  Mode  :character   Mode  :character  
##                                       
##                                       
## 
```


![plot of chunk unnamed-chunk-28](figure/unnamed-chunk-28-1.png)
Now, we get a clear idea about the fast changes in 2006 from the above plot. The volume increased very clearly in the second and third quarter of the year. It reached its peak in the middle of the year. Obviously, the first quarter of the year was weak in terms of volume and even changes in index.


![plot of chunk unnamed-chunk-29](figure/unnamed-chunk-29-1.png)


Now, we are pretty sure that, the changes will increase positively when volume getting high and vice versa. it is the main and important idea we have to keep in mind when trading.



```
## [1] "statistic"   "parameter"   "p.value"     "estimate"    "null.value" 
## [6] "alternative" "method"      "data.name"   "conf.int"
```

```
##   cor 
## 0.838
```

Correlation between Turnover and closed  :
correlation between Closed and  Turnover = 0.838  -> Strong correlation.


![plot of chunk unnamed-chunk-31](figure/unnamed-chunk-31-1.png)

From here we can see the distribution of turnover through out colors. So, We again see how the trading of 2006 reach the highest turnover ever among all representive years.

# Reflection:

During working with this I found myself getting a general idea about the main point we should considered during trading as Volume and turnover for example and the basic concept of trading, for example the main factors affecting trading indexes. I would be thankful if DirectFN Pro provides the number of stocks that positively increased and vice versa. Wherefore, I could have a complete overview of how each factor affects the number of increased or decreased stocks. 
For future work, I downloaded the dataset of all index sectors and for stocks as well. The idea is to create a pattern which perdictes the positive and negative stocks. 

------------------


#*References*:
1- R-bloggers. 2017. Plot Weekly or Monthly Totals in R | R-bloggers. [ONLINE] Available at: https://www.r-bloggers.com/plot-weekly-or-monthly-totals-in-r/. [Accessed 13 April 2017].

2- printing multiple plot in on plot http://stackoverflow.com/questions/14860078/plot-multiple-lines-data-series-each-with-unique-color-in-r

3- format ggplot and axis titles:  https://www.r-bloggers.com/how-to-format-your-chart-and-axis-titles-in-ggplot2/

4- Get maximum value with in each group of values. http://stackoverflow.com/questions/25314336/extract-the-maximum-value-within-each-group-in-a-dataframe

5- https://www.harding.edu/fmccown/r/

6- R  Markdown Quick Tour http://rmarkdown.rstudio.com/authoring_quick_tour.html

7- Common legend for combined ggplot http://stackoverflow.com/questions/13649473/add-a-common-legend-for-combined-ggplots
