# Airbnb Data Analysis Project

## Introduction
I love to travel and I always end up using Airbnb to book my stay everywhere I go. Some of my favorite stays include cities such as New York, Denver, London, Barcelona, and Madrid. Over time, I've noticed an increase in cleaning fees for Airbnb bookings without a noticeable increase in the standard of cleanliness. This has me thinking that a good business opportunity exists in providing additional cleaning services for hosts who are already comfortable with offering their place as an accommodation on Airbnb. For this project, I am going to analyze Airbnb data for the most populous city in Colorado, Denver. I've visited Denver with family and friends in separate occasions and every year I find myself wanting to go back to see the snow over the Rocky Mountains during wintertime. The data I will be using for this analysis is collected by **[Inside Airbnb's](insideairbnb.com)** and I  will be using Excel, and SQL in order to solve the following business tasks.

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

I first downloaded two compressed csv files from Inside Airbnb's latest information on Airbnb rentals in Denver as of September 2022:

* `listings` - contains detailed listings data showing attributes for each of the listings. Some of the attributes used in the analysis are neighbourhood_cleansed, room_type, host_name, longitude, latitude, listing_type among others.
* `reviews` - contains detailed reviews given by the guests. Key attributes include date, listing_id, reviewer_id and comment.

I then used an unzipping tool to convert them into regular csv files. 

#### Data Cleaning:

I initially reviewed the downloaded data in excel, since it’s the tool I am most familiar with in order to inspect and understand the information. After inspecting the datasets, I decided to begin the data manipulation process using SQL.

A quick glance at the data shows that there are:


* 5,801 unique listings across 78 neighborhoods in the City of Denver .
* A total of 314,858 reviews for 4,966 of those unique listings.
* Price ranges from $10 - $10,000 a night. The listing with the $10,000 price tag per night is located in Five Points, Denver.


I continued the cleaning process by creating a cleaned_listings table from the listings dataset where I removed all *Null* values from the listing_url, host_name, neighbourhood_cleansed, room_type and bedrooms columns. Removing null values from the columns of interest resulted in a table with 5,529 unique lisitngs. I will be using the cleaned listings dataset and the reviews dataset in the exploratory data analysis.

## Exploratory Data Analysis (EDA)

In this section, I will detail the analysis to the questions of interest mentioned in the business tasks and gain preliminary insights through exploratory data analysis. I have divided the EDA into four subsections that aim to answer the questions through a variety of different visualizations.

### 1.) Properties

My first business task is to identify the different property types in the Airbnb rental market. Having a clear understanding of the rental market allows me to identify my potential customers and better market my Airbnb servicing company. As I begin the exploratory data analysis, I can see that there are four different property types for listings in Denver: Entire homes, private rooms, shared rooms, and Hotel rooms (See table 1).

Initial observations indicate the Entire Homes/apt is the largest segment, making up for 82% of the market or 4,546 of the listings. The second largest market is private rooms, which make up 17% of the market with 916 active listings. Additional analysis over the Entire Homes/apt segment shows that out of the 4,546 listings in the Entire Homes/apt segment, 90% or 4,111 of listings have between 1 to 3 bedrooms (See table 2). This information will be very useful when deciding how I will be pricing my cleaning services in a way that maintains margins and appeals to my customers.

Looking at the data, it is interesting how quickly we can understand the markets' preferences. Identifying the right segment and number of bedrooms per listing allows me, the investor, to make more informed decisions, putting the business one step closer to the goal of successfully identifying and addressing our target market.

**Table 1**

![image](https://user-images.githubusercontent.com/42790824/195717647-3d1988f7-87e1-4641-9b13-12813076c177.png)

**Table 2**

![image](https://user-images.githubusercontent.com/42790824/196058999-1edf1d6a-8981-4e3b-86c8-660b0510e163.png)


### 2.) Prices

The second business task is to identify how pricing varies by neighborhood. Conducting a pricing analysis can help me, the investor, develop different business cases and implement effective pricing strategies for my servicing company. In this analysis, we will start by looking at the top 10 neighborhoods with the largest average price per night (See table 3).

Initial observation shows that the average price per night for the top 10 neighborhoods ranges from $211 to $341 a night. The neighborhoods with the highest average price per night include Belcaro, Cherry Creek, University Park, Cory-Merrill, CBD, Cole, Five points, Country Club, Highland and Civic Center. I decided to only look at the top 10 neighborhoods because hosts don’t necessarily need to charge a cleaning fee. In some cases, the host may feel charging a cleaning fee drives their booking price up too much. In these instances, hosts generally do their own cleaning instead of paying the cost of hiring a cleaning company.

However, by looking at the higher average price points by neighborhood, we can identify the geographic location of hosts that are more likely to have a cleaning fee and be listing a luxury stay. Therefore, they are more likely to want to maintain the advertised living standards and have the capital to afford hiring a cleaning service.

**Table 3**

![image](https://user-images.githubusercontent.com/42790824/195718767-0e97ddfd-87c9-4caa-93cf-1dddc9a1833c.png)

### 3.) Common Themes

For the third business task, I need to identify common themes from the text section of the reviews. For this analysis, I used the reviews dataset and extracted the comments column in order to isolate all 314,858 comments that were on the reviews dataset. I then used an online word cloud generator and uploaded the dataset to create a visualization. A word cloud generator is a tool that uses simple text analysis to help you visualize and summarize qualitative data. The visualization design gives greater emphasis to words that appear more frequently in the text. The larger the word, the higher its frequency. By looking at the comment’s visualization (see table 4), at first glance, I can see that some of the largest adjectives are: great, clean, comfortable, cozy, perfect, and many more. Most of the high-frequency texts shown are overwhelmingly positive adjectives one would hope to find when looking for honest feedback on an Airbnb.

The reviews dataset contained another category where the hosts listed all of the rental amenities in text form so I decided to take a look at the most common amenities mentioned that can be found among Denver Airbnb rentals (See table 5). Visualizing the most frequently listed amenities allows you to identify what is important to your customers. If there are any amenities that require maintenance or replacements, it could present an opportunity for a cleaning business to offer upkeep and replacements for such. By looking at the amenity visualization (see table 5), at first glance, I can see some of the largest words are: alarm, water, coffee, shampoo, hangers, etc.

As an investor, I see these results as an opportunity to create a high-tiered service for customers who would like to replace supplies, add new amenities and replace existing ones like those in the visualization. This tier could consist of a team to organize all house items and replenish supplies and amenities according to the quality standards of a luxury stay.

**Table 4**

![word-cloud](https://user-images.githubusercontent.com/42790824/195720048-17c705ec-f6da-4930-8fb0-51911e546c0d.png)

**Table 5**

![image](https://user-images.githubusercontent.com/42790824/195723366-4a607feb-150b-42ea-9153-b90c23184873.png)

### 4.) Potential Customers

For the fourth and final business task, I am tasked to determine if it's possible to identify a list of potential customers for an Airbnb cleaning Business. For this analysis, I decided run a query and create a new table joining both the cleaned listings dataset and the reviews dataset by the listing id. By combining the two tables using a query I should be able to create a table and pull in a customer list by host_id, host_url, host_name and neighbourhood where I can filter for comments with the word "dirty", and sort them by descending order to get the top hosts with the most reviews containing that word. I want to see the host_id, host_url and host_name instead of the actual reviews because I can later use the hosts information to contact potential customers. 

Our initial findings show that there are 727 reviews containing the word "dirty" amongst 390 unique hosts. Our top 10 hosts with most reviews account for 22% of total comments with 158 comments containing the word "dirty". You can **download** the full list of potential customers (table 6) **[here](https://github.com/jimenezsotoj1/Airbnb_Data_Analysis_Project/blob/main/Airbnb_Data_Analysis_Project_EXCEL.xlsx)**, or see the visual in Tableau **[here](https://public.tableau.com/views/ListofPotentialAirbnbClients-DenverCO/Sheet1?:language=en-US&:display_count=n&:origin=viz_share_link)**

I also conducted additional analysis on the "dirty" comments to show the count of comments by neighbourhood. Conducting this analysis would allow us to see if there are any potential customers in the geographical regions of interest discussed earlier in our [**Prices**](https://github.com/jimenezsotoj1/Airbnb_Data_Analysis_Project/blob/main/README.md#prices) section. By looking at the visualization (table 7) we can see two of our desirable neighborhoods (Five points and Highland) have 127 of the 727 comments linked to hosts.  

**Table 7**

![image](https://user-images.githubusercontent.com/42790824/196058947-e1d502c5-a262-4405-a328-267559a67164.png)

## Conclusion

Through this exploratory data analysis and visualizations, I gained some interesting insights into Denver's Airbnb rental market. Below I will summarize the answers to the questions that I wished to answer at the beginning of the project:

**1.What are the different types of properties in Denver?**
There are four different types of properties in Denver: Entire home/apt, Private room, Shared room and Hotel Room. The Entire home/apt (82%) and the Private room (17%) account for 99% of the current active listings. the vast majority of listings (90% or 4,111 listings) in the Entire home/apt category have between 1 and 3 bedroooms.

**2.How do prices of listings vary by Neighborhood?**
The highest average price per night for the top 10 neighborhoods ranges from $211-$341 a night. The neighborhoods with the highest average price per night include Belcaro, Cherry Creek, University Park, Cory-Merrill, CBD, Cole, Five points, Country Club, Highland and Civic Center.

**3.What are some common themes that can be identified from the text section of the reviews?**
There are certain words such as words such as “great, clean, comfortable, cozy, perfect” that are associated with the location and cleanliness. Most of the texts shown contain overwhelmingly positive adjectives related to their stay.

**4.Can we identify a list of potential customers for an Airbnb cleaning Business?**
Yes, I was able to create a list sorted by host_id, host_url and host_name. There was a total of 727 reviews containing the word dirty amongst 390 unique hosts. Our top 10 hosts with most reviews account for 22% of total comments with 158 comments containing the word "dirty".

## Future Exploration
As an investor, I would want to expand this analysis to multiple cities and compare patterns and trends amongst them before making a final decision. Choosing to do this project on my own area of interest instead of completing a case study for the Google Capstone project has helped me sharpen Data analysis skills and I hope to implement the visualizations and SQL techniques used in this project into my professional setting soon.

