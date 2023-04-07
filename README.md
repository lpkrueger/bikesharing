# bikesharing
Module 15, Tableau - UNCCH Data Analytics Bootcamp, Spring 2023

## Project Overview

### Purpose
In this exercise, it was necessary to create a data story to support 
a pitch to investors that launching a bike-sharing program in Des Moines, Iowa would be a viable business proposal, based on analyzing similar bike-sharing trip data from another city.

The analysis required creating a set of visualizations to show:
- The length of time that bikes are checked out
- The number of bike trips for all riders and genders for each hour of each day of the week
- The number of bike trips for each type of user and gender for each day of the week
- Peak hours of the day for bike trips
- Top locations for trip starts and stops


## Method
A .csv file was downloaded from https://citibikenyc.com/system-data which contained bike-sharing trip history data for Citi Bike bicycles during the month of August, 2019. This month was chosed due to its nice weather allowing for high bike traffic. 
Using python in a jupyter notebook environment, the raw data file named "201908_citibike_data.csv" was imported and a dataframe created to convert the "tripduration" field from integer format to datetime format. Then the resulting dataframe was exported to a .csv file named "201908_citibike_data_cleaned.csv"   

The python function employed within jupyter notebook to perform this is as follows, utilizing the pandas and datetime libraries:
[Jupyter Notebook File](NYC_CitiBike_Challenge.ipynb)

A subset of this code can be viewed here: 
```
import pandas as pd
import datetime as dt
citibike_df = pd.read_csv("201908-citibike-tripdata.csv")
citibike_df['tripduration'] = pd.to_datetime(citibike_df['tripduration'], unit='s')
citibike_df.dtypes
citibike_df.to_csv('201908_citibike_data_cleaned.csv', index=False, encoding='utf8')
```

The resulting modified data file was imported into Tableau Public, from which several visualizations and dashboards were created to display a Tableau story. To create visualizations using gender information, a new field was created called "Gender to String" by converting the "Gender" field from an integer to a string. The code used in Tableau to create the "Gender to String" field is as follows:
```
IF [Gender] = 0 then 'UNKNOWN'
ELSEIF [Gender] = 1 then 'MALE'
ELSEIF [Gender] = 2 then 'FEMALE' 
END
```

## Results
The resulting Tableau viz named "NYC Story" depicts all the required metrics.    

- Link to Tableau Story
[Link to Tableau Story](https://public.tableau.com/views/bikesharing_challenge_16800688101830/NYCStory?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link "Link to Tableau Story")

- Observations: 
    - Of the 2.3 million rides in August, 2019 in NYC, over 80% were taken by CitiBike subscribers vs guest customers.
    - On weekdays, the peak times are typical commuting hours ~7-10am and ~5-8pm, with the evening rush hour being the busiest.
    - On weekends, the rides are more evenly spread throuought the day.
    - The most common bike trip duration is 6 minutes long, and very few trips are longer than an hour. 
    - Most trips end very close to their origination point, on a city-wide scale. 
    - More males participate in bike-sharing than females, and males are more likely to be subscribers.
    
## Summary
These data are very informative. Some takeaways for the investory pitch may include:
- Turning customers into subscribers would be optimal, as subscribers generally take 4 times more trips than guest customers in the area studied.  
- Placing bikes in strategic high-use locations can reduce the required number of bikes in the fleet, allowing the business to optimize revenew with a minimum investment bicycles, at least to get started. 
- Trips are generally short duration, and therefore short distances. Therefore, charging customers by the trip would be more lucrative than charging by the mile or by the minute. 

Recommendations for additional supporting visualizations:
- Average trip duration for males and females
- Average trip duration by starting location
- Trip locations by workweeks vs weekends 
- Average age of riders (can be compared with the age demographic of the intended market)   
- Average trip distance by trip duration, mapped by hours of the day
- Correlation between user type and weekday of bike use (i.e. are subscribers more likely to be commuters and take more trips than non-subscribers?)   