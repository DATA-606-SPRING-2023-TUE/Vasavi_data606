# Final Proposal for my Capstone Project on Air Ticket Fare Prediction
## By: Vasavi Koonapalli

Presentation Slides for this project can be found here: https://docs.google.com/presentation/d/176He7YKPlOoeTY_zDSEQH142Jt32lEkQ/edit?usp=sharing&ouid=117012765111818748232&rtpof=true&sd=true

Presentation Video for this project can be found here: https://drive.google.com/file/d/162IQuIBpy3PH4fUD1sXVbaHp7Q54Fl8J/view?usp=sharing

## 1. Introduction
Booking cheap air tickets can vary in terms of hassle, depending on the individual's preferences, resources, and circumstances. Some factors that can affect the hassle of booking cheap air tickets include Research and comparison, getting hold of the correct timing of the travel that is economic, budget and ticket availability. Overall, the hassle of booking cheap air tickets can be reduced by being organized, flexible, and proactive in your approach. By doing research, staying on top of prices and promotions, and being willing to book in advance or make changes to your travel plans, you can increase your chances of finding the best deal on air tickets. Booking relatively cheaper air tickets has always been a thing on mind for me and with this project, I intend on doing this. 

In this project, I'll analyze and explore a dataset obtained from the "Ease My Trip" website, as well as run various statistical hypothesis tests to extract meaningful information. I am going to predict the price of the air tickets as accurately as possible. Since the price here is a numeric field, a regression model would be a great pick.

![image](https://user-images.githubusercontent.com/56116206/218330081-aa9144d6-bef0-40af-9fb1-9b723a388cf8.png)

## 2. Research Questions
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
When researched, I could not find any API that I could use to scrap data from Easemytrip website. I used python web scraping library - Beautiful Soup to gather data from their website. Also, I used a tool called Octoparse to extract some data aswell. The information was gathered in two parts: one for economy class tickets and one for business class tickets. The site yielded a total of 300261 distinct flight booking options. From February 11th to March 31st, 2022, data was gathered for 50 days. The data source was secondary data obtained from the Ease My Trip website.
The dataset contains flight booking options from the website Easemytrip for flights between India's top six metro cities. The cleaned dataset contains 300261 datapoints and 11 features.

_Link to the dataset_: https://docs.google.com/spreadsheets/d/1Bi_slUGz4cPL5Ng1QOYFTRh4t8d_w0ZulvKm9JVX5tU/edit?usp=sharing

## 4. Exploratory Data Analysis
When I performed some initial exploartory data analysis on the dataset, I found that the mean of the price is around 20,000 INR, while the median was around 7,500 INR. It was seen that only 2 airlines flew passengers in business class, while all the other airlines operated only Economy class. The price of the business class tickets was almost 6.5 times the price of the economy class ticket. 
AirAsia seems to have the cheapest flights when Air India and Vistara are more expensive. However it looks like Vistara's business tickets are a little more expensive than the Air India's ones. 
As expected, flights leaving early in the morning remained the cheapest way to travel. But it was also found that flights arriving early morning are also cheap and afternoon flights are a bit cheaper than morning and night flights. It was clear that the more stops there are, the more expensive the flight is, except for AirAsia where the prices seem more constant. 

We all know that the duration of flight has everything to do with the cost of the ticket. 
It is clear that, here the relationship is not linear but can be approximated with a second degree curve. The prices reaches a high price at a duration of 20 hours before lowering again.

<img width="679" alt="image" src="https://user-images.githubusercontent.com/56116206/236880009-59ab5dd6-cf55-4e1e-a85b-a030cc864696.png">

I then wanted to see how price is varying when I buy the ticket just 1 or 2 days before the departure. The regression graph here shows the graph for this. It is possible to see two different curves on this graph, the first one, stable between 50 and 20 days before the flight, and a positive monotone curve between 20 and 2 days before. A pattern is clearly visible in the way prices evolve depending on the days left.
The graph highlights how the prices rise slowly and then drastically start rising 20 days before the flight, but fall just one day before the flight up to three times cheaper. This can be explain by the fact the companies want to fill their empty seats and thus lower the prices of the tickets to ensure the planes remains full.

<img width="656" alt="image" src="https://user-images.githubusercontent.com/56116206/236880679-4cd6a401-7b09-4e20-b27a-669040b4370c.png">

## 5. Feature Selection
When it comes to feature selection, the first thing that comes to mind is the correlation matrix. The correlation is a good metric for linear relationship but doesn't highlight nonlinear ones. For that I will use mutual information. Mutual information is calculated between two variables and measures the reduction in uncertainty for one variable given a known value of the other variable. A quantity called mutual information measures the amount of information one can obtain from one random variable given another.

## 6. Machine Learning Models
Since my target variable-Price is a numerical variable, I decided to apply regression models to help predict better. The models I used to predict the price are Linear Regression, XGBRegressor, KNeighboursRegressor and CatBoostRegressor. The r2 score results of these models are as follows:

 <img width="182" alt="image" src="https://user-images.githubusercontent.com/56116206/236888430-b71804d8-0e37-4ff0-963a-d78bf6db6b00.png">


After looking at these results, I decided to try and improve the performance of the XGBRegressor model. 

## 7. Improving model Accuracy

I used Stacking and Blending method to try and improve the model performance. 
XGBRegressor giving best results may be explained by the fact some relationships are not linear like the duration or the days_left. Thus, a more flexible algorithm like XGBRegressor tends to give better results. For this, I used a technique called stacking and bending. 
In the essence, stacking makes prediction by using a meta-model trained from a pool of base models — the base models are first trained using training data and asked to give their prediction; a different meta model is then trained to use the outputs from base models to give the final prediction. The process is actually quite simple. To train a base model, K-fold cross validation technique is used.Blending is very similar to Stacking. It also uses base models to provide base predictions as new features and a new meta model is trained on the new features that gives the final prediction. The only difference is that training of the meta-model is applied on a separate holdout set (e.g 10% of train_data)rather on full and folded training set.
The first layers will composed with all the different regressor functions. And the final layer will be XGBRegressor since it gave the best results.

## 8. Result

<img width="314" alt="image" src="https://user-images.githubusercontent.com/56116206/236891757-661521d2-4bbc-45da-886b-2283727789c4.png">

## 9. Takeaway Points

1. The model that gives the best result is the XGBRegressor with on the test dataset an R^2 score equals to 0.9807 and a MAE score equals to 1688. However, when we use the stacking and bending method, we can reduce the MAE by more than 7% with 1580 and increase the R^2 score to 0.9821.
2. There is a big gap between flight tickets in business and economy. In average business tickets are 6.5 times more expensive than economy tickets.
3. Vistara and Air India seems to be the most expensive companies and AirAsia the cheapest. However, for business tickets, only Vistara and AirIndia are available, and Vistara is slightly more expensive.
4. In general, prices rise quite slowly until 20 days before the flight where the prices rise drastically. But one day before the flight, there usually are empty seats that have not been sold. Thus, it is possible to find tickets three times cheaper than the day before.
5. The longer the flight is the more expensive the tickets are until it reaches around 20 hours, then the prices tend to decrease.
6. For the time of the flight:
      It seems that departure during early morning is cheaper, and night more expensive.
       It seems that arrival during the early morning is cheaper.
7. In general, the more stops there are, the more expensive the flight ticket is.












