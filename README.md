# Project-data
Instructions on how we constructed our data management project : 
1. Webscrapping part
    -Installation of all the packages that were useful for our project.
    -Starting the webscrapping process by opening the website page Abritel and rejecting the cookies.
    -We then collected all the different pieces of information we chose to add later into our data frames using a loop that will go through all the pages of the websites in order to collect the information of all the propositions of the website considering our research characteristics. 
    -While working on the collection of data, we had to specially design a scroll command that would scroll entirely through the different pages and collect the data progressively because otherwise the data wouldn't have loaded and the data collection was not possible. Indeed, only the first cells were loading without the scroll and thus only the data concerning those first few cells was collected.
    
   -Peut etre expliquer pourquoi on a fait plusieurs dataframe qu on a merge ? 
   
   -Afterwards, the data was stored in a data frame. However, note that the location information data was not present in the principal pages of the website where each housing cells were pooled but could only be found in each individual page of each housing so we had to develop a command that opened each cell of the hundreds of observations and collected the location info and went back to the main page and repeated that same process with each observation of our sample. All this information on the location of the housings were stored in another data frame. 
   -Then the different data frames were exported as Excel files because it was too time-consuming to re-load all of the webscrapping part. You will notice that the next two parts are based on those Excel files.
