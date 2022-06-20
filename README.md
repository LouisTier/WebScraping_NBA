# WebScraping_NBA

## **1. About this project**

Everything is explained in the pdf file named "ProjectReport". However, as it is written in French, this README file will explain the main points in English. Let's start with a brief presentation of the different files:

  - Our French report delivered as part of this school project: **ProjectReport.pdf**
  - Our script for web scraping : **WebScraping.ipynb**
  - The content obtained as a table with the csv file: **NBA_data_csv.csv**
  - This same content implemented in a SQL technology to have a _real_ DB: **nbastats_database_sqlite**

This project was done in a school context with two other classmates. The scope and the subject were free. We have a real interest in sports and especially in the NBA. Moreover, we saw that the data was free of acquisition hence this topic.

## **2.Origins and interests for the project**

Basketball, invented by James Naismith in 1891, is rapidly becoming more and more popular in North America. In 1949, the National Basketball Association (NBA) was born, which today is one of the four major leagues in American sports.  
Seeing the astronomical salaries of many players, we asked ourselves for the data collection and storage project:

**To what extent does the sports performance of the players affect their salary?**

Unfortunately, as a result of the health crisis, the seasons were disrupted, so we had to **revert to a so-called "regular" year**. Therefore, we will be looking at the regular season for the **2018-2019 year**.  

The data related to the NBA are **freely available** and can be found on many websites. The objective of this project is to **predict the salary of an NBA player according to his performance** during the season. Thus, a marketing manager within a team can try to **maximize the earnings and profitability of player exchanges during each new season**.  
At the same time, this would allow for example to **adjust the salaries** of new players who have a dazzling first season, who are called *Rookies* and whose "market" value can explode during the season. At the same time, it allows us to check the value of former world-famous players, who are called *Stars* and whose performances can drop from one season to the next.


## **3. Our design of experiments**

We seek to **validate the following hypothesis**: 
**"Good performances during a season increase the value of the player's salary "**.

To test such a hypothesis, here are the different features of our design: 
  - Our study **population**: NBA players  
  - The **sample** taken: The 530 NBA players of the 2018-2019
  - Our **input characteristics**: 
     - Player's name (as index) 
     - Number of games played games played
     - Win ratio
     - Field goal percentage
     - Free throw ratio
     - Number of rebounds
     - Number of assists,
     - Number of steal
     - Number of blocks 
     - Number of points  
 
  _**Please note**: all of these statistics are averaged per game._
  - Our **output** answer: Annual salary in dollars ($)

In the context of our study, we decided to **remove certain characteristics** that we did not consider relevant or representative of the salary, namely:
  - Player ID
  - Team ID
  - The abbreviation of the team name
  - Age
  - The 3-point shot success ratio (since this statistic is included in the ratio of successful shots)
  - Number of turnovers
  - The number of personal fouls

Our study remains *relatively simplistic* and does not take into account many elements such as:

- **The temporality**: We focus only on one season while the salary also depends on the salary of the previous years, the status (new player or not) as well as the performances realized the previous seasons as well as the performances out of regular season.

- **Publicity and media coverage** around the players since the salary also depends on the way the player is represented through the media, his brand image, his sponsors. To evaluate such a rating, we could have been interested in the number of followers on Instagram for example.

## **4. Data collection**

To collect this data, we used the principle of **web scraping**.

1. For the player statistics, we used the following site :

https://www.nba.com/stats/players/traditional/?sort=PTS&dir=-1&Season=2018-19&SeasonType=Regular%20Season 

![image](https://user-images.githubusercontent.com/105392989/174577514-17d020de-5935-4184-87b9-69d6e087ebe2.png)


2. For the salaries we used this website: 

https://hoopshype.com/salaries/players/2018-2019/

![image](https://user-images.githubusercontent.com/105392989/174577635-42585619-7848-463e-8847-33b27514c336.png)

Small precision: We decided to use the salaries that have *not been adjusted for inflation*. These are the salaries in the red box.

## **5. Data storage**

Once we had access to all of our data following the harvest, the question of storage followed.   
**In our case, we first exported the data in CSV** format in order to verify that the table created was in accordance with our dataframe and with our expectations.  
Here is the resulting excel:

![image](https://user-images.githubusercontent.com/105392989/174578412-764a74fa-22ae-486c-b428-44fc80ecc1a0.png)

In order to meet the requirements, we also opted for the **relational database management system** known as **SQLite** in order to create a real database and not a simple table unlike CSV. Indeed, in the case of our project, we have **little data** and **not confidential**, so SQLite will be able to amply support this load.  

We could also have used **MySQL** which allows us to have a **protected database** as well as **more flexible data types unlike SQLite** which is a little more restricted.   
However, SQLite allows you to **store all the information in a file**, which which makes it easier to copy, whereas with MySQL you have to **condense everything** into one file to to allow copying or exporting. Moreover, SQLite is **more accessible and requires very little little assistance**.  

Also our project is **relatively small and doesn't require much scalability** so SQLite scalability so SQLite is perfectly suited to store our data.
