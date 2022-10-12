# Airbnb Data Analysis Project

## Introduction
I love to travel and nearly everywhere I go I end up using Airbnb to book my stay. Some of my favorite stays include cities such as New York, Denver, London, Barcelona and Madrid. Over time, I've noticed an increase in cleaning fees for Airbnb bookings without a noticeable increase in the standard of cleanliness. This has me thinking that a good business opportunity exists in investing in an Airbnb cleaning business. For this project I am going to analyze Airbnb data for the most populous city in Colorado, Denver. I've visited Denver with family and friends in separate ocasions and I still find myself wanting to go back to see the Rockies during wintertime. The data I will be using is collected by **[Inside Airbnb's](insideairbnb.com)** and I  will be using Excel, SQL and Tableau in order to solve the following business tasks:

## Business Task
In this scenario, I am the stakeholder interested in investing in an Airbnb servicing company. 
In my experience, cleaning fees when booking an Airbnb have been steadily increasing over time with little to no increase in booking cleanliness. Because cleaning is the only human element required to operate an Airbnb business, I think there is an opportunity to start a servicing company that can improve an Airbnb owner's operating system. 

#### Business Task:

* What are the different types of properties in Denver? Do they vary by neighborhood?
* What are some common themes that can be identified from the text section of the reviews?
* * Can we identify a list of potential customers for an Airbnb cleaning Business?

## Process
#### Data Sources Used:

I first downloaded two compressed csv files from Inside Airbnb's latest information on Airbnb rentals in Denver:

* `listings` - Detailed listings data showing attibutes for each of the listings. Some of the attributes used in the analysis are neighbourhood_cleansed, room_type, host_name, longitude, latitude, listing_type among others.

* `reviews` - Detailed reviews given by the guests. Key attributes include date, listing_id, reviewer_id and comment.

I then used an unzipping tool to convert them into regular csv files. 

#### Data Cleaning:

I initially reviewed the downloaded data in excel, since it’s the tool I am most familiar with in order to inspect and understand the information. After reviewing the datasets, I decided to begin the data manipulation process using SQL. As I tried to upload the  data into the SQL dataset, an error message popped up and it wouldn't allow me to upload the dataset. I revisited the files in Excel and noticed the listing_id column was formatted incorrectly. I formatted the columns to number values and proceded to effectively load the data into SQL.

A quick glance at the data shows that there are:


* **5,801** unique listings across **78** neighbourhoods in the City of Denver .
* A total of **314,858** reviews for **4,966** of those unique listings.
* listing price ranges from $10 - $10,000 a night. The listing with the $10,000 price tag per night is located in Five Points, Denver.


During the quick glance, I noticed smome null values in the `listings` dataset and decided to create cleaned a `cleaned_listings` table to use for my analysis. Removing null values from the columns of interest resulted in a table with **5,529** unique lisitngs.

## Exploratory Data Analysis (EDA)

```sql
SELECT DISTINCT neighbourhood_cleansed, COUNT(neighbourhood_cleansed) as active_listings
FROM `lithe-creek-364913.airbnb_data.listings_denver`
GROUP BY neighbourhood_cleansed
ORDER BY active_listings DESC;
````



