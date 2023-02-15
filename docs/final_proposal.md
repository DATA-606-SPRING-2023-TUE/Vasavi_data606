# Final Proposal for my Capstone Project on Air Ticket Fare Prediction

Booking cheap air tickets can vary in terms of hassle, depending on the individual's preferences, resources, and circumstances. Some factors that can affect the hassle of booking cheap air tickets include Research and comparison, getting hold of the correct timing of the travel that is economic, budget and ticket availability. Overall, the hassle of booking cheap air tickets can be reduced by being organized, flexible, and proactive in your approach. By doing research, staying on top of prices and promotions, and being willing to book in advance or make changes to your travel plans, you can increase your chances of finding the best deal on air tickets. Booking relatively cheaper air tickets has always been a thing on mind for me and with this project, I intend on doing this. 

In this project, I'll analyze and explore a dataset obtained from the "Ease My Trip" website, as well as run various statistical hypothesis tests to extract meaningful information. I am going to predict the price of the air tickets as accurately as possible. Since the price here is a numeric field, a regression model would be a great pick.

![image](https://user-images.githubusercontent.com/56116206/218330081-aa9144d6-bef0-40af-9fb1-9b723a388cf8.png)


## Research Questions

1. What is the difference in ticket prices between Economy and Business class?
2. Does price vary with Airlines?
3. Is the price of a ticket affected by the departure and arrival times?
4. How does the price change as the source and destination change?
5. Does the number of stops have an effect on the price?
6. What factors have the most influence on price?
7. How is the price affected when tickets are bought in just 1 or 2 days before departure?
8. Price vs Days left using Linear Regression OLS method.
9. Price vs Flight Duration Linear Regression OLS method.
10. Which ML model is predicting the price of the flight ticket as accurately as possible?
11. Will I be needing any techniques to improve the score of the best ML model? If yes, what technique should I use to make the model more effective?

## Data Collection

When researched, I could not find any API that I could use to scrap data from Easemytrip website. I used python web scraping library - Beautiful Soup to gather data from their website. Also, I used a tool called Octoparse to extract some data aswell. The information was gathered in two parts: one for economy class tickets and one for business class tickets. The site yielded a total of 300261 distinct flight booking options. From February 11th to March 31st, 2022, data was gathered for 50 days. The data source was secondary data obtained from the Ease My Trip website.

## Dataset 

The dataset contains flight booking options from the website Easemytrip for flights between India's top six metro cities. The cleaned dataset contains 300261 datapoints and 11 features.

_Link to the dataset_: https://docs.google.com/spreadsheets/d/1Bi_slUGz4cPL5Ng1QOYFTRh4t8d_w0ZulvKm9JVX5tU/edit?usp=sharing

## Features Selection

There are many features in the dataset that I scraped like: Airline, From, To, Price, Class category, class, day, month, flight no, route, departure hour, arrival hour, departure period, arrival period, route index, duration, stops, stops category, arrival daytime, arrival daytime category, days left, departure daytime, departure daytime category and  month category, I am planning on selecting only the below columns as features and price as the target variable. The possible explanation of the features and target variables is given below:


+ _Airline_: The airline column stores the name of the airline company. There are six different airlines in this category.
+ _Flight_: Flight stores data about the plane's flight code. It is a distinguishing feature.
+ _Source City_: The city from which the flight departs is referred to as the source city. It is a distinct feature with six distinct cities.
+ _Departure Time_: This is a derived categorical feature obtained by binning time periods. It stores departure time information and has six distinct time labels.
+ _Stops_: A three-valued categorical feature that stores the number of stops between the source and destination cities.
+ _Destination City_: The city where the flight will land is referred to as the destination city. It is a distinct feature with six distinct cities.
+ _Class_: A categorical feature containing seat class information; it has two distinct values: Business and Economy.
+ _Duration_: A continuous feature that displays the total time required to travel between cities in hours.
+ _Days Left_: This is a derived characteristic that is calculated by subtracting the trip date by the booking date.
+ _Price_: Target variable stores information about ticket prices.

There are few features like airline, destination city and source city which are nominal data and will need *OnehotEncoder* to encode and transform them.

## ML Models

I intend on deploying _K-Nearest Neighbours Regressor_, _Linear Regressor_, _XGBoost Regressor_, _CatBoost Regressor_. Once I see which model will perform better, I will continue with that particular model and then I will see if I have to improve the score. 

I will calculate the R2 values and the %MAE values for all the models mentioned above against the train and test datasets to see which model is performing better. Once I decide the best model, I plan on using the *stacking and bending* technique to improve the score. For this method, I intend on having the best performing model in the final layer and other regressor models in the initial layers.

## Outcome

The best regressor to predict air ticket fare is found out and score improvement technique will be used to make the model more accurate so that the price of the air ticket can be predicted more effectively and accurately.
