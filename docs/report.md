# Final Proposal for my Capstone Project on Air Ticket Fare Prediction
____
## By: Vasavi Koonapalli

Presentation Slides for this project can be found here.
Presentation Video for this project can be found here.

## 1. Introduction
____
Booking cheap air tickets can vary in terms of hassle, depending on the individual's preferences, resources, and circumstances. Some factors that can affect the hassle of booking cheap air tickets include Research and comparison, getting hold of the correct timing of the travel that is economic, budget and ticket availability. Overall, the hassle of booking cheap air tickets can be reduced by being organized, flexible, and proactive in your approach. By doing research, staying on top of prices and promotions, and being willing to book in advance or make changes to your travel plans, you can increase your chances of finding the best deal on air tickets. Booking relatively cheaper air tickets has always been a thing on mind for me and with this project, I intend on doing this. 

In this project, I'll analyze and explore a dataset obtained from the "Ease My Trip" website, as well as run various statistical hypothesis tests to extract meaningful information. I am going to predict the price of the air tickets as accurately as possible. Since the price here is a numeric field, a regression model would be a great pick.

![image](https://user-images.githubusercontent.com/56116206/218330081-aa9144d6-bef0-40af-9fb1-9b723a388cf8.png)

## 2. Research Questions
____
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

## 3. Dataset
____
When researched, I could not find any API that I could use to scrap data from Easemytrip website. I used python web scraping library - Beautiful Soup to gather data from their website. Also, I used a tool called Octoparse to extract some data aswell. The information was gathered in two parts: one for economy class tickets and one for business class tickets. The site yielded a total of 300261 distinct flight booking options. From February 11th to March 31st, 2022, data was gathered for 50 days. The data source was secondary data obtained from the Ease My Trip website.
The dataset contains flight booking options from the website Easemytrip for flights between India's top six metro cities. The cleaned dataset contains 300261 datapoints and 11 features.

_Link to the dataset_: https://docs.google.com/spreadsheets/d/1Bi_slUGz4cPL5Ng1QOYFTRh4t8d_w0ZulvKm9JVX5tU/edit?usp=sharing

## 4. Exploratory Data Analysis
____
When I performed some initial exploartory data analysis on the dataset, I found that the mean of the price is around 20,000 INR, while the median was around 7,500 INR. It was seen that only 2 airlines flew passengers in business class, while all the other airlines operated only Economy class. The price of the business class tickets was almost 6.5 times the price of the economy class ticket. 
AirAsia seems to have the cheapest flights when Air India and Vistara are more expensive. However it looks like Vistara's business tickets are a little more expensive than the Air India's ones. 
As expected, flights leaving early in the morning remained the cheapest way to travel. But it was also found that flights arriving early morning are also cheap and afternoon flights are a bit cheaper than morning and night flights. It was clear that the more stops there are, the more expensive the flight is, except for AirAsia where the prices seem more constant. 

We all know that the duration of flight has everything to do with the cost of the ticket. 
It is clear that, here the relationship is not linear but can be approximated with a second degree curve. The prices reaches a high price at a duration of 20 hours before lowering again.
![image](https://user-images.githubusercontent.com/56116206/236880184-4ddc2166-043d-47c6-b154-af425192b6a6.png)

<img width="179" alt="image" src="https://user-images.githubusercontent.com/56116206/236880009-59ab5dd6-cf55-4e1e-a85b-a030cc864696.png">

I then wanted to see how price is varying when I buy the ticket just 1 or 2 days before the departure. The regression graph here shows the graph for this. It is possible to see two different curves on this graph, the first one, stable between 50 and 20 days before the flight, and a positive monotone curve between 20 and 2 days before. A pattern is clearly visible in the way prices evolve depending on the days left.
The graph highlights how the prices rise slowly and then drastically start rising 20 days before the flight, but fall just one day before the flight up to three times cheaper. This can be explain by the fact the companies want to fill their empty seats and thus lower the prices of the tickets to ensure the planes remains full.
![image](https://user-images.githubusercontent.com/56116206/236880322-dc3f4f2c-3b12-4c77-8214-7371671bd40e.png)
<img width="256" alt="image" src="https://user-images.githubusercontent.com/56116206/236880679-4cd6a401-7b09-4e20-b27a-669040b4370c.png">





