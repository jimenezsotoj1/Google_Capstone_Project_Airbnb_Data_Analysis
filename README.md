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


Before jumping into the exploratory Data Analysis, I created a `cleaned_listings` table from the `listings` dataset where I removed all *Null* values from the listing_url, host_name, neighbourhood_cleansed, room_type and bedrooms columns. Removing null values from the columns of interest resulted in a table with 5,529 unique lisitngs. We will be using the cleaned listings dataset and the reviews dataset in our exploratory data analysis.

## Exploratory Data Analysis (EDA)

In this section, we will detail our analysis to the questions of interest mentioned in the business task and gain preliminary insights through exploratory data analysis. We have divided it into four subsections that aim to answer the questions through a variety of different visualization.

### Properties

There are four different properties types in Denver: Entire homes, private room, shared room and Hotel room.
#### ![image](https://user-images.githubusercontent.com/42790824/195473572-d1e2a873-013d-47ea-b5a8-6c74ac3f508c.png)
From this analysis Emtire homes have the 

```sql
SELECT DISTINCT neighbourhood_cleansed, COUNT(neighbourhood_cleansed) as active_listings
FROM `lithe-creek-364913.airbnb_data.listings_denver`
GROUP BY neighbourhood_cleansed
ORDER BY active_listings DESC;
````



