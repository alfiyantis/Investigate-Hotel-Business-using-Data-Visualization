Investigate Hotel Business using Data Visualization
===

## Table of Contents
* **[Background and Objective](#backg)**
* **[Research Question](#quest)**
* **[Data and Assumptions](#datas)**
* **[Data Analysis](#analys)**
* **[Summary](#summary)**

<a name="backg"></a>
## Background and Objective
Analyzing business performance is significant to apply, one of which is an effort to achieve strategic steps and knows the company's weaknesses. The results of the performance analysis can be use as a basis for developing better business strategies in the future.
Knowing the customer behavior is one of the efforts in analyzing the performance of the hotel business. Customer behavior analysis is needed to help us understand what influences consumer decisions to buy a product, additionaly can fill market gaps and identify what is need or products that are not selling well in the market. In addition, analysis of customer behavior can help decide how to present products that produce a maximum impact on customers.
<a name="quest"></a>
## Research Question
- What types of hotels do guests visit most often?
- Does the duration of the stay affect the cancellation rate of hotel bookings?
- Does the time gap between hotel bookings and the customer's arrival day affect the cancellation rate of hotel reservations?
<a name="datas"></a>
## Data and Assumptions
The sample data used (data frame) is the data from a hotel reservation. It consists of 29 columns and 119390 rows.
Data collection time period is between 2017 – 2019.
<a name="analys"></a>
## Data Analysis
Preprocessing should be done before analyze the data.
Preprocessing stage that needs to do:
- Fill in the null data in rows/columns
- Adjusting data that is less precise, such as data in the "meal" column (there are two categories that have the same meaning, namely no meal and undefined)
- Delete rows with total guest < 1 [`total_guests = adults + children + babies`]

![fig1](https://user-images.githubusercontent.com/105115689/187035065-6071506a-1af4-46e0-bb76-b5948053524f.png)

Grouping by hotel type should be done to know the type of hotel that the customers prefer. In addition, a classification based on the time of stay (per month) needs to get done to find out whether there are certain times when sales increase or decrease.
Data in September and October are available for three years, while only two years in other months. So, it is necessary to calculate the average number of customers every month.

![fig2](https://user-images.githubusercontent.com/105115689/187035231-7c704479-e0da-4c4e-826d-5e56ddd14471.png)

City hotels have more visitors than resort hotels. However, both experienced peak increases in guest numbers in July and December. In addition, the city hotel experienced a significant decrease in the number of guests in September.
To find out the relationship between stay duration and hotel booking cancellation rate, the first thing that needs to be done is to know the total stay duration of each transaction.

`total_stay_duration = stays_in_weekend_nights + stays_in_weekdays_nights`

Then clean the data that has a total stay duration < 1 and see the distribution.
 
 ![fig3](https://user-images.githubusercontent.com/105115689/187035317-8dcca9c1-334a-4a2c-8867-9c835338dd3f.png)

The apparent distribution ends in the range of 15 nights, so total stay duration >=15 is considered as one group. Then make the cancellation rate column based on hotel type and total stay duration.

`cancellation_rate =  number of canceled transactions/number of all transactions`

![fig4](https://user-images.githubusercontent.com/105115689/187035378-923f2e91-577c-46d0-a626-8b4ef8724411.png)

In general, both types of hotels (city and resort hotels) have a relationship between stay duration and hotel booking cancellation rates. The longer the stay duration, the higher the probability of canceling the hotel booking.
To find out the relationship between lead time and the rate of cancellation of hotel reservations, the first thing that needs to be done is to know the distribution of lead times.

![fig5](https://user-images.githubusercontent.com/105115689/187035426-45ba4228-b13e-41cd-a0d0-5af195191b30.png)

Since the distribution on day 400 has significantly decreased, the grouping created by month until it reaches around that day (390 days to be precise). To simplify the visualization process, lead times are grouped by month. Then make the cancellation rate column based on hotel type and lead time group.

![fig6](https://user-images.githubusercontent.com/105115689/187036519-d8b0b900-c4a1-4c28-b89e-4187baa69b87.png)

Reservations with a maximum lead time of 1 month have the lowest cancellation rate. The longer the lead time, the higher the probability of canceling the hotel booking.
<a name="summary"></a>
## Summary
City hotels have a booking percentage of 33.08% compared to resort hotels. Where the percentage of city hotel reservations is 66.54%, while resort hotels are only 33.46%. However, there is an increase in bookings at both types of hotels during the holiday season (in July and September)
In addition, the duration of the stay and the length of the lead time affect the hotel cancellation rate. The longer the duration of stay and the lead time in hotel bookings, the higher the cancellation rate of hotel room reservations.
