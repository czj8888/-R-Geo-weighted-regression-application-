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

#The interface user instructions:
1. Preparations
First of all, place the program folder at root directory under C:/
Before running the script, listed below are the 
  (1) shapefile (CHN_adm_shp folder)
  The shapefile is downloaded from gadm.org. It contains necessary geographic information when running the regression model and visualizing   the paramter estimates in polygons.The shapefile consists of 344 prefecture level cities (the second admin level)       
(Taiwan's data hasn't yet been included)
  (2) a csv file containing the economic data (in our example, table.csv)
 
 2. Upload the table.csv (which records the economic data in east China)
    Other economic data could also be uploaded, but please notify that each city in csv file should be conresponding to the city in the shapefile. Any record in the  csv file which is missing in the shape file will make the program crush. (you may refer to the CHN_adm.csv. All cities available are listed in this file.)
 
 3. Select variables
    Here is the interface design of the variable selection tab. Before running the model we need to check the correlations between each     pair of economic indicators (x-variables). 
    In the listbox on the top-left, you can choose the input variables and explore their relations. Graphs showing the multivariate         correlations will be displayed on the right part.
    
 4. Building models
    The listboxes on the bottom-left are for model input purpose. We allow users to choose both normal linear regression method and gwr     for comparison purpose. 
 5. model interpretation
    After select the variables and the result will be displayed in the modellint tab. We have 2 maps to illustrate the modelling result:     The first map is for the parameter estmates, and the second map is the p value (confidence level) of the parameter.
    To display the effects from different varibles, select the listbox on the left.
