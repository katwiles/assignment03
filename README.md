# Assignment 3
Kat Wiles  
September 26, 2014  

Complete the exercises listed below and submit as a pull request to the [Assignment 3 repository](http://www.github.com/microbialinformatics/assignment03).  Format this document approapriately using R markdown and knitr. For those cases where there are multiple outputs, make it clear in how you format the text and interweave the solution, what the solution is.

Your pull request should only include your *.Rmd and *.md files. You may work with a partner, but you must submit your own assignment and give credit to anyone that worked with you on the assignment and to any websites that you used along your way. You should not use any packages beyond the base R system and knitr.

This assignment is due on October 10th.

------

####1.  
**Generate a plot that contains the different pch symbols. Investigate the knitr code chunk options to see whether you can have a pdf version of the image produced so you can print it off for yoru reference. It should look like this:**
 <img src="pch.png", style="margin:0px auto;display:block" width="500">


```r
plot(x=1:25,y=rep(1,25), pch = 1:25, cex=1.5, yaxt='n', ann=FALSE, bty='n', xaxt='n', panel.first=c(abline(v=1:25, col="light gray",lty=1)))
axis(1,at=c(1,3,5,7,9,11,13,15,17,19,21,23,25), lty=1)
title(main="PCH Symbol",xlab="PCH Value")
```

![plot of chunk unnamed-chunk-1](./README_files/figure-html/unnamed-chunk-1.png) 

   
    


####2.  
**Using the `germfree.nmds.axes` data file available in this respositry, generate a plot that looks like this. The points are connected in the order they were sampled with the circle representing the beginning ad the square the end of the time course:**

    <img src="beta.png", style="margin:0px auto;display:block" width="700">
    
    

```r
germfree<-read.table(file="germfree.nmds.axes", header=T)
plot(germfree$axis2~germfree$axis1, xlab="NMDS Axis 1", ylab="NMDS Axis 2", lty=2, type='n')

points((germfree[germfree$mouse==337 & germfree$day==1,][3]), (germfree[germfree$mouse==337 & germfree$day==1,][4]), pch=16, col="black", cex=1.5)
points((germfree[germfree$mouse==337 & germfree$day==20,][3]), (germfree[germfree$mouse==337 & germfree$day==20,][4]), pch=15, col="black", cex=1.5)
m337 <- as.matrix(germfree[germfree$mouse==337,])
lines((m337[,3]), (m337[,4]), col="black", lwd=2)

points((germfree[germfree$mouse==343 & germfree$day==1,][3]), (germfree[germfree$mouse==343 & germfree$day==1,][4]), pch=16, col="blue", cex=1.5)
points((germfree[germfree$mouse==343 & germfree$day==21,][3]), (germfree[germfree$mouse==343 & germfree$day==21,][4]), pch=15, col="blue", cex=1.5)
m343 <- as.matrix(germfree[germfree$mouse==343,])
lines((m343[,3]), (m343[,4]), col="blue", lwd=2)

points((germfree[germfree$mouse==361 & germfree$day==1,][3]), (germfree[germfree$mouse==361 & germfree$day==1,][4]), pch=16, col="red", cex=1.5)
points((germfree[germfree$mouse==361 & germfree$day==21,][3]), (germfree[germfree$mouse==361 & germfree$day==21,][4]), pch=15, col="red", cex=1.5)
m361 <- as.matrix(germfree[germfree$mouse==361,])
lines((m361[,3]), (m361[,4]), col="red", lwd=2)


points((germfree[germfree$mouse==387 & germfree$day==1,][3]), (germfree[germfree$mouse==387 & germfree$day==1,][4]), pch=16, col="green", cex=1.5)
points((germfree[germfree$mouse==387 & germfree$day==21,][3]), (germfree[germfree$mouse==387 & germfree$day==21,][4]), pch=15, col="green", cex=1.5)
m387 <- as.matrix(germfree[germfree$mouse==387,])
lines((m387[,3]), (m387[,4]), col="green", lwd=2)

points((germfree[germfree$mouse==389 & germfree$day==1,][3]), (germfree[germfree$mouse==389 & germfree$day==1,][4]), pch=16, col="brown", cex=1.5)
points((germfree[germfree$mouse==389 & germfree$day==21,][3]), (germfree[germfree$mouse==389 & germfree$day==21,][4]), pch=15, col="brown", cex=1.5)
m389 <- as.matrix(germfree[germfree$mouse==389,])
lines((m389[,3]), (m389[,4]), col="brown", lwd=2)
```

![plot of chunk unnamed-chunk-2](./README_files/figure-html/unnamed-chunk-2.png) 



####3.  
**On pg. 57 there is a formula for the probability of making x observations after n trials when there is a probability p of the observation.  For this exercise, assume x=2, n=10, and p=0.5.  Using R, calculate the probability of x using this formula and the appropriate built in function. Compare it to the results we obtained in class when discussing the sex ratios of mice.**


####4.  
**On pg. 59 there is a formula for the probability of observing a value, x, when there is a mean, mu, and standard deviation, sigma.  For this exercise, assume x=10.3, mu=5, and sigma=3.  Using R, calculate the probability of x using this formula and the appropriate built in function**


####5.  
**One of my previous students, Joe Zackular, obtained stool samples from 89 people that underwent colonoscopies.  30 of these individuals had no signs of disease, 30 had non-cancerous ademonas, and 29 had cancer.  It was previously suggested that the bacterium *Fusobacterium nucleatum* was associated with cancer.  In these three pools of subjects, Joe determined that 4, 1, and 14 individuals harbored *F. nucleatum*, respectively. Create a matrix table to represent the number of individuals with and without _F. nucleatum_ as a function of disease state.**  



```
##                           N with Disease State     N with F. nucleatum
## No Disease Present                          30                       4
## Non-Cancerous Ademonas                      30                       1
## cancer                                      29                      14
```



**Then do the following:**
**Run the three tests of proportions you learned about in class using built in R  functions to the 2x2 study design where normals and adenomas are pooled and compared to carcinomas.**
    


```
##        Disease State F. nucleatum
## Normal            60            5
## Cancer            29           14
```

```
## 
## 	2-sample test for equality of proportions with continuity
## 	correction
## 
## data:  mat2
## X-squared = 9.389, df = 1, p-value = 0.002183
## alternative hypothesis: two.sided
## 95 percent confidence interval:
##  0.07502 0.42229
## sample estimates:
## prop 1 prop 2 
## 0.9231 0.6744
```
    
    
**Without using the built in chi-squared test function, replicate the 2x2 study design in the last problem for the Chi-Squared Test...**
    
    
**Calculate the expected count matrix and calculate the Chi-Squared test statistics. Figure out how to get your test statistic to match Rs default statistic.**
      
      
**Generate a Chi-Squared distributions with approporiate degrees of freedom by the method that was discussed in class (hint: you may consider using the `replicate` command)**
      
      
**Compare your Chi-Squared distributions to what you might get from the appropriate built in R functions**
      
      
**Based on your distribution calculate p-values**
      
      
**How does your p-value compare to what you saw using the built in functions? Explain your observations.**



####6.
**Get a bag of Skittles or M&Ms.  Are the candies evenly distributed amongst the different colors?  Justify your conclusion.**

