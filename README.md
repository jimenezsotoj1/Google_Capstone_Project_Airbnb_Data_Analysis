# Airbnb Data Analysis Project

## Introduction
I love to travel and nearly everywhere I go I end up using Airbnb to book my stay. Some of my favorite stays include cities such as New York, Denver, London, Barcelona and Madrid. Over time, I've noticed an increase in cleaning fees for Airbnb bookings without a noticeable increase in the standard of cleanliness. This has me thinking that a good business opportunity exists in investing in an Airbnb cleaning business. For this project I am going to analyze Airbnb data for the most populous city in Colorado, Denver. I've visited Denver with family and friends in separate ocasions and every year I find myself wanting to go back to see the Rocky Mountains during wintertime. The data I will be using for this analysis is collected by **[Inside Airbnb's](insideairbnb.com)** and I  will be using Excel, SQL and Tableau in order to solve the following business tasks.

## Business Tasks
In this scenario, I am the stakeholder interested in investing in an Airbnb servicing company. 
In my experience, cleaning fees when booking an Airbnb have been steadily increasing over time with little to no changes in booking cleanliness. Because cleaning is the only human element required to operate an Airbnb business, I believe a good business opportunity exists in creating a servicing company that can improve an Airbnb owner's operating system. 

#### Business Tasks:

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


I then created a `cleaned_listings` table from the `listings` dataset where I removed all *Null* values from the listing_url, host_name, neighbourhood_cleansed, room_type and bedrooms columns. Removing null values from the columns of interest resulted in a table with 5,529 unique lisitngs. We will be using the cleaned listings dataset and the reviews dataset in the exploratory data analysis.

## Exploratory Data Analysis (EDA)

In this section, we will detail the analysis to the questions of interest mentioned in the business task and gain preliminary insights through exploratory data analysis. We have divided it into four subsections that aim to answer the questions through a variety of different visualizations.

### Properties

My first business task is to identify the different property types in the Airbnb rental market. Having a clear understanding of the rental market allows me to identify my potential customers and better market my Airbnb servicing company. As I begin the eploratory data analysis, we can see that there are four different property types for listings in Denver: Entire homes, private room, shared room and Hotel room (See table 1).

Initial observations indicate the Entire Homes/apt is the largest segment, making up for 82% of the market or 4,546 of the listings. The second largest market belongs to Private rooms, which make up for 17% of the market with 916 active listings. Additional analysis over the Entire Homes/apt segment we can see that out of the 4,546 listings in the Entire Homes/apt segment, 90% or 4,111 of listings have between 1 to 3 bedrooms (See table 2). This information will be very useful when deciding how I will be pricing my cleaning services in a way that maintains margins and appeals to my customers.

Looking at the data, it is interesting how quickly we are able to understand the markets' preference. Identifying the right segment and amount of bedrooms per listing allows us to make more informed decicions, putting us one step closer to their goal of successfully identifying the different types of potential customers and developing a strategy to address them.

**Table 1**

![image](https://user-images.githubusercontent.com/42790824/195717647-3d1988f7-87e1-4641-9b13-12813076c177.png)

**Table 2**

![image](https://user-images.githubusercontent.com/42790824/195717495-cdef1b89-ecfa-48fe-9373-2eb42fefe629.png)


### Prices

The second business task is to identify how pricing varies by neighbourhood. Conducting a pricing analysis can help me, the inverstor in this scenario, develop different business cases and implement effective pricing strategies for my servicing company. In this analysis, we will start by taking a look at the top 10 neighbourhoods with the largest average price per night (See table 3). 

Initial observation shows that the average privce per night for the top 10 neighbourhoods ranges from $211 to $341 a night. The neighbourhoods with the highest average price per night include Belcaro, Cherry Creeek, University Park, Cory-Merrill, CBD, Cole, Five points, Country club, Highland and Civic Center. I decided to only look at the top 10 neighbourhoods because hosts don’t necessarily need to charge a cleaning fee. In some cases, the host may feel charging a cleaning fee drives their booking price up too much. In these instances, hosts generally do their own cleaning or pay the cost themselves of hiring a cleaning company.

However, by looking at the higher average price points by neighbourhood, we can identify the geographic location of hosts that are more likely to have a cleaning fee and be listing a luxury stay. Therefore, they are more likely to want to maintain the advertised living standards and have the capital to do so.

**Table 3**

![image](https://user-images.githubusercontent.com/42790824/195718174-988fd056-e835-4064-8244-d3c98fe6f1d5.png)

### Common Themes

For the third business task, I need to identify ommon themesfrom the text section of the reviews. For this excercise I ran a query and created a new table where I joined the cleaned listings and the reviews datasets by listing ID.




```sql
SELECT DISTINCT neighbourhood_cleansed, COUNT(neighbourhood_cleansed) as active_listings
FROM `lithe-creek-364913.airbnb_data.listings_denver`
GROUP BY neighbourhood_cleansed
ORDER BY active_listings DESC;
````



