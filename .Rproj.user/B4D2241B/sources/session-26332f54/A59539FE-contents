---
title: "Unemployment in UK" 
subtitle: "MTH6139 Time Series" 
author: "Aiyi Zhang - 230385700" 
date: "Spring term 2026"
output: 
  html_document:
    toc: true
    toc_float: true
    theme: spacelab 
    highlight: tango
    
---
#
```{r, echo=FALSE}
# This code will display the QMUL logo at the top right of the page
# Do not change this code
htmltools::img(src = knitr::image_uri("images/QMlogo.png"),
               alt = 'logo',
               style = 'position:absolute; top:0; right:0; padding:10px; width:20%;')
```

---

# Unemployment Rate (age 16 and over)

This report looks at the unemployment rate from 2000 to 2025 in UK

---

## What does it mean to be unemployed?

- You currently do not have a job

- You are actively looking for work and can start working

To be unemployed, a person must:

- Be of working age 

- Not be working

- Actively seeking a job

---

# Statistics 

### Office for National Statistics

*Collected from Labour market statistics time seriers* <https://www.ons.gov.uk/employmentandlabourmarket/peoplenotinwork/unemployment/timeseries/mgsx/lms>

**Here is a chart produced by Office for National Statistics**


```{r, echo=FALSE}
htmltools::img(src = knitr::image_uri("images/Unemployment_chart.png"))
```

### Summary

In 2000, the unemployment rate stood at 5.4%, this gradually declined till 2006, which rates began to rise reaching the **highest** point of **8.1% in 2011** (shown by the *green* line in the graph below). 

#

**Why?**

This rise is linked to the **Global Financial Crisis** in 2008. Which resulted in significant job losses. In 2011, unemployment has reached its peak since 1994, with 2.57 million people said to be out of work over the June to August period which is the highest since the autumn of 1994, where 1 million unemployed were young people. 

This increase was primarliy due to a stalling ecnomic recovery, the economy grew at half the necessary pace, whilst weak consumer demand and high inflation rates limited businesses ability to hire. Additionally, following of the recession from the crisis led many businesses to close or downsize,reduced investment levels and decline in demands of goods and services. 

---

We then see a decline in unemployment rate, reaching the lowest point of **3.8% in 2019**. We then see it again in 2022 which from then on there was a steady increase in unempployment rate.

Between 2020 to 2021, there is an increase in unemploymnet rate to 4.6%.

**Why?**

**COVID hit!** 

Due to the COVID-19 pandemic there was:

- Lockdowns and restrictions : business closurer and people had to stay home
- Job losses and reduced work : Shops/resturarents had to cut staff due to no customers and no demand for labour

---

# Graph 

## Unemployment Rate in UK from 2000 - 2030

```{r, echo=FALSE, message=FALSE, warning=FALSE}
#so no code is shown 
unemployment_year = read.csv("unemplyment_data.csv")
#this alows R to read the csv file

colnames(unemployment_year) = c("ds", "y")
#changing the names to ds and y to be able to use prophet
#will not work if not ds and y
unemployment_year$ds = as.Date(paste0(unemployment_year$ds, "-01-01"))
#turns my year into dates as it only undertsands dates not just year
library(prophet)
#this allows me to use prophet functions where by seen below where i use prophet(unemployment_year)
model = prophet(unemployment_year)
#implementing the model
prediction = make_future_dataframe(model, periods = 5, freq = "year")
#this makes it that the future predicitons is in the next 5 years and in frequencies of years and not days 
#obtained at <https://mode.com/example-gallery/forecasting_prophet_r_cookbook>
future_prediction = predict(model, prediction)
#using model and implementing it to all data 
#draws a graph of my data
library(ggplot2)
plot (model, future_prediction) + geom_vline(xintercept = as.Date("2025-12-31"), colour = "red", linetype = "dashed", size = 0.5) + geom_vline(xintercept = as.Date("2011-01-01"), colour = "green", linetype = "dashed", size = 0.5) + labs(x = "Year", y = "Unemployment Rate (%)")
#creates a red dash line at 2026 and a green at 2011
#allows me to change ds and y to titles for unemployment and year
#obtained at <https://psyteachr.github.io/introdataviz/additional-advanced-plots-and-customisation-options.html>
```


**The table below shows *predicitons* of unemployment rate for the next five years, based on the assumption that no unforessen events where to take place!** Indicated by the **red** line.


- **2026** : 4.7%

- **2027** : 4.5%

- **2028** : 4.4%

- **2029** : 4.6%

- **2030** : 4.4%



```{r, echo=FALSE, message=FALSE, warning=FALSE}
tail(future_prediction[c('ds', 'yhat', 'yhat_lower', 'yhat_upper')])
#gives us a prediction
prophet_plot_components(model, future_prediction)
#allow you to visualize individual forecast components - showing trend in the data
#<https://mode.com/example-gallery/forecasting_prophet_r_cookbook>
```


---

# Unemployment in Quarters from 2023 to 2028


The chart below illustrates the unemployment rate in UK from 2023 to 2028 on a quarterly basis which also includes forcasting for the next eight quarters.  

We see a steady increase in unemploymnet rate from 2024 Q2 to 2025 Q4 rising from 4.2% to 5.2% which is the highest rate in nearly five years. This is due to **businesses slowing down hiring**, because of the increase in minimum wage and employer national insurasnce contributions, this cause business to face an increases in their costs.

---

Pedictions show there will be a steady increase in unemployment rate in the next eight quarters from 2026 to 2028 *(shown from the yellow line)*:

```{r, echo=FALSE, message=FALSE, warning=FALSE}
#same code as the unemployed-year but fpr quarter 

unemployment_quarter = read.csv("unemployment_quarter.csv")

colnames(unemployment_quarter) = c("ds", "y")
unemployment_quarter$ds = as.Date(paste0(unemployment_quarter$ds, "-01"))
#dont need 01-01 as this data includes months 
library(prophet)

model1 = prophet(unemployment_quarter)
prediction_quarter = make_future_dataframe(model1, periods = 8, freq = "quarter")
#changed freq to quarter as we are working with quarter and no year 
future_prediction_quarter = predict(model1, prediction_quarter)
plot (model1, future_prediction_quarter) + geom_vline(xintercept = as.Date("2025-12-01"), colour = "yellow", linetype = "dashed", size = 0.5)
```
---

# What next?

The governmnet should look to expand access to education and trainning in areas such as healthcare or technology.

**Why?**

- Helps reduce unemployment through individuals developing skills

- Making workers more employable

- Supports long-term economic growth

**How?**

- Aprrenticeship Scheems

- Grad training programmes 

**Also look to support businesses:**

- Reduce employer National Insurance contributions

- Implement tax incentives for hiring employees

---

## Real Example


To give a real world perspective on the labour market conditions currently, I am using my own experience finding graduate roles.

A total of **80 job applications** were submitted, resulting in **43** rejections, **30** online assessments, **15** interviews, and **1** assessment centre opportunity.

Where **response rate** is:

```{r, echo=FALSE}
response_rate <- 50 / 80 * 100
response_rate
```
As you can see, the possiblilty to hear back from a company is 62.5% whilst out of 80 application I was only able to reacieve 1 accessment centre. The compition in the job market now is very competitive, making it harder to be able to find jobs for students who are to graduate.

**Rejection rate:**
```{r, echo=FALSE}
rejection_rate <- 43 / 80 * 100
rejection_rate
```
**Interview rate:**
```{r, echo=FALSE}
interview_rate <- 15 / 80 * 100
interview_rate
```
**Assessment Centre:**
```{r, echo=FALSE}
final_stage_rate <- 1 / 80 * 100
final_stage_rate
```

---

**Table of Data:**

```{r, echo=FALSE}
applications <- data.frame(
  Stage = c("Applications", "Online Ass", "Interviews", "AC", "Rejections"),
  Count = c(80, 30, 15, 1, 43)
)

applications
```


---

## Bar Chart

```{r, echo=FALSE, message=FALSE}
barplot(applications$Count, names.arg = applications$Stage)
# turning data into a bar chart
```

---

Socurses used to create this article:

<https://www.ons.gov.uk/employmentandlabourmarket/peoplenotinwork/unemployment/timeseries/mgsx/lms>

To help code:

<https://flowingdata.com/2012/12/17/getting-started-with-charts-in-r/>

<https://mode.com/example-gallery/forecasting_prophet_r_cookbook>

<https://psyteachr.github.io/introdataviz/additional-advanced-plots-and-customisation-options.html>

<https://facebook.github.io/prophet/docs/quick_start.html#r-api>
