---
title: "Chapter 4: Chi-Squared Test of Homogeniety"
subtitle: "These Proportions Will Not Stand, Man"
author: "Andy Kampfschulte"
output: 
  tint::tintHtml:
    keep_md: true
css: Style_Numbus.css
link-citations: yes

---




# Background

<p><span class="marginnote shownote"><!--
<div class="figure">-->
<img src="C4_Notes_files/figure-html/unnamed-chunk-1-1.gif" alt="....Bivariate Data?"  />
<!--
<p class="caption marginnote">-->....Bivariate Data?<!--</p>-->
<!--</div>--></span></p>

In chapters 2 & 3, we dealt with univariate data. That is,  we analyzed statistics and descriptions from one variable only (ie the proportion of people with a given trait, the average measurement of something, and so on). These univariate tests and summaries are very useful in their own right, but they ave limited applications in the real world -- people generally want to the understand the *cause-and-effect* relationship between a plurality of variables. For example, knowing the proportion of students that got an A in a certain class is helpful, but understanding how that proportion is related to another variable, like the proportion of seniors in that class, can tell us much more and help us better understand the world around us. So, rather than looking at seperate variables in isolation, in chapter 4 we will be looking at bivariate data. In other words, we will be looking at how one variable does (or doesn't) change in the presence of another variable.

In Chapter 4, we will be introduced to the Chi-Squared Test of Independence (or Chi-Squared Test of Homogeniety of Proportions if you're not into the whole brevity thing). This test allows us to see whether the level of one variable has an impact or association with the level of another variable. 

---

# Independence and the Two-Way Table

<p><span class="marginnote shownote"><!--
<div class="figure">-->
<img src="C4_Notes_files/figure-html/unnamed-chunk-2-1.png" alt=" "  />
<!--
<p class="caption marginnote">--> <!--</p>-->
<!--</div>--></span></p>


In Chapter 4, our tool of choice is the two-way table. Most of you should have seen these at some point prior to this class. A two-way table is simply a frequency table from chapter 2 in which we've added another frequency table on top. This allows us to see frequency changes across two variables (a two-dimensional change). You may heard these referred to as cross-tabulations or pivot tables as well. They're all the same thing. 

<table class='gmisc_table' style='border-collapse: collapse; margin-top: 1em; margin-bottom: 1em;' >
<thead>
<tr><th style='border-bottom: 1px solid grey; font-weight: 900; border-top: 2px solid grey; text-align: center;'></th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;A&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;B&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;C&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;#Total&nbsp;</th>
</tr>
</thead>
<tbody> 
<tr><td colspan='5' style='font-weight: 900;'>&nbsp;sex&nbsp;</td></tr>
<tr>
<td style='text-align: left;'>&nbsp;&nbsp;&nbsp;Female&nbsp;</td>
<td style='text-align: right;'>15</td>
<td style='text-align: right;'>8</td>
<td style='text-align: right;'>6</td>
<td style='text-align: right;'>29</td>
</tr>
<tr>
<td style='text-align: left;'>&nbsp;&nbsp;&nbsp;Male&nbsp;</td>
<td style='text-align: right;'>12</td>
<td style='text-align: right;'>9</td>
<td style='text-align: right;'>5</td>
<td style='text-align: right;'>26</td>
</tr>
<tr>
<td style='border-bottom: 2px solid grey; text-align: left;'>&nbsp;&nbsp;&nbsp;#Total&nbsp;</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>27</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>17</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>11</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>55</td>
</tr>
</tbody>
</table>


Two-way tables are constructed by cross-referencing frequencies of a row variable with the frequencies of a column variable. The row variable will always be the **explanatory variable** while the column variable will henceforth be known as the **response variable**. If you recall from chapter one, the explanatory variable is the variable we use to *explain* any changes in the response variable. In the case of a two-way table, we are seeing the row variable is changing the frequencies of the response variable. **We are seeing if the conditional probability for the response variable changes at different levels of the explanatory variable** .

To put it simply, we are going to compare the proportions for each level of the explanatory variable at each level of the resonse variable and see if they are equal. If the proportions are equal, then we can say that the two variables have no relationship with another (they are indepependent). However, if the proportions end up being wildly different across levels of the explanatory, then we can quantify that difference and determine how *strongly* they are related, and determine if the relationship is string enough that it cannot be explained away by mere chance. 

>**Independence:** The explanatory variable has no effect on the response variable

Let's look at an example where independence makes complete sense. Here we have a two way table taken from several STA 215 classes. As the explanatory variable, we have the STA 215 student's gender. The response variable is the final grade of the STA 215 student. **SO**, what this table is exploring is the relationship a student's gender may have on their final STA 215 grade. Well, obviously we would hope there is no difference in academic performance between males and females, so we would anticipate that the two variables (gender and STA 215 grade) are independent and there is no association. As we can see here, the counts line up pretty well - a similiar number of males and females got an A, a similiar number got a B, and so on. Therefore, if the counts are pretty similiar, the probabilities should be similiar as well. 

<table class='gmisc_table' style='border-collapse: collapse; margin-top: 1em; margin-bottom: 1em;' >
<thead>
<tr><th style='border-bottom: 1px solid grey; font-weight: 900; border-top: 2px solid grey; text-align: center;'></th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;A&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;B&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;C&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;#Total&nbsp;</th>
</tr>
</thead>
<tbody> 
<tr><td colspan='5' style='font-weight: 900;'>&nbsp;sex&nbsp;</td></tr>
<tr>
<td style='text-align: left;'>&nbsp;&nbsp;&nbsp;Female&nbsp;</td>
<td style='text-align: right;'>15</td>
<td style='text-align: right;'>8</td>
<td style='text-align: right;'>6</td>
<td style='text-align: right;'>29</td>
</tr>
<tr>
<td style='text-align: left;'>&nbsp;&nbsp;&nbsp;Male&nbsp;</td>
<td style='text-align: right;'>12</td>
<td style='text-align: right;'>9</td>
<td style='text-align: right;'>5</td>
<td style='text-align: right;'>26</td>
</tr>
<tr>
<td style='border-bottom: 2px solid grey; text-align: left;'>&nbsp;&nbsp;&nbsp;#Total&nbsp;</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>27</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>17</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>11</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>55</td>
</tr>
</tbody>
</table>

And this makes perfect sense - there is no reason to suspect that a student's gender has any impact on their STA 215 grade. This sort of reasoning is easy to do when there are a similiar number of Males and Females - but what this wasn't the case?


<table class='gmisc_table' style='border-collapse: collapse; margin-top: 1em; margin-bottom: 1em;' >
<thead>
<tr><th style='border-bottom: 1px solid grey; font-weight: 900; border-top: 2px solid grey; text-align: center;'></th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;A&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;B&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;C&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;#Total&nbsp;</th>
</tr>
</thead>
<tbody> 
<tr><td colspan='5' style='font-weight: 900;'>&nbsp;sex&nbsp;</td></tr>
<tr>
<td style='text-align: left;'>&nbsp;&nbsp;&nbsp;Female&nbsp;</td>
<td style='text-align: right;'>15</td>
<td style='text-align: right;'>8</td>
<td style='text-align: right;'>6</td>
<td style='text-align: right;'>29</td>
</tr>
<tr>
<td style='text-align: left;'>&nbsp;&nbsp;&nbsp;Male&nbsp;</td>
<td style='text-align: right;'>118</td>
<td style='text-align: right;'>88</td>
<td style='text-align: right;'>49</td>
<td style='text-align: right;'>255</td>
</tr>
<tr>
<td style='border-bottom: 2px solid grey; text-align: left;'>&nbsp;&nbsp;&nbsp;#Total&nbsp;</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>133</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>96</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>55</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>284</td>
</tr>
</tbody>
</table>

Here the counts are wildly different between genders - 29 females vs 255 males. How can we tell if the probabilities are still similiar? Easy, break it down into row percentages, where each cell count is divided by the row total. In this case, you should get something like this.

<table class='gmisc_table' style='border-collapse: collapse; margin-top: 1em; margin-bottom: 1em;' >
<thead>
<tr><th style='border-bottom: 1px solid grey; font-weight: 900; border-top: 2px solid grey; text-align: center;'></th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;A&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;B&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;C&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;#Total&nbsp;</th>
</tr>
</thead>
<tbody> 
<tr><td colspan='5' style='font-weight: 900;'>&nbsp;sex&nbsp;</td></tr>
<tr>
<td style='text-align: left;'>&nbsp;&nbsp;&nbsp;Female&nbsp;</td>
<td style='text-align: right;'>51.7</td>
<td style='text-align: right;'>27.6</td>
<td style='text-align: right;'>20.7</td>
<td style='text-align: right;'>100</td>
</tr>
<tr>
<td style='text-align: left;'>&nbsp;&nbsp;&nbsp;Male&nbsp;</td>
<td style='text-align: right;'>46.3</td>
<td style='text-align: right;'>34.5</td>
<td style='text-align: right;'>19.2</td>
<td style='text-align: right;'>100</td>
</tr>
<tr>
<td style='border-bottom: 2px solid grey; text-align: left;'>&nbsp;&nbsp;&nbsp;#Total&nbsp;</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>46.8</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>33.8</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>19.4</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>100</td>
</tr>
</tbody>
</table>

Low and behold, the row percentages are exactly the same between the scenario with 26 males and the scenario with 255 males. This is whats great about the two way table - you can display it as function of row percentages to eliminate by skew in numbers. These row percentage are also, effectively, the probabibilities. See "joint Probabilities."

---

# The Logic behind the Hypothesis Test

Okay, let's take a deep breath here and prepare ourselves for the hypothesis test procedure. Let's take the first small step and establish what the goal of the hypothesis test is for:**The goal of the $\chi^2$ test is to determine if there is an association between the response and explanatory variables**. This is useful to determine vital relationships between cause-and-effect factors. In fact, elements of the $\chi^2$ test were used to examine the relationship between smoking and lung cancer.  


How does the $\chi^2$ test do this? The answer: quite logically. The $\chi^2$ determines if two variables are related by creating a "Null" table - a table where the marginal counts are the same, but the joint probabilities are equal within the rows - this shows *no* relationship between the row and column variables. It creates exactly what an independent table would look like in any particular scenario. Then, it compares the actual, "observed" table to the null table. If the differences between the null table and the observed table are large, then we can logically  say that there is a relationship between the two variables. If the difference between the two tables is minimal, then we can say that there is no association/ relationship between the two variables.

---

## **The Null Table**
<p><span class="marginnote shownote"><!--
<div class="figure">-->
<img src="C4_Notes_files/figure-html/unnamed-chunk-7-1.gif" alt="The Expected Cell Count formula makes the proportions within a column equal across rows."  />
<!--
<p class="caption marginnote">-->The Expected Cell Count formula makes the proportions within a column equal across rows.<!--</p>-->
<!--</div>--></span></p>

So the null table is a table that shows no relationship between the response and explanatory variables. It shows the table we would expect to see if the two variables were independent from one another. Hence, we can call the null table the *expected table*, and all the counts within that table are called *expected cell counts*. 

To calculate expected cell counts, you need perform the below column on *each* cell in the observed table.


$$\text{Expected Cell Count} = \frac{(\text{Row Total} \times \text{Column Total})}{\text{Grand Total}}$$
$$\tiny{\textbf{Note}: \text{You need to perform this calculation for each cell in the table. Ignore the Row Total and Column Total Cells}} $$ 

Once you've calculated each expected cell count and completed your expected table, you are ready to make a formal comparison between your expected table and your observed table to see if there's any difference between the two. **Remember** a large difference between the observed and expected tables means there is a relationship between the explanatory and response variables, and there is no independence. 

Let's keep using the STA 215 grade data to calculate a chi-squared statistic. Here is the observed table again for reference.

<table class='gmisc_table' style='border-collapse: collapse; margin-top: 1em; margin-bottom: 1em;' >
<thead>
<tr><th style='border-bottom: 1px solid grey; font-weight: 900; border-top: 2px solid grey; text-align: center;'></th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;A&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;B&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;C&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;#Total&nbsp;</th>
</tr>
</thead>
<tbody> 
<tr><td colspan='5' style='font-weight: 900;'>&nbsp;sex&nbsp;</td></tr>
<tr>
<td style='text-align: left;'>&nbsp;&nbsp;&nbsp;Female&nbsp;</td>
<td style='text-align: right;'>15</td>
<td style='text-align: right;'>8</td>
<td style='text-align: right;'>6</td>
<td style='text-align: right;'>29</td>
</tr>
<tr>
<td style='text-align: left;'>&nbsp;&nbsp;&nbsp;Male&nbsp;</td>
<td style='text-align: right;'>12</td>
<td style='text-align: right;'>9</td>
<td style='text-align: right;'>5</td>
<td style='text-align: right;'>26</td>
</tr>
<tr>
<td style='border-bottom: 2px solid grey; text-align: left;'>&nbsp;&nbsp;&nbsp;#Total&nbsp;</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>27</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>17</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>11</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>55</td>
</tr>
</tbody>
</table>

Here's the expected table - Not too different from the observed right? We'll have to wait until compute the $\chi^2$ statistic and associated p-value before make a final judgement, but these differences between observed and expected cells seem rather small. Again, this is what we would expect - gender and academic performance not having any association. 

**Note:** It would be good practice to reporduce these expected counts by hand, so you can become comfortable with the proccess and avoid common pitfalls. 


```
## Using sex as id variables
```

<table class='gmisc_table' style='border-collapse: collapse; margin-top: 1em; margin-bottom: 1em;' >
<thead>
<tr><th style='border-bottom: 1px solid grey; font-weight: 900; border-top: 2px solid grey; text-align: center;'></th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;A&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;B&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;C&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;#Total&nbsp;</th>
</tr>
</thead>
<tbody> 
<tr><td colspan='5' style='font-weight: 900;'>&nbsp;exp&#36;sex&nbsp;</td></tr>
<tr>
<td style='text-align: left;'>&nbsp;&nbsp;&nbsp;Male&nbsp;</td>
<td style='text-align: right;'>12.8</td>
<td style='text-align: right;'>8</td>
<td style='text-align: right;'>5.2</td>
<td style='text-align: right;'>26</td>
</tr>
<tr>
<td style='text-align: left;'>&nbsp;&nbsp;&nbsp;Female&nbsp;</td>
<td style='text-align: right;'>14.2</td>
<td style='text-align: right;'>9</td>
<td style='text-align: right;'>5.8</td>
<td style='text-align: right;'>29</td>
</tr>
<tr>
<td style='border-bottom: 2px solid grey; text-align: left;'>&nbsp;&nbsp;&nbsp;#Total&nbsp;</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>27</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>17</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>11</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>55</td>
</tr>
</tbody>
</table>


## The $\chi^2$ Statistic


To compare the observed and expected tables, you'll need to calculate the $\chi^2$ test statistic. This statistic measures the difference between the observed and expected tables - *A large $\chi^2$ statistic means there is a large difference between the observed and expected tables*. The formula do this is relatively straight forward, albeit it can look a little intimidating. Let's take a look:

$$  \chi^2 = \sum_{cells}^{all}{\frac{(\text{Observed}- \text{Expected)}^2}{\text{Expected}}}$$

Don't get intimidated by the formula. It's simply instructing you to perform the fraction $\bigg(\frac{(\text{Observed}- \text{Expected)}^2}{\text{Expected}}\bigg)$ for each cell (just like you did with the expected cell counts) and then add the result from each cell together. So, you are taking the observed cells counts from a given cell, subtracting it by it corresponding expected value, squaring the difference, and dividing by that expected value. Write that number down. Then, do it for every cell. Then add all those individual $\chi^2$ values up, and that's your $\chi^2$ test statistic. 

Let's keep using the STA 215 grade data to calculate a chi-squared statistic. Here are the observed and expected tables for reference.



```
## Using sex as id variables
## Using sex as id variables
```

<table class='gmisc_table' style='border-collapse: collapse; margin-top: 1em; margin-bottom: 1em;' >
<thead>
<tr>
<th style='border-top: 2px solid grey;'></th>
<th colspan='2' style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;A&nbsp;</th><th style='border-bottom: none; border-top: 2px solid grey;' colspan=1>&nbsp;</th>
<th colspan='2' style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;B&nbsp;</th><th style='border-bottom: none; border-top: 2px solid grey;' colspan=1>&nbsp;</th>
<th colspan='2' style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;C&nbsp;</th>
</tr>
<tr><th style='border-bottom: 1px solid grey; font-weight: 900; text-align: center;'></th>
<th style='font-weight: 900; border-bottom: 1px solid grey; text-align: center;'>&nbsp;Expected&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; text-align: center;'>&nbsp;Observed&nbsp;</th> 
<th style='font-weight: 900; border-bottom: 1px solid grey; text-align: center;' colspan=1>&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; text-align: center;'>&nbsp;Expected&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; text-align: center;'>&nbsp;Observed&nbsp;</th> 
<th style='font-weight: 900; border-bottom: 1px solid grey; text-align: center;' colspan=1>&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; text-align: center;'>&nbsp;Expected&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; text-align: center;'>&nbsp;Observed&nbsp;</th>
</tr>
</thead>
<tbody> 
<tr><td colspan='9' style='font-weight: 900;'>&nbsp;sex&nbsp;</td></tr>
<tr>
<td style='text-align: left;'>&nbsp;&nbsp;&nbsp;Female&nbsp;</td>
<td style='text-align: right;'>14.2</td>
<td style='text-align: right;'>15</td> 
<td style='text-align: right;' colspan=1>&nbsp;</td>
<td style='text-align: right;'>9</td>
<td style='text-align: right;'>8</td> 
<td style='text-align: right;' colspan=1>&nbsp;</td>
<td style='text-align: right;'>5.8</td>
<td style='text-align: right;'>6</td>
</tr>
<tr>
<td style='text-align: left;'>&nbsp;&nbsp;&nbsp;Male&nbsp;</td>
<td style='text-align: right;'>12.8</td>
<td style='text-align: right;'>12</td> 
<td style='text-align: right;' colspan=1>&nbsp;</td>
<td style='text-align: right;'>8</td>
<td style='text-align: right;'>9</td> 
<td style='text-align: right;' colspan=1>&nbsp;</td>
<td style='text-align: right;'>5.2</td>
<td style='text-align: right;'>5</td>
</tr>
<tr>
<td style='border-bottom: 2px solid grey; text-align: left;'>&nbsp;&nbsp;&nbsp;#Total wtd. cases&nbsp;</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>27</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>27</td> 
<td style='border-bottom: 2px solid grey; text-align: right;' colspan=1>&nbsp;</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>17</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>17</td> 
<td style='border-bottom: 2px solid grey; text-align: right;' colspan=1>&nbsp;</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>11</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>11</td>
</tr>
</tbody>
</table>

It's often helpful to make a $\chi^2$ table like this one below. It gives the individual $\chi^2$ value for each cell. Once this is complete, you simply add up all the values together, and that's the final $\chi^2$ statistic. This tells us how similiar the observed table is to the expected table.

<table class='gmisc_table' style='border-collapse: collapse; margin-top: 1em; margin-bottom: 1em;' >
<thead>
<tr>
<th style='border-top: 2px solid grey;'></th>
<th colspan='3' style='font-weight: 900; border-bottom: 1px solid grey; border-top: 2px solid grey; text-align: center;'>&nbsp;grade&nbsp;</th>
</tr>
<tr><th style='border-bottom: 1px solid grey; font-weight: 900; text-align: center;'></th>
<th style='font-weight: 900; border-bottom: 1px solid grey; text-align: center;'>&nbsp;A&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; text-align: center;'>&nbsp;B&nbsp;</th>
<th style='font-weight: 900; border-bottom: 1px solid grey; text-align: center;'>&nbsp;C&nbsp;</th>
</tr>
</thead>
<tbody> 
<tr><td colspan='4' style='font-weight: 900;'>&nbsp;sex&nbsp;</td></tr>
<tr>
<td style='text-align: left;'>&nbsp;&nbsp;&nbsp;Female&nbsp;</td>
<td style='text-align: right;'>0.0457</td>
<td style='text-align: right;'>0.1155</td>
<td style='text-align: right;'>0.0077</td>
</tr>
<tr>
<td style='border-bottom: 2px solid grey; text-align: left;'>&nbsp;&nbsp;&nbsp;Male&nbsp;</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>0.0410</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>0.1036</td>
<td style='border-bottom: 2px solid grey; text-align: right;'>0.0069</td>
</tr>
</tbody>
</table>


```r
chi$statistic
```

```
## X-squared 
## 0.3203828
```


# The Hypothesis Test ($\chi^2$ Test of Homogeniety)

Now that we've gone over the motivation and the utility of the $\chi^2$ statistic, lets go over the 5-step Hypothesis test procedure for this statistic. Again, this is going to be very similiar to chapters 2 & 3, but its *just* different enough that we have to talk about what's different for this chpater. 


1. **Identification**
2. **Hypotheses**
<p><span class="marginnote shownote"><!--
<div class="figure">-->
<img src="C4_Notes_files/figure-html/unnamed-chunk-13-1.gif" alt="...Every Hypothesis is the same?"  />
<!--
<p class="caption marginnote">-->...Every Hypothesis is the same?<!--</p>-->
<!--</div>--></span></p>
$$ \scriptsize{\text{Ho: There is no association between the response and explanatory variables;}}$$
$$\scriptsize{\text{Ha: There is an association between the response and explanatory variables}}$$
Thats it. There's no left or right-tailed test to perform in chapter 4. Every hypothesis for the $\chi^2$ test will look like this. This is because the $\chi^2$ distribution doesn't really have left or right tails from which the measure the area under- certainly not like the normal or t-distributions from chapters 2 and 3.

<p><span class="marginnote shownote"><!--
<div class="figure">-->
<img src="C4_Notes_files/figure-html/unnamed-chunk-14-1.png" alt="The chi-sqaured Distribution"  />
<!--
<p class="caption marginnote">-->The chi-sqaured Distribution<!--</p>-->
<!--</div>--></span></p>

3. **Assumptions/ Conditions/ Test-Statistic** 

   + **Assumption**
The $\chi^2$ statistic follows a $\chi^2$ distribution with $(r-1)\times(c-1)$ degrees of freedom.

Remember how the t-distrution from chapter 3 changes shape depending on the degrees of freedom? The $\chi^2$ distribution does the same thing, but on a more drastic scale and with a different formula to calculate the degrees of freedom. *r* referrs to the number of rows, while *c* referrs to the number of columns. You'll need to calculate the degrees of freedom to find the p-value later on. 

  + **Conditions**

    + No Expected Cell Counts < 1
    + No more than 20% of Expected Cell Counts < 5
      
  + **Calculate the Test Statistic**

$$  \chi^2 = \sum_{cells}^{all}{\frac{(\text{Observed}- \text{Expected)}^2}{\text{Expected}}}$$
4. Find the p-value, Make a Decision

Finding the p-value follows the same logic as in previous chapters. There's a table in the appendix (A.6?)that is constructed specifically for the $\chi^2$ distribution. Making the decision is the exact same. If your p-value is less than alpha, reject the null hypothesis that there is no association between the variables. 

5. Conclude

Summarize what your decision means in terms of the population. Same as its always been.






# A Full Example
Let's go through a full example of the hypothesis test procedure using some interesting survival data. 


```
##   df$Survived|No df$Survived|Yes
## 1      1171.8264        559.1736
## 2       318.1736        151.8264
```

```
## X-squared 
##  454.4998
```
## Identification
<br>
<br>

<br>

<br>

## Hypotheses
<br>

<br>
## Assumption
<br>

<br>
## Conditions
<br>

<br>
## Test Statistic
<br>
<br>

<br>

<br>

<br>

<br>
## p-value & Decision
<br>

<br>

<br>

## Conclusion
<br>
<br>


<br>
<br>





