---
title: "Mobility and Income Segregation in Madrid, Spain"
excerpt: "Detailed portfolio entry describing my master's thesis work."
collection: portfolio
permalink: /portfolio/masters-thesis/
---

<!-- Replace this placeholder text with a detailed description of your master's thesis. -->

- **Program: Social Data Science, M.Sc.** 
- **Institution: University of Copenhagen.** 
- **Thesis Title: Mobility and Income Segregation in Madrid, Spain.** 
- **Advisors: Sandro Sousa and Yevgeniy Golovchenko.** 
- **Date: September 2024 to December 2024**

## Links of Interest

The final paper is available [here](/files/thesis.pdf).

The code built to perform the study is available at the following [GitHub Repo](https://github.com/carobs9/segregation-madrid).

You can view the resulting mobility network by clicking [here](https://carobs9.neocities.org/no_threshold).

## Overview

This study explores the relationship between income inequality and urban mobility in the city of Madrid. Literature shows that bringing mobility into the study of inequality and segregation can bring an extra dimension to its study. By using a granular mobility dataset of trips throughout a month of 2022 (obtained from [MITMA Estudios Básicos](https://www.transportes.gob.es/ministerio/proyectos-singulares/estudios-de-movilidad-con-big-data/estudio-basico-diario)), a series of methods are developed to measure which districts play a central role in pulling and pushing travellers, and to measure which income groups travel more, and longer distances within the city. This research provides insights on the ongoing income segregation patterns in Madrid, and identifies slightly homophilic travelling tendencies. It also reveals that lower income groups tend to travel more and longer on average than higher income groups. This research contributes to the field of urban studies and emerging fields like Science of Cities or Urban Data Science, and aims to aid policymakers to identify mobility isolated areas in the urban space to develop effective policies to reduce the negative effects of gentrification and segregation.

## Objectives

The main research question driving my research is:

>  To what extent do residents from economically segregated districts in Madrid move differently than those in other districts?

To answer this question, I developed the following hypotheses to guide research:

> Low-income and highly segregated districts push residents out for daily mobility purposes, like work or recreational, whereas high-income and low segregated districts pull residents, as these districts tend to offer higher amenities and work possibilities.

> Residents from low-income and highly segregated districts tend to make a higher number of trips to high-income and low segregated districts than vice versa.

> Residents from low-income and highly segregated districts tend to perform, on average, longer distance trips than those living in high-income and low segregated districts.

## Methods

### Exploratory Analysis

I perform an exploratory analysis to address the state of income distribution in Madrid during 2021. This allows me to select the appropriate income variables for the study. To do so, (1) I plot and study the distribution of six income estimators to understand which are more accurate for representing the income and segregation levels of the districts. Based on this analysis, I select two key variables to understand the interactions between mobility and income: the median income per consumption unit and the Gini index by district. (2) I then calculate Global and Local Moran indices for each district based on the median income per consumption unit to illustrate the clustered patterns of income distribution in the city.

### Test Hypothesis 1

I build an origin-destination (OD) dataset containing normalised trip counts within and between districts. These counts are used to build a mobility network and a consequent adjacency matrix. The construction of a network allows to quantitatively analyse the in and out-weights of the nodes. Lastly, I build complementary assortativity matrices based on trips between income and Gini index deciles to study whether there are any mobility patterns across deciles.

### Test Hypothesis 2

I use the previously created trip counts dataset. The districts of origin and destination are classified into four quantiles based on the median income and also on the Gini index values, and I compare the differences among the furthest quantiles. This allows to further analyse the total number of trips between and within districts based the income background of the individuals.

### Test Hypothesis 3

I analyse the average distance of the trips based on the four aforementioned quantiles by variable. I retrieve the average trip distance by OD pair, and compare these based on the top and lowest quantile.


## Results

Based on this analysis, I conclude that there is spatial autocorrelation in terms of the median income per consumption unit in the city of Madrid in 2021, with significant clustering patterns in 48% of the districts.

Based on the assortativity matrices and the adjacency matrix, I conclude that there is a moderate tendency of individuals to stay within their own Gini index deciles, performing a relatively high number of intra-district trips, but still showing certain intra-district interaction. A lower assortativity pattern was found in the case of median income deciles, indicating higher mixing, but the results were not found to be statistically significant.

No significant relationship between low median income, highly segregated districts and out-weight was found, nor a relationship between high median income, low segregated districts and in-weight. In fact, a significant, positive relationship between highly segregated districts and the in-weight was found.

I conclude that residents from the lowest median income quantile travel slightly longer distances on average than residents from the highest median income quantile. Residents from the highest Gini index quantile travel shorter distances on average than residents from the lowest Gini index quantile. I also conclude that the average distance of most trips falls under a 0.5 km - 2.5 km window, and that those performing the longest average trips belong to the low-income and low-Gini quantiles.