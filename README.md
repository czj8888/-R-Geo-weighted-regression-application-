# -R-Geo-weighted-regression-application-
This application was designed to explore the geo-relationship between east China economy and indicators. The program is written by R shiny package which allow users to select models and input variables.

#The raw data consists of 2 parts:
1. Statistics data of economic conditions and GDP indicators (table.csv)
2. Chinese administrative regions shapefile (CHN_adm_shp folder)

#Run Project(1).R to open the application

#Geo-weighted regression:

1. Weighted regression
In normal regression model, a regression model is built based on the least square error of all data points in training data set. It assumes that each data points are totally independant.
In practical cases sometimes each individual will afftect each other by somehow, to solve this problem weighted regression is designed to solve this problem: when training the data, the value of an individual (for example, Xn) is a sum of weighted value from its neighbouring data points Xn-2, Xn-1, Xn+1, Xn+2... and itself, so the value Xn will become sum(weight(n)*value(n)). 
The values are normally unevenly weighted, which means larger weights are given to neighbouring points and less weights for distant points.

2. Geo-weighted regression
Geo-weighted regression is a weighted regression methodology which considers the effects from the geo-graphically neighbouring points. For example, in our project, each city will be an individual, containing the dependant variable (GDP) and indipendant variables (assumed GDP indicators, such as government investment on education...). 
When running the regression model, each individual will build a model on itself, including all the neighbouring individuals as training examples and then return the parameter of each x-variable. 

#The interface user guide:
1. Preparations
Before running the script, listed below are the 
  (1) shapefile
  (2) a csv file containing the economic data
