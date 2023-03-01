# Does Money Buy Medals? 
Author(s) : [Esther](https://www.linkedin.com/in/esther-ki-26362b183/), [Gyubeen](https://www.linkedin.com/in/gyubeen-park-a1017024b/), [Satwik](https://www.linkedin.com/in/saatweek/)

## Abstract

In this project, we aimed to investigate whether there is a relationship between GDP and number of medals won in the Winter Olympics using the data sourced from Winter Olympics Medal Count dataset and Worldwide GDP History dataset. We performed a simple linear regression analysis with the weighted total medal points as our response variable and log(GDP) as our explanatory variable. We set up our null hypothesis as $\hat{\beta_1} = 0$, meaning there is no relationship between the two variables and our alternative hypothesis as $\hat{\beta_1} > 0$, meaning there is a positive relationship between the two variables. From the results, we obtained  $\hat{\beta_0} = -158.733$, $\hat{\beta_1} = 7.326$, p-value for $\hat{\beta_1} = 7.66e-07$, and confidence interval for $\hat{\beta_1} =  (4.51, 10.14)$. Therefore, we reject our null hypothesis and conclude that there is a positive relationship between
the total medal points and log(GDP).

## Background/Introduction

At the last Beijing Winter Olympics, 2,861 athletes from 91 countries participated in a great competition. There are many factors that affect the number of medals, such as economic factors, geographical factors, and host country effects. We decided to investigate the impact of the country's economic power on medals, so we analyzed the relationship between GDP and medal count. We specifically looked  at the Winter Olympics because Winter Olympic sports require special training facilities, so the results vary from country to country.

## Methods

#### a. Source of the Data:
The data was collected from the Winter Olympics Medal Count dataset and Worldwide GDP History dataset. The size of data is 175 rows and 12 columns. This is the data on the countries that won medals in the 10 Olympics, from the 1984 Sarajevo Olympics to the 2018 Pyeongchang Olympics. The collected variables are host country, host city, participating countries, number of gold, silver, and bronze medals, GDP, GDP per capita, number of athletes and total medal points. Total medal points are calculated by weighting 6 points for gold, 4 points for silver, and 3 points for bronze. Countries who won no medals are not included.
#### b. Statistical Methods:
We assumed that the residuals are independent and identically and normally distributed. We used R to run a
simple linear regression model. Our population model is the following: 
<p align="center">$Total Medal Points= \beta_0 + \beta_1*log(GDP)_i + \epsilon_i$</p>

## Results

#### a. Transformation and Descriptive Statistics
We took the log of GDP to scale and make the data points spread out more evenly (Figure 1.1 and 1.2).

![](https://user-images.githubusercontent.com/43529908/222273858-e71b899f-8dba-4440-9d8f-95eca88fcde5.png)  |  ![](https://user-images.githubusercontent.com/43529908/222273941-1deb5daf-5bff-4753-99ec-c20a114b5177.png)
:-------------------------:|:-------------------------:
Figure 1.1 : Total Medal Points vs. GDP | Figure 1.2 : Total Medal Points vs. log(GDP)


| Variables               | Mean (SD)           |
| ----------------------- | ------------------- |
| Total Medal Points      | 37.71 (36.76)       |
| GDP                     | 1.63e+12 (3.14e+12) |
| log(GDP)                | 26.81 (1.82)        |

**Table 1 : Summary Statistics of Variables of Our Interest**

#### b. Estimated Model and Results

Our estimated model is the following:

<p align="center">
$\widehat{TotalMedalPoints_i} = \hat{\beta_0} + \hat{\beta_1}*log(GDP)_i$
</p>

$\hat{\beta_0}$ is the estimated average total medal points for countries with log(GDP) of 0 and $\hat{\beta_1}$ is the estimated average difference in total medal points for countries whose log(GDP) differs by one unit. By running the regression model in R, we obtained the results in Table 2.
|                                       |               | 
| ------------------------------------- | ------------- |
| $\hat{\beta_0}$                       | -158.733      |
| $\hat{\beta_1}$                       | 7.326         |
| p-value ($\hat{\beta_1}$)             | 3.83e-07      |
| Confidence Interval ($\hat{\beta_1}$) | (4.51, 10.14) |

**Table 2 : Results from Simple Linear Regression Model with Total Medal Points and log(GDP)**

#### c. Secondary Analysis
Our estimated model for secondary analysis  is the following:
<p align="center">
$\widehat{TotalMedalPoints_i} = \hat{\beta_0} + \hat{\beta_1}*Number Of Athletes_i$
</p>
$\hat{\beta_0}$ is the estimated average total medal points for countries who send 0 athletes, and $\hat{\beta_1}$ is the estimated average difference in total medal points for countries whose number of athletes differs by one unit. By
running the regression model in R, we obtained the results in Table 3.

|                                       |              | 
| ------------------------------------- | ------------ |
| $\hat{\beta_0}$                       | -5.06204     |
| $\hat{\beta_1}$                       | 0.52762      |
| p-value ($\hat{\beta_1}$)             | < 2e-16      |
| Confidence Interval ($\hat{\beta_1}$) | (0.45, 0.60) |

**Table 3 : Results of Secondary Analysis with Total Medal Points and Number of Athletes**

## Discussion

For our primary analysis of the relationship between log(GDP) and total medal points, we set up our nullhypothesis as $\hat{\beta_1} = 0$, meaning there is no relationship between the two variables and our alternative hypothesis as $\hat{\beta_1} > 0$, meaning there is a positive relationship between the two variables. After looking at the value of $\hat{\beta_1}$, p-value and the confidence intervals, we reject the null hypothesis. Therefore, there is a correlation between the log(GDP) and average total medal points. Our p-value is 3.83e-07 which is much lower than 0.05, and the confidence interval for $\hat{\beta_1}$ is (4.51, 10.14), which does not include 0. This result tells us that the country's economic level contributes to the sports industry, leading to more Olympic medals.

For our secondary analysis, we analyzed the relationship between the number of athletes with the total medal points. Our null hypothesis was $\hat{\beta_1} = 0$, meaning there is no relationship between the number of athletes a country sends and the total medal points and our alternative hypothesis was  $\hat{\beta_1} > 0$, meaning there is a positive relationship between the two variables. Upon doing the analysis, we obtained p-value ≤ 2e-16, and the confidence interval for $\hat{\beta_1}$ = (0.45, 0.60) which does not include 0 as well. This means we reject our null hypothesis and there is a positive relationship between the number of athletes and total medal points.

Let us now look at other variables that might affect the total medal points or GDP.
- Latitude: Richer countries are mainly located on the higher latitude and can also invest more money into the required infrastructure for these games. This makes it easier for athletes from high latitudes to practice sports.
- Host Effect: It is observed that countries who host the Olympics win more medals than they typically do and Olympics are typically organized in relatively richer nations.
- Population: Higher populated countries are able to send a lot of athletes, which increases their chances of winning.

Here are some of the limitations of our analysis:
- Calculation of Total Medal Points: In our calculation, the gold medal is associated with the weight of 6, the silver medal with a weight of 4, and bronze with 3. But these weights were assigned arbitrarily based on how important we think these medals are as analysts. The weights could be any other combination of numbers depending on how important these medals are to anyone.
- Top 3 Ranks: Since our data contains the information about the medals, we limit our analysis to comparing only the top three. Looking up to the top 10 of the game results may help us analyze more precisely by increasing the sample size as we include the countries that have not won a medal.
- YoY changes in GDP:  While our data has the year column, we limit ourselves to GDP and total medal points. This makes it hard to observe how changes in GDP affect the total medal points of a particular country. This also makes it difficult to see countries with consistent performance and countries that are outliers that have performed well once and then not performed well again.

For future work, along with addressing the aforementioned issues, we can work on the following few points:
- A multilinear regression considering other important factors such as GDP per capita, number of athletes, population, etc.
- We can do a time series analysis of each country by comparing their GDP and total medal points throughout the years.
- We can also take a look at the host effect or home advantage effect, which means the hosting team performs better than other visiting teams.

## Reference

1. Kaggle 
    - [Winter Olympics Prediction - Fantasy Draft Pick](https://www.kaggle.com/datasets/ericsbrown/winter-olympics-prediction-fantasy-draft-picks)
    - [Winter Olympic Medals 1924 - 2018](https://www.kaggle.com/datasets/ramontanoeiro/winter-olympic-medals-1924-2018)
2. The World Bank
    - [GDP Data](https://data.worldbank.org/indicator/NY.GDP.MKTP.CD?end=2020&start=1984&view=chart)
3. Articles
    - [Does economy determine a country's performance at Olympics?](https://www.thehindu.com/data/data-does-economy-determine-a-countrys-performance-at-olympics/article61430189.ece)

## Appendix

- Plots for checking conditions (diagnostic plots)

| 1. Linearity | 2. Independence |
:-------------------------:|:-------------------------:
| ![](https://user-images.githubusercontent.com/43529908/222273941-1deb5daf-5bff-4753-99ec-c20a114b5177.png) | Each country is independent of one another. We assume that all the country's GDP and number of medals are independent. |
| **3. Normality** | **4. Equal Variance** |
| ![qq_plot](https://user-images.githubusercontent.com/43529908/222283149-cc937ae5-8f14-484a-98d1-66ece5431689.png) | ![res_vs_fit](https://user-images.githubusercontent.com/43529908/222283234-b3488996-0520-4384-8147-451280114e1b.png)
