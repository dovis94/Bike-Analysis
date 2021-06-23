---
title: "Bike Sharing Data"
author: "Dov Shtauber"
date: "6/22/2021"
output: html_document
---

# Analyzing Bike Sharing Data
## How can we convert casual bikers to members
A bike sharing company in Chicago collected data on their
bikes and their riders.
They would like to use this data to find out the best way to 
change any casual rider to a member.
This conversion would be easier than acquiring completely new customers because we already have data on the casual riders.
*Especially that they ride bikes.*

## Collecting data
Data was retrieved from [Divvy-tripdata](https://divvy-tripdata.s3.amazonaws.com/index.html).
I chose the following metrics out of the dataset for my analysis:
- Rider Type.
- Bike Type (electric, classic, handicap accessible).
- Start and end timestamps.
- Start and end locations.

## Cleaning and Organizing Data
I checked to see if any columns had null - if applicable and corrected it.
I uploaded 12 months of data **June 2020 Until May 2021** 
I then combined all the files together in Bigquery Using the *Union* function
The column types for the first 6 months were different than the second 6, so I converted them all to the same data type

SELECT *, DATE_DIFF(ended_at, started_at, minute) AS Total_Bike_Time,
CAST(started_at AS DATE) AS Date

FROM `ancient-figure-315513.bike_data.dec_2020_may_2021`

I added two new columns "Date" and "Total_Bike_Time"
These two columns will help with the analyzing process
## Analyzing Data
With the organized data, I imported the spreadsheet to tableau 
and wanted to compare overall casual ridership against member ridership and to add another layer of granularity I stacked the bar graphs by day of the week to get an understanding of the impact of the weekend. 
In this case we see that the weekdays are fairly similar however Friday through Sunday we see a sharp increase in casual riders.
I didn't include monday even though there is an increase in ridership because national holidays tend to be on the monday after the weekend so it doens't say much about monday itself.

Average bike time 	
General 18.34
classic 19.94
electric 16.81
member 13.90
casual 25.95
[bike data](https://drive.google.com/file/d/1bv1t_CW0l1OEjYjHgqSMFdqclXaiKD7v/view?usp=sharing)


