# Data management project: How to choose the best accommodation for your vacation in Belgium?
## By Iman Ajdamova and Pauline Colle
### Instructions on how we constructed our data management project 
On this file, we will go through the different steps of each data frame and the eventual particularity in the code and why we did so. The question we aimed at answering with this project was *"How to choose the best accommodation for your vacation in Belgium?"*

**1. Webscrapping part**

The project was carried out using Selenium, due to the structure of the website. The first step was therefore to install all the packages needed for our project and then open the Abritel webpage through Selenium and reject the cookies.

We then proceeded to collect all information directly available on the **main page**, as most of the relevant information could be found there. We did so by using a loop that goes through all the pages of the website.

Here are some explanation about the code for this part: 
- When collecting data, we ran into difficulties because the items would not load until we scrolled all the way to the bottom of the page every time. Therefore, only data for the first few cells was collected. For this reason, we specifically designed a scroll command that would scroll all the way through the different pages before proceeding to collect the data. 
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
- For technical reasons, we separated the information into several data frames, and eventually merged them into a single one. Indeed, we encountered some difficulties in collecting the data, in particular the price data was not always collected for each cell. Placing it in a separate notebook was a way to check whether it was the same length as the other data. In addition, we are aware that there is an error at cell 31 for the data frame of the name, type and hote premium. However, in the end, all the required information was collected and since running the cells takes several hours, we decided to leave it like this.
- The information was then cleaned and finally stored in a data frame and exported as an Excel file so as not to lose it. 

The information about the **localisation** of the different accommodations was  not present on the main pages of the website but could only be found on the individual page for each housing. We therefore had to develop a command that open each cell of the hundreds of observations, collect the localisation, return to the main page and repeat the same process with each observation in our sample. Two items were collected:
- The name: to be able to connect this data frame to the previous one.
- The localisation: after collecting the town names of each accommodation, geopy was used to collect the GPS coordinates. Note that geopy is not perfect, so we had to manually correct a few errors in the Excel file.

This information was stored in another data frame, and also exported as an Excel file  so as not to lose it. 

Finally, thanks to the "Names" column, the two previous data frames were merged into one. The file "Abritel_merged.xlsx" is the one that will be used for the rest of the project.

**2.Visualisation part**

The first steps consist in loading and cleaning the data, with steps such as:
- Installation of all the packages.
- Import the merged data frame with all the information we webscrapped.
- Converting the data to float type in order to be able to use them in graphs.

Then, the data will be represented in the form of graphs or maps:
- Descriptive statistics : we constructed many graphs to visualise the different properties of our data set, for example, to see if there was any relation with the price and other characteristics such as rating, type of announcement, etc. All necessary explanations are written in the Visualisation notebook.

In this notebook can be found some elements of response to our question, based on the graphs realised.

**3. Modelling**

This last notebook constitutes the modelling part. We realised a linear regression with supervised machine learning, with the logarithm of the price per night as a dependent variable.

The first step consists in loading and cleaning the data from the same Excel sheet as in notebook 2. Because coming from Excel, the data are not completely ready for use, we cleaned them. We transformed the numerical values into float types and added the variables of the logarithm of the price.

Before starting the regression, we realised a correlation matrix to have an idea of how the variables are correlated with each other.

Then, we started the supervised machine learning part. The code for this procedure comes mainly from the notebook seen in class about this part of the content, but adapted for our case. All interpretation about the results can be found in the notebook.
    
