<h1 align="center">Bike Sharing Case Study</h1> 

## INTRODUCTION

>Hi everyone, over the last few months, I've been working on a bike sharing case study . This has been a very insightful case study that has included Tableau, python programming, SQL and key data analyst terminologies and processes. Below is my walkthrough of Case Study using various tools and methods.
>Scenario: You are a data analyst working at Cyclistic, a bike-share company in Chicago. 

>Cyclistic allows people to pick up bikes and dock them at various stations. Riders who have an annual subscription are called members while riders who are single-ride or full-day pass users are considered casual riders.The director of marketing is looking to maximise the number of annual memberships as they are more profitable than single-ride or full-day passes. This strategy is believed to be the key to future growth.Management believes that the best approach to do this is through converting casual riders into members as casual riders are already customers and aware of Cyclistic's services. 

>Ask/Business Task: To understand the differences in bike usage among casual and member users in order to recommend how to encourage casual riders to become members.

## Prepare/Understanding the Dataset

I will be using the public dataset located above. The data has been made available by Motivate International Inc.. This is a public dataset therefore, there is no personal data and no way to know how often the same rider uses the biking service.

Across the various tables, the column names varied slightly however the key columns within the 2020-2021 dataset which are worth noting are the start and end stations, start and end ride times as well as the member and casual rider columns. The station latitude and longitude columns were also useful for data visualisation.

Process

I tried processing this data in both BigQuery and Python but for storage reasons, Python was a better fit.

I started by creating a data cleaning rundown script. Among other things I:

1. Removed duplicate records with the use of unique ride ids using drop_duplicates() in pandas
2. Deleted rows with incomplete or unavailable data with dropna() functionality in pandas
3. Deleted rows with inconsistent times where the start time was later than the end time
4. Added a column for the ride length of the trip in minutes and a column for the starting hour e.g. If the ride start time was ‘2020-07-22 15:38:23’ the starting hour would be 15
5. Added 2 weekday columns for the respective weekdays the ride started and ended on using dt.weekday() in pandas
6. My main challenges were working with the date format, although I only created visualisations for 2020 - 2021, I cleaned all the tables going back to    2016. They had various date formats and I found working with dates to be the most challenging part of this case study as certain functions turned dates into string or number formats which were then not readable as dates in Python. In the end, I figured out how to use libraries such as time and functionalities such as gmtime and strftime also datetime function in pandas to create the right column format and add a weekday column.
## Below is a summary of the data after the initial data processing:
<img width="814" alt="photo after initial data processing" src="https://user-images.githubusercontent.com/124433494/216765462-8ee7e790-cbdd-46ac-8a43-6b040e7abf34.png">
<img width="814" alt="photo after initial data processing 2" src="https://user-images.githubusercontent.com/124433494/216765538-dab609b8-19e4-4833-8011-680ec2e13d4e.png">
#comments include mean median mode data also in the above picture
#to be included box plot
#look at image 2 comments also

## [Image 3]

## Data Visualisation

I used Tableau and matplotlib.pyplot  in python  for data visualisation, below are my key findings.

##Daily Use

The key difference in usage, shown below, is that casual riders use bikes most on weekends and least at the beginning of the week, whereas members use the bikes more evenly across the week. Members also use classic and electric bikes more often throughout the week whereas casual riders mostly use docked bikes.Here 0 in the chart being monday and so on
<img width="1425" alt="daily plot for casual members" src="https://user-images.githubusercontent.com/124433494/216783338-d6db7478-5914-444d-b1d1-62d5823f4719.png">
#daily plot for member is remaining

##[Image 4]

##Hourly Use

Throughout the week, members and casual riders use the bikes most often around 5/6 pm on weekdays and 1/2 pm during the weekends. Casual riders begin trips fairly frequently in the early afternoons on weekdays while members start journeys quite often around 7/8 am on weekdays.I also will be adding individual photos in a seperate folder
#ask shreyas how to do that
![hourly plots combined](https://user-images.githubusercontent.com/124433494/216784374-a5f4a5cf-4ff0-49bf-9df5-fb486144d3d1.png)

##[Image 5]

Monthly Use

Overall bikes are used most often and for longer periods from march to june, casual riders use the service particularly more during Saturdays in May. As expected there are fewer users in the winter months. It is also interesting to note that casual riders use the service a fair amount between july  and october with a slight dip in november. Electric bikes are fairly popular during spring for causal riders 

![monthly plots according to bike](https://user-images.githubusercontent.com/124433494/216785120-058b1620-f4cb-4d30-8ce9-907abbf44881.png)
#comments image 6 remaining

[Image 7]

Trip Duration

The graph below confirms the finding I noticed earlier in the processing stage. Here we can see that casual riders have longer ride journeys across the whole year.

<img width="1097" alt="line graph" src="https://user-images.githubusercontent.com/124433494/217450246-47dd8e62-77e0-424b-ae4a-322c28d9b84c.png">






