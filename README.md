<h1 align="center">Bike Sharing Case Study</h1> 

## INTRODUCTION

>Hi everyone, over the last few months, I've been working on a bike sharing case study . This has been a very insightful case study that has included Tableau, python programming, SQL and key data analyst terminologies and processes. Below is my walkthrough of Case Study using various tools and methods.
Scenario: You are a data analyst working at Cyclistic, a bike-share company in Chicago. 

>Cyclistic allows people to pick up bikes and dock them at various stations. Riders who have an annual subscription are called members while riders who are single-ride or full-day pass users are considered casual riders.

>The director of marketing is looking to maximise the number of annual memberships as they are more profitable than single-ride or full-day passes. This strategy is believed to be the key to future growth.

>Management believes that the best approach to do this is through converting casual riders into members as casual riders are already customers and aware of Cyclistic's services. 

>Ask/Business Task: To understand the differences in bike usage among casual and member users in order to recommend how to encourage casual riders to become members.

## Prepare/Understanding the Dataset

I will be using the public dataset located above. The data has been made available by Motivate International Inc.. This is a public dataset therefore, there is no personal data and no way to know how often the same rider uses the biking service.

Across the various tables, the column names varied slightly however the key columns within the 2020-2021 dataset which are worth noting are the start and end stations, start and end ride times as well as the member and casual rider columns. The station latitude and longitude columns were also useful for data visualisation.

Process

I tried processing this data in both BigQuery and Python but for storage reasons, Python was a better fit.

I started by creating a data cleaning rundown script. Among other things I:

Removed duplicate records with the use of unique ride ids using drop_duplicates() in pandas
Deleted rows with incomplete or unavailable data with dropna() functionality in pandas
Deleted rows with inconsistent times where the start time was later than the end time
Added a column for the duration of the trip in minutes and a column for the starting hour e.g. If the ride start time was ‘2020-07-22 15:38:23’ the starting hour would be 15
Added 2 weekday columns for the respective weekdays the ride started and ended on
My main challenges were working with the date format, although I only created visualisations for 2020 - 2021, I cleaned all the tables going back to 2016. They had various date formats and I found working with dates to be the most challenging part of this case study as certain functions turned dates into string or number formats which were then not readable as dates in Tableau. In the end, I figured out how to use the 'as.POSIXct' and 'as.Date' functions to create the right column format and add a weekday column.
