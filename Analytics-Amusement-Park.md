# Analytics at an Amusement Park


## Problem Statement: To run a large-scale amusement park, we require a lot of analytics in various components such as queueing systems, inventory management, park attendance, maximum utilization of resources and revenue. We will investigate some aspects of this and try to provide recommendations on the models which can be used to solve some of these problems.

## Approach:


### A. Predicting the number of Customers to the Park
One of the crucial tasks for an analytics team is to forecast the number of customers to the park. This is of utmost importance as the management, functioning and maintenance of the park will depend on this. Only by knowing how many customers are expected to arrive will the management be able to improve the overall experience while also keeping in mind the cost to do so. As tickets can be sold both online and directly at the park, it is also important to consider the occupancy limit of the park. The seasonal inflow of customers, the growing tourist attractions, online sales, and promotional offers make the forecast much more complicated than usual. The customers enter the park at different times too and it is important to know how many people might come at a given time in the future. The two tasks can be solved by predicting the number of customers that enter a park every hour using a Time-Series approach.
We would require the following data for it.

Data:
• Historical data of customers entering the park (Seasonal and Trends) at each hour /day: Given by the ticket scan data
• Online sales vs In-park purchases and no-show data: Given from ticket scan data
• Split of sales and number of customers by ticket type: 1-day pass/2-day pass: Given by the sales team
• Historical data of marketing promotions by type: Given from marketing team
• Holiday Season: Given from general calendars
• Tourist inflow into city/state/country: Collect from historical tourist inflow/#tourist visas granted and travel share of non-citizens
• Epidemic spread: Collect from CDC guidelines over the past few years
• Historical hourly weather information: Collect it via a weather API/datasets

Model:
Time Series (ARIMA) model to find out the number of people who come in on an hourly basis.
• Time series Variables: Historical Data of Customers, Online sales vs In-Park purchases, Ticket Type splits, Tourist Inflow into City/State/Country, Historical Hourly Weather Information
• Non-Time Series Variables: Holiday Season, Marketing Promotions by Type, Epidemic Spread

Result:
The output of the expected crowd size will help the management optimize their planning; resource management for rides and support staff, inventory management for merchandise and food, safety and maintenance and estimate the revenue generated for financial purposes.




### B. Optimizing the Queue Length and Ride Settings based on Rush and #Customers
Depending on how crowded the park is and how many customers are expected to arrive, we can tweak the all the rides in the park such that there is maximum utilization of the rides (restricted by maximum occupancy), reduced wait times and varied length/settings of rides. The ride settings must be optimized so that when crowds enter the park, they spread evenly to different parts of the park without creating a bottleneck at a specific location. The spread can be controlled by altering the ride settings for the day and changing the length of the queue based on the estimated number of customers at the park.
This problem can be solved by using optimization. We can feed the known parameters like duration of ride and ride size, along with the forecasted visitor count from the previous model to optimize the approach. We also have the expected wait time for each ride and the utilization shares of each ride. The sum of the customers in the queues and the rides would be equal to the expected number of customers for that given day. The output would help us optimize ride settings and allowed queue length such that we minimize the average waiting time and maximize the number of rides that are active.

Given:
• Duration of each ride: Given
• Queue length of each ride: Given
• Number of customers in a ride (ride size): Given
• Current ride utilization shares of each ride: Given, we will try to maximize each value while reducing the wait time
• Expected wait time for each ride: Given
• Constraints: Max queue capacity, max ride settings allowed to be changed for each ride, at least X # of utilizations for each ride, expected number of customers (from model A) = sum of queue lengths


Model:
• Optimize the ride settings like (max occupancy per ride, ride length) and allowed queue length such that we minimize the average waiting time and maximize # number of rides active


Result:
Optimized ride settings and max queue length help increase utilization of all rides as customers are forced to move to other rides. The customers also end up spending less time waiting for rides thereby making them experience the park to the fullest.




### C. Inventory Management in each restaurant to serve the customers
We also need to ensure that the inventory in the restaurants is sufficient to feed the number of people who come in while ensuring that the food does not get wasted. This would require us to consider historical data for the food that has been consumed by the number of customers and consider how the competitors are behaving. It is important to do a competitor check as well because if they are
offering food at a discount, the customers might be more tempted to go there, reducing the demand for the remaining restaurants. We can expect a larger crowd to visit the restaurants sometime during lunch and mostly in the evening when they are done going through the rides. Therefore, we need to make sure that our model gives a good estimate. Hence, we can create a multiple linear regression model for every restaurant in the amusement park.

Given:
• Historical number of customers each day (Given)
• Historical data for demand (Given)
• Historical data of inventory available for each specific item
• Competitor's initiatives (Collect through visiting that restaurant or web scraping)
• Restaurant discounts (Given)
• Human resources available (Given)

Model and Result:
Firstly, we would build a multiple linear regression model using the parameters mentioned above for each restaurant at the amusement park. Then, we would use the forecasted number of customers from model A as an input to this model. This would help us forecast the demand for the food at every restaurant. Using the demand forecasting model we would predict how much extra of each ingredient type would be needed in the restaurant from the inventory so that the staff can accurately plan and transfer to appropriate amount of ingredients well in advance.

Future Scope:
There are additional aspects we which we also discussed which can be expanded upon later. One of the important drivers of the park is human resources. There is an extensive number of staff who work in the park, and we need to optimize the number of staff required at different locations during the day and formulate a timetable for their work schedule. Safety is another major component, and we need to plan the maintenance of the rides in such a way that it does not hinder the overall performance of the park while maintaining maximum safety for the customers. We also did not cover the financial aspect of running a large-scale amusement park. This is also critical as we would like to ensure maximum profitability to pay wages to the staff, power consumption and maintenance of rides. Amusement parks conduct a lot of events and that’s a whole scope as we can cover scheduling of events based on the seasons and the purchasing, planning and inventory management of costumes for the staff.
