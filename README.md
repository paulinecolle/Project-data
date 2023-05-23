# Data management project: Abritel
## By Iman Ajdamova and Pauline Colle
### Instructions on how we constructed our data management project 
On this file, we will go through the different steps of each data frame and the eventual particularity in the code and why we did so. The question we aimed at answering with this project was *"How to choose the best accommodation for your vacations in Belgium?"*

**1. Webscrapping part**

The project was realised using Selenium due to the structure of the website. The first step consists therefore in installing all the packages useful for our project and then opening the Abritel webpage through Selenium and rejecting the cookies.

We then proceeded to collect all available information directly from the **main page**, as most of the relevant information was found there. We did so by using a loop that will go through all the pages of the websites in order to collect the information of all the propositions of the website considering our research characteristics. Here are some explanation on the code for this part: 
- When collecting data, we ran into difficulties because the items would not load until we scrolled all the way to the bottom of the page each time, so only data for the first few cells was collected. For this reason, we specifically designed a scroll command that would scroll all the way through the different pages before proceeding to collect the data. 
- The data collected on this part were: 
    - The names of each accommodation
    - The price per night
    - The total price: we considered a period of two weeks at the beginning of September because it was the period at which the most accommodations were available when we realised the Webscrapping.
    - The type of accommodation: if it is a house, an apartment, a cottage etc.
    - Whether the host is considered premium or not: we assigned the value 1 if the accommodation is considered to have a premium host and zero otherwise.
    - The number of stars awarded by previous guests (rating). As the information was not consistent for all the accommodations, we had to make a special code for this category and the two following ones. 
    - The number of reviews left by previous customers (a sign that it is a popular accommodation or not).
    - The type of ad: whether it is a professional ad, a private ad or not specified.
    - The number of beds
    - The number of bedrooms
    - How many guests are allowed
- The information was then cleaned and finally stored in a data frame and exported as an Excel file so as not to lose it. 

The information about the **localisation** of the different accommodation was  not present in the principal pages of the website where each housing cells were pooled but could only be found in each individual page of each housing, so we had to develop a command that opened each cell of the hundreds of observations and collected the location info and went back to the main page and repeated that same process with each observation of our sample. Two items were collected:
- The name: to be able to connect this data frame to the previous one.
- The localisation: after the name of the town of each accommodation were collected, geopy was used to collect the GPS details. It should be noted that geopy is not perfect, so we add to manually correct a few mistakes on the Excel file.

This information was stored in another data frame, and also exported as an Excel file to not lose the information. 

Finally, thanks to the "Names" column, the two previous data frame were merged into one.

**2.Visualisation part**
- Installation of all the packages.
- Import the merged data frame with all the information we webscrapped.
- Converting the data to float type in order to be able to use them in graphs.
- Descriptive statistics : we constructed many graphs to visualise the different properties of our data set, for example, to see if there was any relation with the price and other characteristics such as rating, type of announcement, etc. (All necessary explanations are written in the Visualisation notebook)

In this notebook can be find some elements of response to our question, based on the graphs realised.

**3. Modelling**

This last notebook constitute the modelling part. We realised a linear regression with machine learning.

The first part consists in loading the data from the same Excel sheet as in notebook 2. Because coming from Excel, the data are not completely ready for use, we cleaned them. We transform the numerical values in float types and added the variables of the logarithm of the price.

Before starting the regression, we realised a correlation matrix to have an idea of how the variables are correlated with each other.

Then, we started the supervised machine learning part. The code for this procedure comes mainly from the notebook about this part of the content, but adapted for our case. All interpretation about the results can be find in the notebook.
    
