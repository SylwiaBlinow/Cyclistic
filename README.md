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
* Reliable -  it has a large sample size
* Original  - this is the original dataset as collected and made available by Motivate International Inc.
* Comprehensive - there is information about each ride trip: member status of bike-user, ride date and time, starting location and ending location of trip, duration of bike ride. The data is unbiased and randomised where all other data is not covered: gender, age, race etc.
* Current - it is relevant and up to date, thus indicating that the source refreshes its data regularly. The data is currently updated monthly. The dataset covered a whole year record in 2023 where this report is drafted in 2024.
-	Cited - the source has been vetted.
The data integrity and credibility are sufficient to provide reliable and comprehensive insights for the team's analysis.


### III. Process — From Dirty Data to Clean

In this process we need to make sure that our organized data is complete and accurate. Clean data is the key to making sure our data has integrity before we analyze it.  Data integrity is the accuracy, completeness, consistency, and trustworthiness of data throughout its lifecycle. 
The process of data cleaning involves identifying errors in a dataset and then fixing or removing it. Data errors may include incorrect, duplicate, or incomplete data.

In processing data I used EXCEL - POWER QUERY, SQL AND R language. Power Query will help me to compare my results in SQL and find any mistakes in analysing data. 

### $${\color{blue}POWER \space QUERY}$$ 

Steps:
1.	I downloaded the previous 12 months of trip data (Jan 2023 to Dec 2023)
2.	I unziped the files.
3.	I created a folder on my  desktop to house the files. I used appropriate file-naming conventions.
4.	I created subfolders for the .csv file and Sheets file so that I have a copy of the original data. I moved the downloaded files to the appropriate subfolder.
5.	I opened spreadsheet and used Power Query to import, merge and clean data

![Picture3](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/5a4a83f9-83d5-44c7-a294-c87070850ca6)
   
6.	I counted rows and the results was: 5 719 877 rows
   
![Picture01](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/4cfc71a7-e92a-45b2-a98c-c246e2be2e3f)

7.	I  calculated the length of each ride by adding time substraction column (subtracting the column started_at from the column ended_at)


![Picture1](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/74acd67b-7344-4414-b4ed-911bb11f4e53)

8.	I calculated the day of the week that each ride started by adding another column called day_of_week, where 0= Monday and 6=Sunday. Also I added day name and month name

   
![Picture2](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/c6e95f29-659d-4318-83ba-0a08c7532be5)

9.	I removed empty cells in columns: [start_station_name], [start_station_id], [end_station_name], [end_station_id], [start_lat], [start_lng], [end_lat], [end_lng]

10.	I separated hours of starting the trip



![Picture6](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/8c09ce81-8cc3-4708-a6f3-ed3f7ad1419a)

11.	I unfiltered trips with ride_lenghth lower than 2 minutes. The number of rows I had is 4 166 574 

![Picture7](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/7bd42bd2-efa7-4777-a740-de91e98e745e)

![Picture9](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/c61e8397-0cc4-43c9-9b8f-7a5582ab7e38)


### $${\color{blue}SQL}$$ 

### _COMBINE_
https://github.com/SylwiaBlinow/Cyclistic/blob/main/1.Combine_SQL

1.	I created a dataset named Cycalitic_Trips in BigQuery and uploaded all 12 CSV files. 
2.	I encountered an issue with 6 of the files, as their size exceeded the 100 MB limit for uploading to BigQuery. 
3.	To resolve this, I split each of these files into two smaller files. 
4.	I merged all the tables into a single table named cycalitics_trips_all_2023.
5.	I saved outcome as a dataset table Cycalitics_Trips_ALL_2023

### _EXPLORE_
https://github.com/SylwiaBlinow/Cyclistic/blob/main/2.Explore

1. I have counted rows and the results was: 5 719 877 rows (the same as was in Power Query)
   
![Picture11](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/9e0aaa54-8120-4a8a-9cb5-5ceaa5156931)

2.	I checked number of null values in all columns

![Picture10](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/3397906c-b041-48c6-a5e1-02555c68934a)


3.	I checked whether there are duplicate data after the ride_id - there were none
   

![Picture12](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/d01bc1d6-ed26-4899-9095-b2abbd7bd5a9)

4.	I looked at the bike types (rideable_type) and user type (member_casual) to check for distinct values, spelling errors, and trailing or leading space. No inconsistency  was detected

![Picture15](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/77e2160a-e41d-4f49-b830-675190e92fa5)

![Picture16](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/e16e7738-f3ed-47fb-869f-e0f21d34fdc9)

### _CLEAN_
https://github.com/SylwiaBlinow/Cyclistic/blob/main/3.Clean%20data%20in%20SQL

1.	I removed null rows

2.	I counted again number of row and the results was: 4 331 707 so 1 388 170 null rows were removed (I checked that the same as was in Power Query)

![Picture13](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/9f59635c-f20c-4c06-b6cb-35140350699c)

3.	I made new table and added 3 more columns: ride_length for duration of the trip, day_of_week and month.

![Picture19](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/b59eac45-bf91-4945-96e3-8cc1f4a4915c)

4.	I unfiltered trips with ride_lenghth lower than 2 minutes because are potentially test rides. In addition it helps to remove potentially negative ride length
   
5.	I checked again number of row and the results was 4 166 574 as well as in Power Query


![Picture20](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/fb2ea0dc-a8c2-4077-a686-43538b2271c4)

### IV. Analyze — Find the Patterns

Now that our data looks clean, I am ready to analyze data and find patterns, connections, insights, and predictions.

https://github.com/SylwiaBlinow/Cyclistic/blob/main/4.Analyze

1. I started by calculating the total rides for members and casual riders and total rides for users and bike types. 

![Picture18](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/6a7dfc1c-8ea7-4679-a1a0-9162c877d90e)

![Picture17](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/74faa957-44aa-48c0-851b-9b55c839fc96)

   
2. I checked number of trips:
* per month:

![month](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/fc010ea4-0699-4be6-b8a0-c8b0806c5131)

![month2](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/d802ac0c-cf54-49b8-820a-ee7090c7ad35)

* per day 
 
 ![week](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/3ac5234c-7ae1-4d5c-9478-8eb2c60e413f)  

 * and per hour 

 ![HOUR](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/71f4b7b9-d5e3-4fcb-974e-d6481cb3e4c1)
 
 ![HOUR2](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/8faa0335-49d7-4d92-80f8-f3825bf570a5)
 
![HOUR3](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/120d7c0b-e16c-44e1-92d5-b0cf893d9cd2)

![HOUR4](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/c3628086-f21b-4554-9518-65314b490d05)

3. I calculated an average ride duration in minutes:

![avg](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/5a631730-6a42-46ed-8562-6bf0cef348a6)

![avg1](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/4ad05d96-34a7-4343-8a37-794a0d8a7ba0)

![avg2](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/bcfa11d2-d783-46f7-ace2-e169731aedd6)

3. Lastly, I calculated the number of rides per start and end stations for users to see which stations they prefer. 

![Picture21](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/3936b79b-bf89-4f23-b305-67d76a4ce6ed)

![Picture22](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/6d17225d-0206-4d2f-b04a-9a8552930e6a)

### V. SHARE - Visualizing Insights

#### Total Trips Taken

Users of Cyclistic bike-share services categorize into two types: Cyclistic members and Casual riders. The pie chart below shows the total number of trips each kind of user took from January 2023 to December 2023

![Picture10](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/b27a66d9-57b3-4a02-b669-f7f39e7be054)

![Picture11](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/7ee2b2c4-4eb4-4190-9e5b-f826ea74068e)


*	Cyclistic members have recorded an overall higher activity with approximately 2.7 million trips. That is 64,29% of the total trips taken.
  
*	Casual riders, however, have recorded their activity with approximately 1.5 million trips. That is 35,71% of the total trips taken.

#### Types of Bicycles Used

Cyclistic has a variety of different bicycles. They can be categorized as classic, docked, and electric. The bar chart below shows the total number of trips each user took on the three different types of bicycles from January 2023 to December 2023

![Picture12](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/873e50b1-0157-4df4-aba7-a8158efcae68)

*	Cyclistic members prefer the classic bicycle to the electric one — of the total trips taken in one year, 1.75 million have been on a classic bicycle. That is 42,01% of the total trips taken. 0.93 million trips were on electric bicycles. That is 22,28% of the total trips taken and this outcome is not much bigger than classic bikes
*	Casual riders have also shown a higher preference for classic bicycles — of the total trips taken in one year, 0.85 million have been on a classic bicycle. That is 20,43% of the total trips taken. On the other hand, only 0.56 million trips were on electric bicycles. That is 13,47% of the total trips taken.
*	Casual riders have also used the docked bicycles, with 0.08 million trips taken. That is 1,80% of the total trips taken.

#### Trips Taken in a Year

With a total of 4.166.574  rides in a year, knowing which months had the most user activity is essential to identifying Cyclistic's target demographics. The bar chart below shows the total number of trips each user took in 12 months, from January 2023 to December 2023.

![Picture13](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/4ff7399f-bc91-49ae-9260-35e6f28c249b)

* Cyclistic members recorded their highest activity in August 2023, with 337 830 trips at 8.11%, and the lowest in February 2023, with 142 230,00 trips at 2.65%.
* Casual riders recorded their highest activity in July 2023, with 238 156 trips at 5.72%, and the lowest in January 2023, with 28 564 trips at 0.69%.
* From May to August, Cyclistic members recorded a higher user activity at 29.52% compared to casual riders, who had a user activity of 20.42%.

#### Trips Taken in a Week

![Picture14](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/cdd999fd-3cf0-48eb-b442-2c79dfbb7fb4)


*	The casual users ride more on the weekends(Saturday & Sunday), while the member users rides mostly on the weekdays(Monday-Friday)

![Picture15](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/12459f1e-a908-4367-9484-a8ee2a9976a7)

*	The weekdays (Monday -Friday) had more rides compared to weekends in general

 ![Picture16](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/4f23f6b4-ba81-4612-91b7-5a1c4d65afd5)

* The average ride length is 16 minutes. Weekends have the longest ride length, while the weekdays have shorter ride length

#### Mean Trip Duration Across the Year

Now that we know when user activity is highest or lowest, we can complement it with insights regarding duration of each trip. For example, the bar chart below shows each user's mean trip duration traveled in 12 months, from January 2023 to December 2023

![Picture17](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/bfd22422-c9a1-4ca3-8d28-e7cbc10fe344)

![Picture18](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/39b93bdd-c50f-4a93-a4fc-4562d4b49d13)

* The average ride length is had casual users longer than members but members had more number of trips taken during year.


#### Number of trips during the Day

![Picture19](https://github.com/SylwiaBlinow/Cyclistic/assets/156024627/88707b4d-2626-4c13-9118-c305a19d41f8)

The peak of using the bikes is at 8 am and at 5 pm by member users. Probably it is made by people commute to work. 


### Recommendations

We can conclude that member users and casual users are quite different group of people:
* casual users use bike for casual reasons such as sightseeing or leisure. They have peak season of summertime, peak usage on weekend and off-rush hour and spend more time on bike. 
* member users use bike at commuting hours in commercial areas with heavy traffic. They use bike more often but for short time.

To convert casual riders into annual members, the following marketing strategies can be implemented:
* online advertising with app benefits for memebrs
* social media marketing showing users and they trips 
* customer referral marketing with discounts
* offering loyalty programs especially during summertime and weekends
* organizing sightseeing events for members
