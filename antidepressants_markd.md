Antidepressants and suicidal behaviour?
================
Jakob A. Kaminski
4 7 2019

Intro
-----

Hengartner et al. performed a re-analysis of the FDA database and evaluated newer-generation antidepressants and suicide risk in Randomized Controlled Trials. We critically review the literature and reanalyze the re-analysis.

This is the data. Of note, there is considerable variance between the studies.

    ## # A tibble: 14 x 5
    ##    study              ADsuicides ADparticipants PLCsuicides PLCparticipants
    ##    <chr>                   <dbl>          <dbl>       <dbl>           <dbl>
    ##  1 Sertraline (1991)           2           2053           0             786
    ##  2 Paroxetine (1992)           5           2963           2             554
    ##  3 Venlafaxine (1993)          3           2181           1             451
    ##  4 Nefazodone (1994)           9           3496           0             875
    ##  5 Mirtazapine (1996)          8           2425           0             494
    ##  6 Venlafaxine ER (1…          1            705           0             285
    ##  7 Citalopram (1998)           8           4168           1             691
    ##  8 Escitalopram (200…          0            715           0             592
    ##  9 Duloxetine (2002)           0           2314           0             723
    ## 10 Desvenlafaxine (2…          1           2667           0             803
    ## 11 Trazodone ER (201…          0            202           0             204
    ## 12 Vilazodone (2011)           0           2177           0             997
    ## 13 Levomilnacipran (…          0           2655           0            1004
    ## 14 Vortioxetine (201…          0           3060           0            1621

The analysis is run on the sum of the above mentioned data:

<table>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
Placebo
</th>
<th style="text-align:right;">
Antidepressant
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
no suicide
</td>
<td style="text-align:right;">
10076
</td>
<td style="text-align:right;">
31744
</td>
</tr>
<tr>
<td style="text-align:left;">
suicide
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:right;">
37
</td>
</tr>
</tbody>
</table>
Reproducing Hengartner et al. results

    ## $tab
    ##            Placebo           p0 Antidepressant          p1 oddsratio
    ## no suicide   10076 0.9996031746          31744 0.998835782   1.00000
    ## suicide          4 0.0003968254             37 0.001164218   2.83487
    ##               lower    upper    p.value
    ## no suicide       NA       NA         NA
    ## suicide    1.133143 9.671619 0.02354558
    ## 
    ## $measure
    ## [1] "midp"
    ## 
    ## $conf.level
    ## [1] 0.95
    ## 
    ## $pvalue
    ## [1] "midp.exact"
    ## 
    ## $x
    ##            Placebo Antidepressant
    ## no suicide   10076          31744
    ## suicide          4             37
    ## 
    ## $data
    ##            Placebo Antidepressant Total
    ## no suicide   10076          31744 41820
    ## suicide          4             37    41
    ## Total        10080          31781 41861
    ## 
    ## $p.exposed
    ##                 Placebo Antidepressant        Total
    ## no suicide 0.9996031746    0.998835782 0.9990205681
    ## suicide    0.0003968254    0.001164218 0.0009794319
    ## Total      1.0000000000    1.000000000 1.0000000000
    ## 
    ## $p.outcome
    ##               Placebo Antidepressant Total
    ## no suicide 0.24093735      0.7590626     1
    ## suicide    0.09756098      0.9024390     1
    ## Total      0.24079692      0.7592031     1
    ## 
    ## $p.value
    ##             NA
    ## two-sided    midp.exact fisher.exact chi.square
    ##   no suicide         NA           NA         NA
    ##   suicide    0.02354558   0.02855102 0.04960071
    ## 
    ## $correction
    ## [1] TRUE

First one has to visualize the data.

Mosaic plot
-----------

![](antidepressants_markd_files/figure-markdown_github/mosaic-1.png)

Then we reanalyzed the data using meta analytical approach taking the variance between studies into account peto method <http://www.metafor-project.org/doku.php/analyses:yusuf1985>

suicide
=======

![](antidepressants_markd_files/figure-markdown_github/forest-1.png)

suicide attempts
================

![](antidepressants_markd_files/figure-markdown_github/forest_attempt_plot-1.png)![](antidepressants_markd_files/figure-markdown_github/forest_attempt_plot-2.png)

suicide
=======

Mantel-Haenszel (MH) Methode. Reccomended for rare events, and anequal group sizes: Ref: <https://ebmh.bmj.com/content/21/2/72>

![](antidepressants_markd_files/figure-markdown_github/metafor_suicide-1.png)

    ## 
    ## Fixed-Effects Model (k = 14)
    ## 
    ## Test for Heterogeneity: 
    ## Q(df = 2) = 4.1258, p-val = 0.1271
    ## 
    ## Model Results (log scale):
    ## 
    ## estimate      se    zval    pval    ci.lb   ci.ub 
    ##   0.6828  0.5211  1.3103  0.1901  -0.3386  1.7042 
    ## 
    ## Model Results (OR scale):
    ## 
    ## estimate   ci.lb   ci.ub 
    ##   1.9794  0.7128  5.4968 
    ## 
    ## Cochran-Mantel-Haenszel Test:    CMH = 1.8312, df = 1, p-val = 0.1760
    ## Tarone's Test for Heterogeneity: X^2 = 7.5084, df = 7, p-val = 0.3779

suicide attempts
================

![](antidepressants_markd_files/figure-markdown_github/metafor_suicideattempts-1.png)

    ## 
    ## Fixed-Effects Model (k = 12)
    ## 
    ## Test for Heterogeneity: 
    ## Q(df = 11) = 6.3883, p-val = 0.8462
    ## 
    ## Model Results (log scale):
    ## 
    ## estimate      se    zval    pval   ci.lb   ci.ub 
    ##   0.4901  0.2038  2.4053  0.0162  0.0907  0.8895 
    ## 
    ## Model Results (OR scale):
    ## 
    ## estimate   ci.lb   ci.ub 
    ##   1.6325  1.0950  2.4340 
    ## 
    ## Cochran-Mantel-Haenszel Test:    CMH =  5.9428, df = 1,  p-val = 0.0148
    ## Tarone's Test for Heterogeneity: X^2 = 10.4092, df = 11, p-val = 0.4940

![](antidepressants_markd_files/figure-markdown_github/metafor_suicideattempts-2.png)
