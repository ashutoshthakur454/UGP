# Resource Allocation During Natural Disaster

## Aim of the project:
1) Analyze the IMD data and focus onto frequent flood hit areas
2) Predicting the number of human casualties 
3) Estimating the distribution of displaced humans and thereby proposing warehouse locations

**Dataset** : The India Flood Inventory, a geospatial dataset developed in collaboration with the Indian Meteorological Department (IMD). This dataset provides valuable information on floods in India, including fatalities, damage, and other relevant parameters. However there is a lot of missing data that needs to be addressed before further analysis.

Glimpse of the columns present along with their Non - Null count, Data types and %age of missing values.

![image](https://github.com/user-attachments/assets/c8e6263d-4001-4c65-96db-ec5350ae7a6b)

These columns : Location, Latitude , Longitude, Severity,Area affected, Human injured, Human displaced, Animal fatality and event source have most of the data missing (more than 80%)

## Data Cleaning and Pre processing:

1) Created Start month, Start year from start date, End month and end year from end date. Then dropped start date and end date columns. There were also instances when the start date was later than the end date in the dataset (~3%) so dropped the corresponding rows.<br><br>

2) Main cause column was treated with string conversion to lowercase, stripping off the whitespaces. On seeing the entries there are a couple of problems that need to be addressed in this column<br>
   a) Entries such as 'flood' and 'floods', 'heavy rain' and 'heavy rains' are nothing but the same thing.There are a lot of entries with this problem.<br>
   b) Apart from the most occuring data like heavy rain and flood, there are many other entries which occur only once and are in the form of a long string.<br>
Thus further preprocessing steps were taken which included punctuation removal + word lemmatization.  I took the first 14 unique values into consideration and replaced others with 'other'.<br><br>

 3) We needed to extract the latitude and longitude of the places in order to do the geospatial analysis. Upon going through the data present in these columns, these observations can be made:<br>
    a) The essential data (i.e. data in latitude and longitude columns) is very less. We need to convert the district and state data into coordinates.<br>
    b) First we will consider the dataframe where these latitudes and longitudes are null and the columns will be district, state and location<br>
    c) On seeing the data, there are 410 rows where district data is null and 356 rows where state data is null. Actually state data is always present when district data is present and apart from that 54 rows contain only state information<br>
    d) For the rest rows which contain neither coordinates nor district-state information we have data present in Location column<br>
We will be geocoding the data present in df_geo dataframe. It is nothing but converting an address to a location on map.

![image](https://github.com/user-attachments/assets/39fb627e-7be6-4e90-b8d2-c33316a282f7)

After we fetched the coordinates here are some plots which we created just to visualize the flood locations on a sample of 500 points.
![image](https://github.com/user-attachments/assets/48132727-c0cc-4094-8493-df09ad6440c6)

![image](https://github.com/user-attachments/assets/d0e9dc33-8dad-49a7-a90b-c6974ca4ef72)

So now from the sample maps it could be seen that the north eastern and the southern parts of India are most affected from floods, we can also do a region specific geospatial analysis.
Taking a window 

![image](https://github.com/user-attachments/assets/85da1d1d-5048-4c68-811e-af997d28a6d8)


![image](https://github.com/user-attachments/assets/904b342a-0ea1-4b6f-a77a-f34f1674fb8a)

4) Severity, Area Affected, Human fatality, Human injured, Human Displaced, Animal Fatality, Description of Casualties/injured, Extent of damage :

	The EM_DAT event source has no information regarding the extent of the floods, so we will drop the corresponding rows. We will also take a range of coordinates to further narrow down our research to areas where most of the floods occur. As evident from the marker cluster map, we will take the north eastern part into consideration.


![image](https://github.com/user-attachments/assets/0061a4e8-a132-4c14-9d80-a356a4bf08c1)

DFO source contains complete information about Severity, Area affected , Human fatality and Human Displaced whereas IMD source contains some information about Human fatality, Human injured, animal fatality, description and extent.


![image](https://github.com/user-attachments/assets/5f27eafd-ac29-41a2-9973-8e35b70ed26e)

## Data Visualization


![image](https://github.com/user-attachments/assets/85e91608-522f-4b61-af9f-2c34f647684e)


![image](https://github.com/user-attachments/assets/6d4bb058-ea27-492b-8f41-d98f3a64032c)


![image](https://github.com/user-attachments/assets/648092a2-b325-4109-9275-8626aa07ff71)


![image](https://github.com/user-attachments/assets/045d11e8-c85f-4e15-803e-ad67e38204f4)


![image](https://github.com/user-attachments/assets/ccd044e1-4510-45a7-aa88-183bbc15c0ea)


![image](https://github.com/user-attachments/assets/d1051e0e-151a-4d46-bbda-f7418a62233e)


![image](https://github.com/user-attachments/assets/a26d8261-ca26-45ea-bdeb-34441f2e8fb8)


![image](https://github.com/user-attachments/assets/45136fea-1fe9-4491-84cc-4af9c60b55b2)

## Predictive Modelling


![image](https://github.com/user-attachments/assets/3518d961-6f7a-4462-b8ae-6678be9faa78)

Predicted Human Fatality with R² 0.55 after feature selection, using Artificial Neural Networks. 


![image](https://github.com/user-attachments/assets/07707cbf-570d-40a3-8b0f-39846aaf0838) ![image](https://github.com/user-attachments/assets/84001c88-ce3a-4be3-a06d-13f46dbdd475)

Now estimating humans displaced. Used KNNimputer to fill in the missing values. Achieved R² score of 0.58 using Linear Regression.<br>

We plotted various heat maps to visually show how the impact of floods were spread across the state of Assam and its nearby region.


![image](https://github.com/user-attachments/assets/f7a245ea-f6a2-4f58-9ed9-2695847638b0)


![image](https://github.com/user-attachments/assets/6da0f3fe-d303-4503-a1eb-70198625c654)


![image](https://github.com/user-attachments/assets/88fca873-9fcc-41dc-bfe4-3a96522c8f1d)

## Warehouse Allocation

Now in order to determine the distribution of displaced people we assumed the distribution to be in accordance with the census population report. Since the last detailed census occurred in 2011 (Couldn't happen in 2021 due to covid), we had the following heatmap of assam population: 


![image](https://github.com/user-attachments/assets/82117d2b-c55d-4e8e-ab32-9adbde5f2ba4)

Each warehouse will correspond to one cluster. Location of warehouse will be equivalent to cluster center so as to reduce the within cluster sum of squares or the L2 distance between cluster center and other points. 


![image](https://github.com/user-attachments/assets/e4547ca4-0599-4f32-a8d4-b95c2df607d5)

We further boiled down to Kamrup district of Assam. This was done due to 2 main reasons : (i) More number of town population information was present in Kamrup District as of census 2011 compared to other districts. (ii) Tailoring to one district will give a more detailed solution of this problem as it will be meaningless for a state to have 5-6 warehouses. 


![image](https://github.com/user-attachments/assets/5b51e4a5-efcc-42c2-b1b5-4fe4d91b938d)


![image](https://github.com/user-attachments/assets/b4d9e3da-b86b-48a5-be7a-7c457759c38a)

In the context of disaster response planning in Assam, the Voronoi diagram delineates the boundaries of influence for each cluster centroid, effectively partitioning the geographical area into regions that are closest to each respective centroid.

![image](https://github.com/user-attachments/assets/513871fc-101d-410f-ba03-e60dddc7df73)

