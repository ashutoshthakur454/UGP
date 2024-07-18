<h1 align="center">Welcome to Smart Disaster Relief Management System 👋</h1>
<p>
  <a href="https://docs.google.com/document/d/1zWyqm6A7PqCI_S7ovto-2Em5ri1TkWkbWDy4fC_ikSU/edit?usp=sharing" target="_blank">
    <img alt="Documentation" src="https://img.shields.io/badge/documentation-yes-brightgreen.svg" />
  </a>
</p>

> Allocation of various relief supplies in the flood hit areas of Assam using data obtained by IMD, DFO and EM-DAT

# Missing Data

Initially we had lot of missing data which we had to extract from the extent and description column given in our dataset of Indian Flood Inventory. We used various techniques to fulfill this data to get more insight of the floods' impact in Assam.

<img width="613" alt="Screenshot 2024-07-08 at 1 07 44 PM" src="https://github.com/aryanparihar2910/UGP/assets/116455750/605bee4f-0866-4fd9-984b-c660f7bbdba7">
<img width="649" alt="Screenshot 2024-07-08 at 1 09 47 PM" src="https://github.com/aryanparihar2910/UGP/assets/116455750/d903be3e-a444-42fa-bc8e-0ee1593e7c12">

We used various methods to extract information from the extent and description column to fill in as many missing values as possible.


# Focus on Assam

We chose Assam as our region of study as it had the highest occurence of flood among all states.

<img width="529" alt="Screenshot 2024-07-08 at 1 11 21 PM" src="https://github.com/aryanparihar2910/UGP/assets/116455750/e8f7f758-4cf2-490c-88ee-a30a1e4657ec">

<img width="613" alt="Screenshot 2024-07-08 at 1 04 35 PM" src="https://github.com/aryanparihar2910/UGP/assets/116455750/59bf098b-42ef-4d08-8eeb-0c43caea338f">

This was the heat map of flood occurences in the Assam and its nearby region of India.

# Correlating the Fields

This was the correlation matrix plotted between all available columns of the dataset.

<img width="658" alt="Screenshot 2024-07-08 at 1 12 45 PM" src="https://github.com/aryanparihar2910/UGP/assets/116455750/32322996-2022-4b63-8452-84ba9f36a2e8">

# Modelling

Using various techniques like Linear Regression, Ridge Regression alongwith a KNN imputer to address the missing values, we got pretty decent results in predicting human displaced from the related factors.

<img width="670" alt="Screenshot 2024-07-08 at 9 14 45 PM" src="https://github.com/aryanparihar2910/UGP/assets/116455750/dd6bc6d3-661b-450a-82a4-074e2f158216">

<img width="658" alt="Screenshot 2024-07-08 at 9 14 14 PM" src="https://github.com/aryanparihar2910/UGP/assets/116455750/4930468a-69ba-4307-b185-783a84ec0ae1">

We plotted various heat maps to visually show how the impact of floods were spread across the state of Assam and its nearby region.

<img width="670" alt="Screenshot 2024-07-08 at 9 20 31 PM" src="https://github.com/aryanparihar2910/UGP/assets/116455750/e8e32e15-a068-48b1-9a16-16bfdb667194">

<img width="670" alt="Screenshot 2024-07-08 at 9 20 54 PM" src="https://github.com/aryanparihar2910/UGP/assets/116455750/3c9de5eb-8392-4386-b462-144b15e6c06e">


# Results

After performing K-means clustering with K values ranging from 1 to 11 and observing the "elbow" point at K=6, the dataset was clustered into six distinct groups. These clusters represent areas with similar population density and spatial characteristics within Assam.

<img width="670" alt="Screenshot 2024-07-08 at 9 24 04 PM" src="https://github.com/aryanparihar2910/UGP/assets/116455750/d1a7c9be-5ce0-4781-81e8-a15c71b6f554">

<img width="552" alt="Screenshot 2024-07-08 at 9 24 36 PM" src="https://github.com/aryanparihar2910/UGP/assets/116455750/c1396d74-3a6d-44cb-80af-1195fb16c4c0">


In the context of disaster response planning in Assam, the Voronoi diagram delineates the boundaries of influence for each cluster centroid, effectively partitioning the geographical area into regions that are closest to each respective centroid.

<img width="643" alt="Screenshot 2024-07-08 at 9 24 58 PM" src="https://github.com/aryanparihar2910/UGP/assets/116455750/75716276-d94a-4f8a-8a83-2476cac7dbad">



