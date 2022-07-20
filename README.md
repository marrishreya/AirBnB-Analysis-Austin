# Airbnb-Analysis
This is an analysis of different AirBnB listings of Austin, Texas, USA. It focuses on few objectives and corresponding procedures to achieve the results.
The ` listings.csv ` file contains information of different rooms/hotels/houses that are enlisted on Airbnb of Austin. The `neighbourhoods.geojson` file contains the geographical information about different neighborhoods in Austin.
The platform used is Google Collab to perform various tasks.
## Background 
### Installing 
I installed `folium` and `geopandas` using the following code:
```
!pip install folium
!pip install geopandas
```
### Libraries 
I have imported the following libraries:
` numpy `,`pandas`,`geopandas`,`seaborn`,`Point` from `shapely.geometry` and `matplotlib`.
### Clonning and Loading
I have clonned my github repository and then loaded it to the platform.
```
!git clone https://github.com/makam2901/Airbnb-Analysis.git
%cd Airbnb-Analysis
```
## Task 1
This task was to find the areas with highest number of listings and plot their corresponding neighborhoods.
### Approach
- I first found all the listings which had maximum `calculated_host_listings_count` which was `358`.
- I then used the `latitute` and `longitutde` columns to treat each listing obtainied as a pointer and plotted accordingly.
- I higlighted the corresponding neighborhoods these pointers reside in and plotted them using `geopandas`.

### Results
The following map highlights the neighborhoods/areas with highest number of listings along with the pointers. 
![](https://github.com/makam2901/AirBnB-Analytics/blob/master/Areas_with_highest_listings.png)

## Task 2
This task was to plot a Thematic map of the neighborhoods broken down by private room, entire home.
### Approach
- I first grouped the original data frame by neighbourhood and counted the number of entire homes/apts and private rooms seperately and saved it in a new data frame.
- With the help of neighbourhood `MULTIPOLYGON` data and corresponding room count, I have plotted the thematic maps for both entire homes/apts and private rooms.

### Results
- This is Thematic map showing the number of entire homes/apts availabe in the corresponding neighborhoods.
![](https://github.com/makam2901/AirBnB-Analytics/blob/master/Thematic_Entire_home.png)
- This is Thematic map showing the number of private rooms availabe in the corresponding neighborhoods.
![](https://github.com/makam2901/AirBnB-Analytics/blob/master/Thematic_Private_Room.png)

## Task 3
This task was just to find the top 10 hosts based on their total `calculate_host_listings_count`.
### Approach 
- I first grouped the whole data by `['host_id', 'host_name']` to obtain unique hosts.
- I carried out the aggregate function `sum` to calculate total host listings count.
- And then finally I sorted the table in descending order of their total host listings count and sliced the first 10.
### Results
The following data frame tell us about the top 10 hosts.
![](https://github.com/makam2901/AirBnB-Analytics/blob/master/Top10_hosts.png)

## Task 4
This task was to find neighborhoods which has entire home/apt and private room at economical prices.
### Approach
- A new column is introduced `minimum_price_for_stay` which is essentially the product of price per night and minimum number of nights required to stay.
- I then grouped the data frame by `neighbourhood` and computed the sum of `minimum_price_for_stay` for each neighbourhood.
- It is observed that the histogram of `minimum_price_for_stay` vs `neighbourhood` is left skewed. Hence, the appropriate metric for deciding the economical price is the median.
- Plotted the neighborhoods near the median for both entire homes/apts and private rooms respectively.
### Results

![](https://github.com/makam2901/AirBnB-Analytics/blob/master/Economical_Neighborhoods_Entire_Home.png)

![](https://github.com/makam2901/AirBnB-Analytics/blob/master/Economical_Neighborhoods_Private_Room.png)
