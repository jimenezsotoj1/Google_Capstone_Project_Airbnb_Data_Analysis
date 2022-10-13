# Airbnb Data Analysis Project

## Introduction
I love to travel and nearly everywhere I go I end up using Airbnb to book my stay. Some of my favorite stays include cities such as New York, Denver, London, Barcelona and Madrid. Over time, I've noticed an increase in cleaning fees for Airbnb bookings without a noticeable increase in the standard of cleanliness. This has me thinking that a good business opportunity exists in investing in an Airbnb cleaning business. For this project I am going to analyze Airbnb data for the most populous city in Colorado, Denver. I've visited Denver with family and friends in separate ocasions and every year I find myself wanting to go back to see the Rocky Mountains during wintertime. The data I will be using for this analysis is collected by **[Inside Airbnb's](insideairbnb.com)** and I  will be using Excel, SQL and Tableau in order to solve the following business tasks:

## Business Task
In this scenario, I am the stakeholder interested in investing in an Airbnb servicing company. 
In my experience, cleaning fees when booking an Airbnb have been steadily increasing over time with little to no changes in booking cleanliness. Because cleaning is the only human element required to operate an Airbnb business, I believe a good business opportunity exists in creating a servicing company that can improve an Airbnb owner's operating system. 

#### Business Task:

* What are the different types of properties in Denver? 
* How do prices of listings vary by Neighborhood?
* What are some common themes that can be identified from the text section of the reviews?
* Can we identify a list of potential customers for an Airbnb cleaning Business?

## Process
#### Data Sources Used:

I first downloaded two compressed csv files from Inside Airbnb's latest information on Airbnb rentals in Denver:

* `listings` - Detailed listings data showing attibutes for each of the listings. Some of the attributes used in the analysis are neighbourhood_cleansed, room_type, host_name, longitude, latitude, listing_type among others.

* `reviews` - Detailed reviews given by the guests. Key attributes include date, listing_id, reviewer_id and comment.

I then used an unzipping tool to convert them into regular csv files. 

#### Data Cleaning:

I initially reviewed the downloaded data in excel, since it’s the tool I am most familiar with in order to inspect and understand the information. After reviewing the datasets, I decided to begin the data manipulation process using SQL.

A quick glance at the data shows that there are:


* **5,801** unique listings across **78** neighbourhoods in the City of Denver .
* A total of **314,858** reviews for **4,966** of those unique listings.
* Price ranges from **$10 - $10,000** a night. The listing with the $10,000 price tag per night is located in Five Points, Denver.


I created a `cleaned_listings` table from the `listings` dataset where I removed all *Null* values from the listing_url, host_name, neighbourhood_cleansed, room_type and bedrooms columns. Removing null values from the columns of interest resulted in a table with 5,529 unique lisitngs. We will be using the cleaned listings dataset and the reviews dataset in our exploratory data analysis.

## Exploratory Data Analysis (EDA)

In this section, we will detail our analysis to the questions of interest mentioned in the business task and gain preliminary insights through exploratory data analysis. We have divided it into four subsections that aim to answer the questions through a variety of different visualization.

### Properties

Our first business task is to identify the different property types in the Arbnb rental market. Having a clear understanding of the rental market allows us to identify our potential customers and better market our Airbnb servicing company. As we begin our eploratory data analysis, we can see that there are four different property types for listings in Denver: Entire homes, private room, shared room and Hotel room.

![image](https://user-images.githubusercontent.com/42790824/195486012-73b0a7b9-94f7-429d-9c2f-b5c09d2875de.png)

Initial observations indicate the Entire Homes/apt is the largest segment, making up for 82% of the market or 4,546 of the listings. The second largest market belongs to Private rooms, which make up for 17% of the market with 916 active listings. By diving deeper into the Entire Homes/apt segment we can see that out of the 4,546 listings in the Entire Homes/apt segment, 90% or 4,111 of listings have between 1-3 bedrooms.

![image](https://user-images.githubusercontent.com/42790824/195491267-12641390-9851-4a22-a575-6f8cc8669d98.png)

Looking at the data, it is interesting how quickly we are able to understand the markets' preference. Identifying the right segment and bedroom distribution allows us to make more informed decicions, putting us one step closer to their goal of successfully identifying the different types of potential customers and developing a strategy to address them.

### Prices

Our second business task is to identify how pricing varies by neighbourhood. For this we will run a query in SQL and create a visualization using Excel. 

![image](https://user-images.githubusercontent.com/42790824/195494052-8774e438-a781-4b2e-94ca-4122821b5bef.png)


```sql
SELECT DISTINCT neighbourhood_cleansed, COUNT(neighbourhood_cleansed) as active_listings
FROM `lithe-creek-364913.airbnb_data.listings_denver`
GROUP BY neighbourhood_cleansed
ORDER BY active_listings DESC;
````



