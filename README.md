# Airbnb Data Analysis Project

## Introduction
I love to travel, and nearly everywhere I go, I end up using Airbnb to book my stay. Some of my favorite stays include cities such as New York, Denver, London, Barcelona and Madrid. Over time, I've noticed an increase in cleaning fees for Airbnb bookings without a noticeable increase in the standard of cleanliness. This has me thinking that a good business opportunity exists in investing in an Airbnb cleaning business. For this project I am going to analyze Airbnb data for the most populous city in Colorado, Denver. The data I will be using is collected by [inside Airbnb](insideairbnb.com) and I  will be using Excel, SQL and Tableau in order to solve the following business tasks:

## Business Task
In this scenario, I am the stakeholder interested in investing in an Airbnb servicing company. 
In my experience, cleaning fees when booking an Airbnb have been steadily increasing over time with little to no increase in booking cleanliness. Because cleaning is the only human element required to operate an Airbnb business, I think there is an opportunity to start a servicing company that can improve an Airbnb owner's operating system. 

#### Business Task:

* Can we identify a list of potential customers for an Airbnb cleaning Business in Denver, Colorado?

## Process
#### Data Sources Used:

I first downloaded two compressed csv files from [Inside Airbnb's](insideairbnb.com) latest information on Airbnb rentals in Denver, Colorado. I then used an unzipping tool to convert them into regular csv files. 

#### Data Cleaning:

I initially reviewed the downloaded data in excel, since it’s the tool I am most familiar with in order to inspect and understand the information. The datasets contained useful information on listings, metrics, review data and more. After reviewing, I decided to begin the data manipulation process using SQL. As I tried to upload the  data into the SQL dataset, an error message popped up and it wouldn't allow me to upload the dataset. I reviewed the files in Excel once again and noticed the *listing_id* column was not formatted correclty. I formatted the columns to number values and proceded to effectively load the data into SQL.

## Exploratory Data Analysis (EDA)

**SELECT DISTINCT neighbourhood_cleansed, COUNT(neighbourhood_cleansed) as active_listings

FROM `lithe-creek-364913.airbnb_data.listings_denver`

GROUP BY neighbourhood_cleansed

ORDER BY active_listings DESC;**




