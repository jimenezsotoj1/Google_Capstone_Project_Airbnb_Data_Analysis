# Airbnb Data Analysis Project

## Introduction
I love to travel and nearly everywhere I go I end up using Airbnb to book my stay. Some of my favorite stays include cities such as New York, Denver, London, Barcelona and Madrid. Over time, I've noticed an increase in cleaning fees for Airbnb bookings without a noticeable increase in the standard of cleanliness. This has me thinking that a good business opportunity exists in investing in an Airbnb cleaning business. For this project I am going to analyze Airbnb data for the most populous city in Colorado, Denver. I've visited Denver with family and friends in separate ocasions and every year I find myself wanting to go back to see the Rocky Mountains during wintertime. The data I will be using for this analysis is collected by **[Inside Airbnb's](insideairbnb.com)** and I  will be using Excel, and SQL in order to solve the following business tasks.

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

* `listings` - contains detailed listings data showing attibutes for each of the listings. Some of the attributes used in the analysis are neighbourhood_cleansed, room_type, host_name, longitude, latitude, listing_type among others.
* `reviews` - contains detailed reviews given by the guests. Key attributes include date, listing_id, reviewer_id and comment.

I then used an unzipping tool to convert them into regular csv files. 

#### Data Cleaning:

I initially reviewed the downloaded data in excel, since it’s the tool I am most familiar with in order to inspect and understand the information. After inspecting the datasets, I decided to begin the data manipulation process using SQL.

A quick glance at the data shows that there are:


* 5,801 unique listings across 78 neighbourhoods in the City of Denver .
* A total of 314,858 reviews for 4,966 of those unique listings.
* Price ranges from $10 - $10,000 a night. The listing with the $10,000 price tag per night is located in Five Points, Denver.


I continued the cleaning process by creating a `cleaned_listings` table from the `listings` dataset where I removed all *Null* values from the listing_url, host_name, neighbourhood_cleansed, room_type and bedrooms columns. Removing null values from the columns of interest resulted in a table with 5,529 unique lisitngs. I will be using the cleaned listings dataset and the reviews dataset in the exploratory data analysis.

## Exploratory Data Analysis (EDA)

In this section, we will detail the analysis to the questions of interest mentioned in the business tasks and gain preliminary insights through exploratory data analysis. I have divided the EDA into four subsections that aim to answer the questions through a variety of different visualizations.

### Properties

My first business task is to identify the different property types in the Airbnb rental market. Having a clear understanding of the rental market allows me to identify my potential customers and better market my Airbnb servicing company. As I begin the eploratory data analysis, we can see that there are four different property types for listings in Denver: Entire homes, private room, shared room and Hotel room (See table 1).

Initial observations indicate the Entire Homes/apt is the largest segment, making up for 82% of the market or 4,546 of the listings. The second largest market belongs to Private rooms, which make up for 17% of the market with 916 active listings. Additional analysis over the Entire Homes/apt segment we can see that out of the 4,546 listings in the Entire Homes/apt segment, 90% or 4,111 of listings have between 1 to 3 bedrooms (See table 2). This information will be very useful when deciding how I will be pricing my cleaning services in a way that maintains margins and appeals to my customers.

Looking at the data, it is interesting how quickly we are able to understand the markets' preference. Identifying the right segment and amount of bedrooms per listing allows me, the investor, to make more informed decicions, putting the business one step closer towards the goal of successfully identifying the customers and addressing them.

**Table 1**

![image](https://user-images.githubusercontent.com/42790824/195717647-3d1988f7-87e1-4641-9b13-12813076c177.png)

**Table 2**

![image](https://user-images.githubusercontent.com/42790824/195717495-cdef1b89-ecfa-48fe-9373-2eb42fefe629.png)


### Prices

The second business task is to identify how pricing varies by neighbourhood. Conducting a pricing analysis can help me, the investor, develop different business cases and implement effective pricing strategies for my servicing company. In this analysis, we will start by taking a look at the top 10 neighbourhoods with the largest average price per night (See table 3). 

Initial observation shows that the average privce per night for the top 10 neighbourhoods ranges from $211 to $341 a night. The neighbourhoods with the highest average price per night include Belcaro, Cherry Creeek, University Park, Cory-Merrill, CBD, Cole, Five points, Country club, Highland and Civic Center. I decided to only look at the top 10 neighbourhoods because hosts don’t necessarily need to charge a cleaning fee. In some cases, the host may feel charging a cleaning fee drives their booking price up too much. In these instances, hosts generally do their own cleaning or pay the cost themselves of hiring a cleaning company.

However, by looking at the higher average price points by neighbourhood, we can identify the geographic location of hosts that are more likely to have a cleaning fee and be listing a luxury stay. Therefore, they are more likely to want to maintain the advertised living standards and have the capital to do so.

**Table 3**

![image](https://user-images.githubusercontent.com/42790824/195718767-0e97ddfd-87c9-4caa-93cf-1dddc9a1833c.png)

### Common Themes

For the third business task, I need to identify common themes from the text section of the reviews. For this analysis I used the reviews dataset and extracted the comments column in order to isolate all 314,858 comments that were left on reviews. I then used  word cloud generator online and uploaded the dataset to create a visualization. A word cloud generator is a tool that uses simple text analysis to help you visualize and summarize qualitative data. The visualization design gives greater emphasis to words that appear more frequently in the text. The larger the word, the higher its frequency. 

By looking at the comments visualization (see table 4), at first glance, I can see that the some of the largest words that stick out to me are: great, clean, comfortable, cozy, perfect and many more. Most of the high frequency texts shown are overwhelmingly positive adjectives one would hope to find when looking for honest feedback on an Airbnb. 

The reviews dataset contained another category where the hosts listed all of the rental amenities in text form so I decided to take a look at what are the most common amenities you can find amongst Denver Airbnb rentals (See table 5). Visualizing the most frequently listed ammenities allows you to identify what is important to your customers. If there are any amenities that require maintenance or replacements, they could present an oportunity for a cleaning business to offer upkeep and replacements for such.  By looking at the amenities visualization (see table 5), at first glance, I can see some of the largest words shown are: alarm, parking, water, coffee, shampoo, hangers, etc. 

As an inverstor, I see these results as an opportunity to create a high-tiered service for customers who would like to replace supplies, add new amenities and replace existing like the ones with tyhe highest frequency. This tier could consist of a team to organize all house items and replenish supplies and amenities according to the quality standards of a luxury stay.

**Table 4**

![word-cloud](https://user-images.githubusercontent.com/42790824/195720048-17c705ec-f6da-4930-8fb0-51911e546c0d.png)

**Table 5**

![image](https://user-images.githubusercontent.com/42790824/195723366-4a607feb-150b-42ea-9153-b90c23184873.png)

### Potential Customers

For the fourth and final business task, I am tasked to determine if its possible to identify a list of potential customers for an Airbnb cleaning Business. For this analysis I decided run a query and create a new table joining both the cleaned listings dataset and the reviews dataset by the listing id. By combining the two tables using a query I should be able to create a table and run another query to pull in a customer list by host_id, host_url, host_name, neighbourhood where I can filter for comments with the word "dirty" for example, and sort them by descending order to get the top hosts with the most reviews with that word. I want to see the host_id, host_url and host_name instead of the actual review because I can later use the hosts information to contact my potential customers. 

Our initial findings show that there are 727 reviews containing the word dirty amongst 390 unique hosts. Our top 10 hosts with most reviews account for 22% of total comments with 158 comments containing the word "dirty". You can see the full list of potential customers (table 6) **here**. 

I also conducted additional analysis on the "dirty" comments to show the count of comments by neighbourhood. Conducting this analysis would allow us to see if there are any potential customers in the geographical regions of interest discussed earlier in our **Prices** setcion. By looking at the visualization (table 7) we can see two of our desirable neighbourhoods (Five points and Highland) have 127 of the 727 comments linked to hosts.  

**Table 7**

![image](https://user-images.githubusercontent.com/42790824/195734815-aff2b6e7-45f4-49d0-8546-7d65cddc370a.png)

## Conclusion

Through this exploratory data analysis and visualizations, we gained some interesting insights into Denver's Airbnb rental market. Below I will summarise the answers to the questions that we wished to answer at the beginning of the project:

**1.What are the different types of properties in Denver?**
There are four different types of properties in Denver: Entire home/apt, Private room, Shared room and Hotel Room. The Entire home/apt (82%) and the Private room (17%) account for 99% of the current active listings. the vast majority of listings (90% or 4,111 listigns) in the Entire home/apt category have between 1 and 3 bedroooms.

**2.How do prices of listings vary by Neighborhood?**
The highest average price per night for the top 10 neighbourhoods ranges from $211-$341 a night. The neighbourhoods with the highest average price per night include Belcaro, Cherry Creeek, University Park, Cory-Merrill, CBD, Cole, Five points, Country club, Highland and Civic Center.

**3.* What are some common themes that can be identified from the text section of the reviews?**
There were two visualizations created from the text section of the reviews. One




