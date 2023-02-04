# Draft Proposal for my Capstone Project on Air Ticket Fare Prediction

Booking cheap air tickets can vary in terms of hassle, depending on the individual's preferences, resources, and circumstances. Some factors that can affect the hassle of booking cheap air tickets include Research and comparison, getting hold of the correct timing of the travel that is economic, budget and ticket availability. Overall, the hassle of booking cheap air tickets can be reduced by being organized, flexible, and proactive in your approach. By doing research, staying on top of prices and promotions, and being willing to book in advance or make changes to your travel plans, you can increase your chances of finding the best deal on air tickets. Booking relatively cheaper air tickets has always been a thing on mind for me and with this project, I intend on doing this. 

In this project, I'll analyze and explore a dataset obtained from the "Ease My Trip" website, as well as run various statistical hypothesis tests to extract meaningful information.

## Research Questions

1. What is the difference in ticket prices between Economy and Business class?
2. Does price vary with Airlines?
3. Is the price of a ticket affected by the departure and arrival times?
4. How does the price change as the source and destination change?
5. Does the number of stops have an effect on the price?
6. What factors have the most influence on price?

## Data Collection

When researched, I could not find any API that I could you to scrap data from Easemytrip website. I used python web scraping library - Beautiful Soup to gather data from their website. Also, I used a tool called Octoparse to extract some data aswell. The information was gathered in two parts: one for economy class tickets and one for business class tickets. The site yielded a total of 300261 distinct flight booking options. From February 11th to March 31st, 2022, data was gathered for 50 days. The data source was secondary data obtained from the Ease My Trip website.

## Dataset 

The dataset contains flight booking options from the website Easemytrip for flights between India's top six metro cities. The cleaned dataset contains 300261 datapoints and 11 features.

## Important Features

+ Airline: The airline column stores the name of the airline company. There are six different airlines in this category.
+ Flight: Flight stores data about the plane's flight code. It is a distinguishing feature.
+ Source City: The city from which the flight departs is referred to as the source city. It is a distinct feature with six distinct cities.
+ Departure Time: This is a derived categorical feature obtained by binning time periods. It stores departure time information and has six distinct time labels.
+ Stops: A three-valued categorical feature that stores the number of stops between the source and destination cities.
+ Destination City: The city where the flight will land is referred to as the destination city. It is a distinct feature with six distinct cities.
+ Class: A categorical feature containing seat class information; it has two distinct values: Business and Economy.
+ Duration: A continuous feature that displays the total time required to travel between cities in hours.
+ Days Left: A derived characteristic calculated by dividing the trip date by the booking date.
+ Price: Target variable stores information about ticket prices.

## ML Models

I intend on deploying K-Nearest Neighbours, Linear Regression, XGBoost Regressor, CatBoost Regressor. Once I see which model will perform better, I will continue with that particular model and then I will see if I have to improve the score. 
