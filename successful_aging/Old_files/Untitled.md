# Successuful Aging
Leonardo Martins  
09 de abril de 2016  

All files used here are availible in a public repository licensed under MIT Licences and accessible by the following url:

https://github.com/crepeia/saging


#Preparing new analysis

#Loading required packages


#Preparing all data

```r
#Setting Directory
setwd("~/successful_aging")

#Importing SPSS file .sav
base.dat <- read.spss("Base.sav", to.data.frame = T, use.missings = T)
```


#Selecting only working variables

```r
saging <- base.dat[ ,c(3,6:27)]


saging <- base.dat[ ,c(2,4,5,6,7,8,9,3,10:27)]

#As dataframe
saging<-as.data.frame(saging)

#As factor

saging[,c(1)]<-as.factor(saging[,c(1)])
saging[,c(2)]<-as.factor(saging[,c(2)])
saging[,c(3)]<-as.factor(saging[,c(3)])
saging[,c(4)]<-as.factor(saging[,c(4)])
saging[,c(5)]<-as.factor(saging[,c(5)])
saging[,c(6)]<-as.factor(saging[,c(6)])
saging[,c(7)]<-as.factor(saging[,c(7)])

saging<-as.data.frame(saging)

#As numeric
for (i in c(7:26)) {
saging[,c(i)]<-as.numeric(saging[,c(i)])
}

#Sabedoria
saging$sabed<- saging$X.3dwscogAFC + saging$X.3dwsrefAFC + saging$X.3dwsafeAFC
```

#Variables Summary - Descriptive Stats

```r
#Status Social Economic - Variables

##Descriptive 
describe(saging)
```

```
## saging 
## 
##  27  Variables      303  Observations
## ---------------------------------------------------------------------------
## sexo 
##       n missing  unique 
##     303       0       2 
## 
## 1 (73, 24%), 2 (230, 76%) 
## ---------------------------------------------------------------------------
## escol 
##       n missing  unique 
##     303       0       5 
## 
##            1   2  3  4  5
## Frequency 66 130 31 38 38
## %         22  43 10 13 13
## ---------------------------------------------------------------------------
## estcivil 
##       n missing  unique 
##     303       0       5 
## 
##             1  2  3   4 5
## Frequency 123 35 26 114 5
## %          41 12  9  38 2
## ---------------------------------------------------------------------------
## autosaude 
##       n missing  unique 
##     303       0       5 
## 
##            1   2   3 4 5
## Frequency 56 115 118 9 5
## %         18  38  39 3 2
## ---------------------------------------------------------------------------
## constab 
##       n missing  unique 
##     303       0       3 
## 
## 1 (23, 8%), 2 (75, 25%), 3 (205, 68%) 
## ---------------------------------------------------------------------------
## consalco 
##       n missing  unique 
##     303       0       3 
## 
## 1 (251, 83%), 2 (50, 17%), 3 (2, 1%) 
## ---------------------------------------------------------------------------
## consfrveg 
##       n missing  unique    Info    Mean 
##     303       0       4    0.67   1.389 
## 
## 1 (206, 68%), 2 (77, 25%), 3 (19, 6%), 4 (1, 0%) 
## ---------------------------------------------------------------------------
## idade 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0      32       1   70.79    61.0    62.0    65.0    70.0 
##     .75     .90     .95 
##    75.0    82.0    85.9 
## 
## lowest : 60 61 62 63 64, highest: 87 88 89 91 99 
## ---------------------------------------------------------------------------
## meemtotal 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0      16    0.99   25.93      20      22      24      27 
##     .75     .90     .95 
##      28      29      30 
## 
##           14 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30
## Frequency  2  1  2  1  5  6 13 15 14 24 34 26 44 55 40 21
## %          1  0  1  0  2  2  4  5  5  8 11  9 15 18 13  7
## ---------------------------------------------------------------------------
## voctotal 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0      47       1   22.51     8.1    11.0    15.0    22.0 
##     .75     .90     .95 
##    29.0    35.8    42.0 
## 
## lowest :  1  2  4  6  7, highest: 45 46 47 48 50 
## ---------------------------------------------------------------------------
## rmtotal 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0      25    0.99   7.079     1.0     2.2     4.0     6.0 
##     .75     .90     .95 
##     8.0    15.0    19.0 
## 
## lowest :  0  1  2  3  4, highest: 20 21 22 23 24 
## ---------------------------------------------------------------------------
## esvtotal 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0      24    0.98   29.91      20      23      27      31 
##     .75     .90     .95 
##      34      35      35 
## 
## lowest :  6 10 12 13 14, highest: 31 32 33 34 35 
## ---------------------------------------------------------------------------
## partidtotal 
##       n missing  unique    Info    Mean 
##     303       0       6     0.9   1.086 
## 
##             0   1  2  3 4 5
## Frequency 105 112 50 29 5 2
## %          35  37 17 10 2 1
## ---------------------------------------------------------------------------
## eaertotal 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0      19    0.99   32.24      26      27      29      32 
##     .75     .90     .95 
##      35      38      39 
## 
##           19 22 23 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40
## Frequency  1  1  2  7  7 17 15 27 40 20 27 17 32 24 15 18 15  5 13
## %          0  0  1  2  2  6  5  9 13  7  9  6 11  8  5  6  5  2  4
## ---------------------------------------------------------------------------
## qsvpresenca 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0      23    0.99   29.54      21      23      27      30 
##     .75     .90     .95 
##      34      35      35 
## 
## lowest : 10 13 14 16 17, highest: 31 32 33 34 35 
## ---------------------------------------------------------------------------
## qsvbusca 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0      31       1   22.18     5.0     8.2    14.5    24.0 
##     .75     .90     .95 
##    30.0    34.0    35.0 
## 
## lowest :  5  6  7  8  9, highest: 31 32 33 34 35 
## ---------------------------------------------------------------------------
## qsvtotal 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0      40       1   51.73    37.1    40.0    45.0    52.0 
##     .75     .90     .95 
##    59.0    64.0    67.0 
## 
## lowest : 24 30 31 34 35, highest: 66 67 68 69 70 
## ---------------------------------------------------------------------------
## qpdtotal 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0      11    0.97   3.568       1       1       2       3 
##     .75     .90     .95 
##       5       6       7 
## 
##           0  1  2  3  4  5  6  7 8 9 13
## Frequency 5 42 50 58 57 47 19 19 3 2  1
## %         2 14 17 19 19 16  6  6 1 1  0
## ---------------------------------------------------------------------------
## assptotal 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0      12    0.96   17.26      12      13      15      18 
##     .75     .90     .95 
##      20      20      20 
## 
##           8 10 11 12 13 14 15 16 17 18 19 20
## Frequency 1  4  8  7 12 16 30 32 20 54 23 96
## %         0  1  3  2  4  5 10 11  7 18  8 32
## ---------------------------------------------------------------------------
## aivdptotal 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0      13    0.58  0.8911     0.0     0.0     0.0     0.0 
##     .75     .90     .95 
##     0.5     2.8     5.0 
## 
##             0  1  2 3 4 5 6 7 8 9 11 17 18
## Frequency 227 25 20 6 6 5 3 3 1 3  1  1  2
## %          75  8  7 2 2 2 1 1 0 1  0  0  1
## ---------------------------------------------------------------------------
## gdstotal 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0      13    0.98    3.29       0       1       2       3 
##     .75     .90     .95 
##       4       6       7 
## 
##            0  1  2  3  4  5  6 7 8 9 11 13 14
## Frequency 23 40 62 56 47 34 20 8 3 5  2  2  1
## %          8 13 20 18 16 11  7 3 1 2  1  1  0
## ---------------------------------------------------------------------------
## qcspatotal 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0      14    0.98   5.624       2       3       4       5 
##     .75     .90     .95 
##       7       8       9 
## 
##           0 1  2  3  4  5  6  7  8  9 10 11 12 14
## Frequency 2 2 15 28 56 53 41 49 32 11  7  3  2  2
## %         1 1  5  9 18 17 14 16 11  4  2  1  1  1
## ---------------------------------------------------------------------------
## X.3dwscogAFC 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0      26       1   2.726   1.571   1.857   2.286   2.714 
##     .75     .90     .95 
##   3.286   3.829   4.000 
## 
## lowest : 1.000 1.143 1.286 1.571 1.714
## highest: 4.143 4.286 4.429 4.571 4.857 
## ---------------------------------------------------------------------------
## X.3dwsafeAFC 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0      15    0.98   4.045    2.50    3.00    3.50    4.25 
##     .75     .90     .95 
##    4.75    5.00    5.00 
## 
##           1 1.5 2 2.25 2.5 2.75  3 3.25 3.5 3.75  4 4.25 4.5 4.75  5
## Frequency 2   1 9    1   4    8 13   19  32   16 37   48  31   17 65
## %         1   0 3    0   1    3  4    6  11    5 12   16  10    6 21
## ---------------------------------------------------------------------------
## X.3dwsrefAFC 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0      24       1   3.162   1.667   2.000   2.500   3.167 
##     .75     .90     .95 
##   3.833   4.333   4.500 
## 
## lowest : 1.000 1.167 1.333 1.500 1.667
## highest: 4.167 4.333 4.500 4.667 5.000 
## ---------------------------------------------------------------------------
## X.3dwstotalAFC 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0     241       1   3.311   2.240   2.460   2.944   3.365 
##     .75     .90     .95 
##   3.734   4.065   4.238 
## 
## lowest : 1.159 1.222 1.333 1.540 1.817
## highest: 4.500 4.508 4.603 4.698 4.841 
## ---------------------------------------------------------------------------
## sabed 
##       n missing  unique    Info    Mean     .05     .10     .25     .50 
##     303       0     242       1   9.933   6.719   7.379   8.833  10.095 
##     .75     .90     .95 
##  11.202  12.195  12.713 
## 
## lowest :  3.476  3.667  4.000  4.619  5.452
## highest: 13.500 13.524 13.810 14.095 14.524 
## ---------------------------------------------------------------------------
```

```r
summary(saging)
```

```
##  sexo    escol   estcivil autosaude constab consalco   consfrveg    
##  1: 73   1: 66   1:123    1: 56     1: 23   1:251    Min.   :1.000  
##  2:230   2:130   2: 35    2:115     2: 75   2: 50    1st Qu.:1.000  
##          3: 31   3: 26    3:118     3:205   3:  2    Median :1.000  
##          4: 38   4:114    4:  9                      Mean   :1.389  
##          5: 38   5:  5    5:  5                      3rd Qu.:2.000  
##                                                      Max.   :4.000  
##      idade         meemtotal        voctotal        rmtotal      
##  Min.   :60.00   Min.   :14.00   Min.   : 1.00   Min.   : 0.000  
##  1st Qu.:65.00   1st Qu.:24.00   1st Qu.:15.00   1st Qu.: 4.000  
##  Median :70.00   Median :27.00   Median :22.00   Median : 6.000  
##  Mean   :70.79   Mean   :25.93   Mean   :22.51   Mean   : 7.079  
##  3rd Qu.:75.00   3rd Qu.:28.00   3rd Qu.:29.00   3rd Qu.: 8.000  
##  Max.   :99.00   Max.   :30.00   Max.   :50.00   Max.   :24.000  
##     esvtotal      partidtotal      eaertotal      qsvpresenca   
##  Min.   : 6.00   Min.   :0.000   Min.   :19.00   Min.   :10.00  
##  1st Qu.:27.00   1st Qu.:0.000   1st Qu.:29.00   1st Qu.:27.00  
##  Median :31.00   Median :1.000   Median :32.00   Median :30.00  
##  Mean   :29.91   Mean   :1.086   Mean   :32.24   Mean   :29.54  
##  3rd Qu.:34.00   3rd Qu.:2.000   3rd Qu.:35.00   3rd Qu.:34.00  
##  Max.   :35.00   Max.   :5.000   Max.   :40.00   Max.   :35.00  
##     qsvbusca        qsvtotal        qpdtotal        assptotal    
##  Min.   : 5.00   Min.   :24.00   Min.   : 0.000   Min.   : 8.00  
##  1st Qu.:14.50   1st Qu.:45.00   1st Qu.: 2.000   1st Qu.:15.00  
##  Median :24.00   Median :52.00   Median : 3.000   Median :18.00  
##  Mean   :22.18   Mean   :51.73   Mean   : 3.568   Mean   :17.26  
##  3rd Qu.:30.00   3rd Qu.:59.00   3rd Qu.: 5.000   3rd Qu.:20.00  
##  Max.   :35.00   Max.   :70.00   Max.   :13.000   Max.   :20.00  
##    aivdptotal         gdstotal       qcspatotal      X.3dwscogAFC  
##  Min.   : 0.0000   Min.   : 0.00   Min.   : 0.000   Min.   :1.000  
##  1st Qu.: 0.0000   1st Qu.: 2.00   1st Qu.: 4.000   1st Qu.:2.286  
##  Median : 0.0000   Median : 3.00   Median : 5.000   Median :2.714  
##  Mean   : 0.8911   Mean   : 3.29   Mean   : 5.624   Mean   :2.726  
##  3rd Qu.: 0.5000   3rd Qu.: 4.00   3rd Qu.: 7.000   3rd Qu.:3.286  
##  Max.   :18.0000   Max.   :14.00   Max.   :14.000   Max.   :4.857  
##   X.3dwsafeAFC    X.3dwsrefAFC   X.3dwstotalAFC      sabed       
##  Min.   :1.000   Min.   :1.000   Min.   :1.159   Min.   : 3.476  
##  1st Qu.:3.500   1st Qu.:2.500   1st Qu.:2.944   1st Qu.: 8.833  
##  Median :4.250   Median :3.167   Median :3.365   Median :10.095  
##  Mean   :4.045   Mean   :3.162   Mean   :3.311   Mean   : 9.933  
##  3rd Qu.:4.750   3rd Qu.:3.833   3rd Qu.:3.734   3rd Qu.:11.202  
##  Max.   :5.000   Max.   :5.000   Max.   :4.841   Max.   :14.524
```


```r
#Saging

#Saging - First Model

saging1 <- '

# measurement model
envels =~ gdstotal + esvtotal + autosaude


# regressions
envels ~ voctotal + rmtotal + qsvpresenca + qsvbusca + X.3dwstotalAFC + qcspatotal


#correlations and residuals 

gdstotal ~~ gdstotal 
esvtotal ~~ esvtotal
autosaude ~~ autosaude
envels ~~ envels




#Mod Index

'

fitsaging1 <- sem(saging1, estimator="WLSMVS", mimic = "Mplus", data = saging,
        ordered=c("autosaude"))
```

```
## Found more than one class "Model" in cache; using the first, from namespace 'MatrixModels'
```

```r
#Model Summary 
summary(fitsaging1, standardized=T, fit.measures=T, rsquare=T)
```

```
## lavaan (0.5-20) converged normally after  62 iterations
## 
##   Number of observations                           303
## 
##   Estimator                                       DWLS      Robust
##   Minimum Function Test Statistic               28.940      35.696
##   Degrees of freedom                                12          10
##   P-value (Chi-square)                           0.004       0.000
##   Scaling correction factor                                  0.811
##     for the mean and variance adjusted correction (WLSMV)
## 
## Model test baseline model:
## 
##   Minimum Function Test Statistic              230.281     165.031
##   Degrees of freedom                                21          15
##   P-value                                        0.000       0.000
## 
## User model versus baseline model:
## 
##   Comparative Fit Index (CFI)                    0.919       0.829
##   Tucker-Lewis Index (TLI)                       0.858       0.743
## 
## Root Mean Square Error of Approximation:
## 
##   RMSEA                                          0.068       0.092
##   90 Percent Confidence Interval          0.037  0.101       0.057  0.130
##   P-value RMSEA <= 0.05                          0.153       0.025
## 
## Weighted Root Mean Square Residual:
## 
##   WRMR                                           0.999       0.999
## 
## Parameter Estimates:
## 
##   Information                                 Expected
##   Standard Errors                           Robust.sem
## 
## Latent Variables:
##                    Estimate  Std.Err  Z-value  P(>|z|)   Std.lv  Std.all
##   envels =~                                                             
##     gdstotal          1.000                               1.560    0.704
##     esvtotal         -2.086    0.313   -6.672    0.000   -3.255   -0.628
##     autosaude         0.412    0.058    7.086    0.000    0.644    0.610
## 
## Regressions:
##                    Estimate  Std.Err  Z-value  P(>|z|)   Std.lv  Std.all
##   envels ~                                                              
##     voctotal          0.015    0.013    1.098    0.272    0.009    0.092
##     rmtotal          -0.031    0.028   -1.097    0.272   -0.020   -0.099
##     qsvpresenca      -0.104    0.022   -4.729    0.000   -0.067   -0.322
##     qsvbusca          0.016    0.013    1.288    0.198    0.010    0.095
##     X.3dwstotalAFC   -0.548    0.199   -2.759    0.006   -0.351   -0.218
##     qcspatotal       -0.128    0.048   -2.643    0.008   -0.082   -0.184
## 
## Intercepts:
##                    Estimate  Std.Err  Z-value  P(>|z|)   Std.lv  Std.all
##     gdstotal          9.278    1.073    8.649    0.000    9.278    4.188
##     esvtotal         18.960    2.239    8.470    0.000   18.960    3.656
##     autosaude         0.000                               0.000    0.000
##     envels            0.000                               0.000    0.000
## 
## Thresholds:
##                    Estimate  Std.Err  Z-value  P(>|z|)   Std.lv  Std.all
##     autosaude|t1     -2.315    0.570   -4.062    0.000   -2.315   -2.192
##     autosaude|t2     -1.176    0.563   -2.088    0.037   -1.176   -1.114
##     autosaude|t3      0.454    0.541    0.839    0.401    0.454    0.430
##     autosaude|t4      0.909    0.572    1.588    0.112    0.909    0.861
## 
## Variances:
##                    Estimate  Std.Err  Z-value  P(>|z|)   Std.lv  Std.all
##     gdstotal          2.473    0.314    7.888    0.000    2.473    0.504
##     esvtotal         16.306    1.541   10.584    0.000   16.306    0.606
##     autosaude         0.700                               0.700    0.628
##     envels            1.760    0.324    5.436    0.000    0.723    0.723
## 
## Scales y*:
##                    Estimate  Std.Err  Z-value  P(>|z|)   Std.lv  Std.all
##     autosaude         1.000                               1.000    1.000
## 
## R-Square:
##                    Estimate
##     gdstotal          0.496
##     esvtotal          0.394
##     autosaude         0.372
##     envels            0.277
```

```r
#Model Fit Measures
fitMeasures(fitsaging1, c("chisq","df","rmsea","rmsea.ci.lower", "rmsea.ci.upper", "srmr", "cfi", "tli", "nfi", "ecvi"))
```

```
##          chisq             df          rmsea rmsea.ci.lower rmsea.ci.upper 
##         28.940         12.000          0.068          0.037          0.101 
##           srmr            cfi            tli            nfi           ecvi 
##          1.224          0.919          0.858          0.874             NA
```

```r
#Parameters Estimates
EstPCA2rf <- parameterEstimates(fitsaging1, standardized=T, ci=F)
subset(EstPCA2rf, op == "=~")
```

```
##      lhs op       rhs    est    se      z pvalue std.lv std.all std.nox
## 1 envels =~  gdstotal  1.000 0.000     NA     NA  1.560   0.704   0.704
## 2 envels =~  esvtotal -2.086 0.313 -6.672      0 -3.255  -0.628  -0.628
## 3 envels =~ autosaude  0.412 0.058  7.086      0  0.644   0.610   0.610
```

```r
#Modification Index
MIPCA2rf<-modindices(fitsaging1)
MIIPCA2rf<- MIPCA2rf[which(MIPCA2rf$mi>10),]
print(MIIPCA2rf)
```

```
## [1] lhs       op        rhs       mi        mi.scaled epc       sepc.lv  
## [8] sepc.all  sepc.nox 
## <0 rows> (or 0-length row.names)
```

```r
#Model Plot
semPaths(fitsaging1, what="path", whatLabels ="std", edge.label.cex = 0.7, exoVar = F, exoCov = T, layout = "tree2", optimizeLatRes=T, style = "lisrel", curve= 0.9, sizeLat = 5, sizeLat2 = 5, sizeMan = 3, sizeMan2 = 3, title = T, thresholds = F, curvePivot=T, intercepts = F, residuals = F)

#Define Title
title(main = "Figure 1. Structural Equation Model For Successful Aging", line = 1)

#Define Subtitle
title(sub = expression("Fit measures:" ~ chi^2~(31)==272,039 ~", p<0.001, n=303; CFI=0.360; TLI=0.401; NFI=0.986; RMSEA=0.160; 90%CI(0.146-0.175); SRMR=0.045"), line = 3, font.sub = 1, cex.sub = 0.5)
```

![](Untitled_files/figure-html/unnamed-chunk-3-1.png)<!-- -->

```r
moreFitIndices(fitsaging1, fit.measures = "all", nPrior = 303)
```

```
##       gammaHat    adjGammaHat baseline.rmsea 
##      0.9639532      0.9819766      0.1813568
```




```r
#Saging

#Saging - First Model

saging1 <- '

# measurement model
envels =~ esvtotal + autosaude + gdstotal


# regressions
envels ~ voctotal + rmtotal + qsvbusca + qsvpresenca + X.3dwstotalAFC + qcspatotal


#correlations and residuals 

gdstotal ~~ gdstotal 
esvtotal ~~ esvtotal
autosaude ~~ autosaude
envels ~~ envels




#Mod Index

'

fitsaging1 <- sem(saging1, estimator="WLSMVS", mimic = "Mplus", data = saging,
        ordered=c("autosaude"))

#Model Summary 
summary(fitsaging1, standardized=T, fit.measures=T, rsquare=T)
```

```
## lavaan (0.5-20) converged normally after  79 iterations
## 
##   Number of observations                           303
## 
##   Estimator                                       DWLS      Robust
##   Minimum Function Test Statistic               28.940      35.696
##   Degrees of freedom                                12          10
##   P-value (Chi-square)                           0.004       0.000
##   Scaling correction factor                                  0.811
##     for the mean and variance adjusted correction (WLSMV)
## 
## Model test baseline model:
## 
##   Minimum Function Test Statistic              230.281     165.031
##   Degrees of freedom                                21          15
##   P-value                                        0.000       0.000
## 
## User model versus baseline model:
## 
##   Comparative Fit Index (CFI)                    0.919       0.829
##   Tucker-Lewis Index (TLI)                       0.858       0.743
## 
## Root Mean Square Error of Approximation:
## 
##   RMSEA                                          0.068       0.092
##   90 Percent Confidence Interval          0.037  0.101       0.057  0.130
##   P-value RMSEA <= 0.05                          0.153       0.025
## 
## Weighted Root Mean Square Residual:
## 
##   WRMR                                           0.999       0.999
## 
## Parameter Estimates:
## 
##   Information                                 Expected
##   Standard Errors                           Robust.sem
## 
## Latent Variables:
##                    Estimate  Std.Err  Z-value  P(>|z|)   Std.lv  Std.all
##   envels =~                                                             
##     esvtotal          1.000                               3.255    0.628
##     autosaude        -0.198    0.029   -6.859    0.000   -0.644   -0.610
##     gdstotal         -0.479    0.072   -6.672    0.000   -1.560   -0.704
## 
## Regressions:
##                    Estimate  Std.Err  Z-value  P(>|z|)   Std.lv  Std.all
##   envels ~                                                              
##     voctotal         -0.030    0.028   -1.090    0.276   -0.009   -0.092
##     rmtotal           0.065    0.059    1.096    0.273    0.020    0.099
##     qsvbusca         -0.034    0.027   -1.277    0.201   -0.010   -0.095
##     qsvpresenca       0.217    0.048    4.489    0.000    0.067    0.322
##     X.3dwstotalAFC    1.143    0.421    2.717    0.007    0.351    0.218
##     qcspatotal        0.267    0.100    2.662    0.008    0.082    0.184
## 
## Intercepts:
##                    Estimate  Std.Err  Z-value  P(>|z|)   Std.lv  Std.all
##     esvtotal         18.960    2.239    8.470    0.000   18.960    3.656
##     autosaude         0.000                               0.000    0.000
##     gdstotal          9.278    1.073    8.649    0.000    9.278    4.188
##     envels            0.000                               0.000    0.000
## 
## Thresholds:
##                    Estimate  Std.Err  Z-value  P(>|z|)   Std.lv  Std.all
##     autosaude|t1     -2.315    0.570   -4.062    0.000   -2.315   -2.192
##     autosaude|t2     -1.176    0.563   -2.088    0.037   -1.176   -1.114
##     autosaude|t3      0.454    0.541    0.839    0.401    0.454    0.430
##     autosaude|t4      0.909    0.572    1.588    0.112    0.909    0.861
## 
## Variances:
##                    Estimate  Std.Err  Z-value  P(>|z|)   Std.lv  Std.all
##     gdstotal          2.473    0.314    7.888    0.000    2.473    0.504
##     esvtotal         16.306    1.541   10.585    0.000   16.306    0.606
##     autosaude         0.700                               0.700    0.628
##     envels            7.657    1.637    4.679    0.000    0.723    0.723
## 
## Scales y*:
##                    Estimate  Std.Err  Z-value  P(>|z|)   Std.lv  Std.all
##     autosaude         1.000                               1.000    1.000
## 
## R-Square:
##                    Estimate
##     gdstotal          0.496
##     esvtotal          0.394
##     autosaude         0.372
##     envels            0.277
```

```r
#Model Fit Measures
fitMeasures(fitsaging1, c("chisq","df","rmsea","rmsea.ci.lower", "rmsea.ci.upper", "srmr", "cfi", "tli", "nfi", "ecvi"))
```

```
##          chisq             df          rmsea rmsea.ci.lower rmsea.ci.upper 
##         28.940         12.000          0.068          0.037          0.101 
##           srmr            cfi            tli            nfi           ecvi 
##          1.224          0.919          0.858          0.874             NA
```

```r
moreFitIndices(fitsaging1, fit.measures = "all", nPrior = 303)
```

```
##       gammaHat    adjGammaHat baseline.rmsea 
##      0.9639532      0.9819766      0.1813568
```

```r
#Parameters Estimates
EstPCA2rf <- parameterEstimates(fitsaging1, standardized=T, ci=F)
subset(EstPCA2rf, op == "=~")
```

```
##      lhs op       rhs    est    se      z pvalue std.lv std.all std.nox
## 1 envels =~  esvtotal  1.000 0.000     NA     NA  3.255   0.628   0.628
## 2 envels =~ autosaude -0.198 0.029 -6.859      0 -0.644  -0.610  -0.610
## 3 envels =~  gdstotal -0.479 0.072 -6.672      0 -1.560  -0.704  -0.704
```

```r
#Modification Index
MIPCA2rf<-modindices(fitsaging1)
MIIPCA2rf<- MIPCA2rf[which(MIPCA2rf$mi>10),]
print(MIIPCA2rf)
```

```
## [1] lhs       op        rhs       mi        mi.scaled epc       sepc.lv  
## [8] sepc.all  sepc.nox 
## <0 rows> (or 0-length row.names)
```

```r
#Model Plot
semPaths(fitsaging1, what="path", whatLabels ="std", edge.label.cex = 0.7, exoVar = F, exoCov = T, layout = "tree2", optimizeLatRes=T, style = "lisrel", curve= 0.9, sizeLat = 5, sizeLat2 = 5, sizeMan = 3, sizeMan2 = 3, title = T, thresholds = F, curvePivot=T, intercepts = F, residuals = F)

#Define Title
title(main = "Figure 1. Structural Equation Model For Successful Aging", line = 1)

#Define Subtitle
title(sub = expression("Fit measures: n=303; CFI=0.919; TLI=0.858; NFI=0.874; RMSEA=0.068; 90%CI(0.037-0.057)" ~ chi^2~(31)==272.039), line = 3, font.sub = 1, cex.sub = 0.5)
```

![](Untitled_files/figure-html/unnamed-chunk-4-1.png)<!-- -->

