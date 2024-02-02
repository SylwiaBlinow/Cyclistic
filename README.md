# Cyclistic : Google Data Analytics Case Study


## A. Introduction 
In this case study, I work for a fictional company, Cyclistic, along with some key team members. In order to answer the business questions, I will follow the steps of the data analysis process: Ask, Prepare, Process, Analyze, Share, and Act.

### I.	Background — About the Company
Cyclistic is a bike-share company in Chicago. In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime
Cyclistic sets itself apart by also offering reclining bikes, hand tricycles, and cargo bikes, making bike-share more inclusive to people with disabilities and riders who can’t use a standard two-wheeled bike. The majority of riders opt for traditional bikes; about 8% of riders use the assistive options. Cyclistic users are more likely to ride for leisure, but about 30% use the bikes to commute to work each day.

### II. Business Task — Marketing Strategy

Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members
Lily Moreno, the marketing director is responsible for the development of campaigns and initiatives to promote the bike-share program. These may include email, social media, and other channels.
Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, Moreno believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, Moreno believes there is a solid opportunity to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.
Moreno has set a clear goal: Design marketing strategies aimed at converting casual riders into annual members.

## B. Methodology 

### I. Ask — Define a Problem to Solve

Moreno and her team are interested in analyzing the Cyclistic historical bike trip data to identify trends and design effective strategies to maximize the number of annual memberships by converting casual riders of Cyclistic into yearly members. 
Three questions will guide the future marketing program: 
1. How do annual members and casual riders use Cyclistic bikes differently? 
2. Why would casual riders buy Cyclistic annual memberships? 
3. How can Cyclistic use digital media to influence casual riders to become members?


###  II. Prepare — What Data do We Need?

I used the previous 12 months of Cyclistic trip data (the data dated from Jan 2023 to Dec 2023) Cyclistic’s historical trip data to analyze and identify trends. This is public data and is located here: https://divvy-tripdata.s3.amazonaws.com/index.html

After downloading the source zip files, the first step is to create a folder with appropriate file names. Each dataset was a CSV (comma-separated values) file. 


**Credibility of Data**
The credibility and integrity of our data can be determined using the ROCCC system and find out if our data is:
-	Reliable -  it has a large sample size
-	Original  - this is the original dataset as collected and made available by Motivate International Inc.
-	Comprehensive - there is information about each ride trip: member status of bike-user, ride date and time, starting location and ending location of trip, duration of bike ride. The data is unbiased and randomised where all other data is not covered: gender, age, race etc.
-	Current - it is relevant and up to date, thus indicating that the source refreshes its data regularly. The data is currently updated monthly. The dataset covered a whole year record in 2023 where this report is drafted in 2024.
-	Cted - the source has been vetted.
The data integrity and credibility are sufficient to provide reliable and comprehensive insights for the team's analysis.


### III. Process — From Dirty Data to Clean

In this process we need to make sure that our organized data is complete and accurate. Clean data is the key to making sure our data has integrity before we analyze it.  Data integrity is the accuracy, completeness, consistency, and trustworthiness of data throughout its lifecycle.
Steps:
1.	I downloaded the previous 12 months of trip data (Jan 2023 to Dec 2023)
2.	I unziped the files.
3.	I created a folder on my  desktop to house the files. I used appropriate file-naming conventions.
4.	I created subfolders for the .csv file and Sheets file so that I have a copy of the original data. I moved the downloaded files to the appropriate subfolder.
5.	I opened spreadsheet and used Power Query to import and clean data 
6.	I  calculated the length of each ride by adding time substraction column (subtracting the column started_at from the column ended_at) 

