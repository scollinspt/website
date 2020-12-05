---
title: SBP Analysis Trial
author: Collins
date: '2020-12-05'
slug: trial
categories: [analysis]
tags: []
subtitle: ''
summary: ''
authors: []
lastmod: '2020-12-05T05:46:00-05:30'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

SBP
===

Primary Independent Variables
-----------------------------

-   TargetHR is a factor variable that is the stage of exercise
-   HR (calculated from RPP and SBP) is a continuous variable that is
    the subjects actual mean HR during a particular stage of exercise
-   Mode is a factor variable and either AE (arm ergometry) or LE (leg
    ergometry)

Secondary Independent Variables
-------------------------------

-   Sex (male or female)
-   Age (rather narrow range so not included as a co-variate)

Primary Dependent Variables
---------------------------

-   Systolic Blood Pressure (SBP) (mm Hg)

Systolic Blood Pressure
=======================

SBP Scatterplot
---------------

![SBP Scatterplot](sbp.png)

LME - Systolic Blood Pressure
-----------------------------

### LME SBP Model Statistics

    ##                     Model df      AIC      BIC    logLik   Test   L.Ratio
    ## sbpBaseline             1  4 3145.153 3160.585 -1568.577                 
    ## sbpHrModel              2  5 2979.862 2999.152 -1484.931 1 vs 2 167.29088
    ## sbpFullModel            3  6 2899.745 2922.892 -1443.872 2 vs 3  82.11754
    ## sbpInteractionModel     4  7 2864.929 2891.934 -1425.465 3 vs 4  36.81586
    ##                     p-value
    ## sbpBaseline                
    ## sbpHrModel           <.0001
    ## sbpFullModel         <.0001
    ## sbpInteractionModel  <.0001

    summary(sbpInteractionModel)

    ## Linear mixed-effects model fit by maximum likelihood
    ##  Data: data 
    ##        AIC      BIC    logLik
    ##   2864.929 2891.934 -1425.464
    ## 
    ## Random effects:
    ##  Formula: ~1 | ParticNum
    ##         (Intercept)
    ## StdDev:    13.43265
    ## 
    ##  Formula: ~1 | HR %in% ParticNum
    ##         (Intercept) Residual
    ## StdDev:    11.46336 5.039526
    ## 
    ## Fixed effects: SBP ~ HR + Mode + HR:Mode 
    ##                 Value Std.Error  DF   t-value p-value
    ## (Intercept)  85.20690  8.356191 312 10.196859       0
    ## HR            0.38327  0.063177 312  6.066725       0
    ## ModeLE      -58.50953 11.793069 312 -4.961349       0
    ## HR:ModeLE     0.55770  0.089785 312  6.211484       0
    ##  Correlation: 
    ##           (Intr) HR     ModeLE
    ## HR        -0.955              
    ## ModeLE    -0.652  0.673       
    ## HR:ModeLE  0.668 -0.700 -0.993
    ## 
    ## Standardized Within-Group Residuals:
    ##          Min           Q1          Med           Q3          Max 
    ## -1.311358641 -0.267614471 -0.009098334  0.244087649  1.524017297 
    ## 
    ## Number of Observations: 350
    ## Number of Groups: 
    ##         ParticNum HR %in% ParticNum 
    ##                35               350

    intervals(sbpInteractionModel, which="fixed")

    ## Approximate 95% confidence intervals
    ## 
    ##  Fixed effects:
    ##                   lower        est.       upper
    ## (Intercept)  68.8595087  85.2068986 101.5542885
    ## HR            0.2596813   0.3832750   0.5068686
    ## ModeLE      -81.5805567 -58.5095307 -35.4385047
    ## HR:ModeLE     0.3820515   0.5577005   0.7333495
    ## attr(,"label")
    ## [1] "Fixed effects:"



