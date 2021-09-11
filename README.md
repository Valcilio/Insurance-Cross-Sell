# HEALTH-CAR INSURANCES CROSS SELL

<img src="/home/valcilio/respos/heal_insu_class/github/heal-car.png" alt="Health-Car Insuranc" style="zoom:70%;" />

## **PREMISES:**

**Insurance All Company**

Our client is an Insurance company that has provided Health Insurance to its customers now they need your help in building a model to predict whether the policyholders (customers) from past year will also be interested in Vehicle Insurance provided by the company.

An insurance policy is an arrangement by which a company undertakes to provide a guarantee of compensation for specified loss, damage, illness, or death in return for the payment of a specified premium. A premium is a sum of money that the customer needs to pay regularly to an insurance company for this guarantee.

For example, you may pay a premium of Rs. 5000 each year for a health insurance cover of Rs. 200,000/- so that if, God forbid, you fall ill and need to be hospitalised in that year, the insurance provider company will bear the cost of hospitalisation etc. for upto Rs. 200,000. Now if you are wondering how can company bear such high hospitalisation cost when it charges a premium of only Rs. 5000/-, that is where the concept of probabilities comes in picture. For example, like you, there may be 100 customers who would be paying a premium of Rs. 5000 every year, but only a few of them (say 2-3) would get hospitalised that year and not everyone. This way everyone shares the risk of everyone else.

Just like medical insurance, there is vehicle insurance where every year customer needs to pay a premium of certain amount to insurance provider company so that in case of unfortunate accident by the vehicle, the insurance provider company will provide a compensation (called ‘sum assured’) to the customer.

**The Challenge**

Building a model to predict whether a customer would be interested in Vehicle Insurance is extremely helpful for the company because it can then accordingly plan its communication strategy to reach out to those customers and optimise its business model and revenue.

Now, in order to predict, whether the customer would be interested in Vehicle insurance, you have information about demographics (gender, age, region code type), Vehicles (Vehicle Age, Damage), Policy (Premium, sourcing channel) etc.

**Deliveriables:**

1. Main insights about the features more relevant from clients interesteds in purchase a car insurance.

2. What's the percentage of clients interesteds in purchase a car insurance, the sales team will be able to contact 10.000 customers?

3. If the capacity of the sales team growh up to 20.000 calls, which will be the percentage of clients interesteds in purchase a car insurance that the sales team will be able to contact?

4. How many call the sales team will need to do to contact 80% of the customers interests in purchase a car insurance?

5. What's the minimum score I need to address to get the greatest return?

## **Solution Plan:**

1. Clean the dataset
2. Derivate New Features
3. Analysis Dataset
4. Data FIltering
5. Prepare Data and Select Features
6. Machine Learning Modeling
7. Performance Interpretation

## **Technicals Reviews:**

The dataset originally has about 173909 rows and 12 columns. 

When analyzing the column types, some modifications were made from string to integer and no lines with NA were found, in addition to a statistical description, as in the image below. 

<img src="/home/valcilio/respos/heal_insu_class/github/technical/statistic.png" alt="Health-Car Insuranc" style="zoom:70%;" />

In the feature engineering part, initially a study was carried out on the features to understand which features it would be possible to derive and later four features were due (see image below) that helped in the analysis of the data later.

<img src="/home/valcilio/respos/heal_insu_class/github/technical/feature_engineering.png" alt="Health-Car Insuranc" style="zoom:70%;" />

In the exploratory data analysis part, some important analyzes were performed. The distributions were checked and all of them are far from a normal one, while it was possible to obtain 3 relevant insights for the business I separeted some features to the model after.

After that, the data preparation was made with this metodology:

<img src="/home/valcilio/respos/heal_insu_class/github/technical/data_preparation.png" alt="Health-Car Insuranc" style="zoom:70%;" />

In the feature selection was used the Random Forest Feature Importance's Technique and Boruta, after that I mescled with my manual select and the result is below:

<img src="/home/valcilio/respos/heal_insu_class/github/technical/cols_selected.png" alt="Health-Car Insuranc" style="zoom:70%;" />

The models that I tested were XGBoost, LGBM, Naive Bayes and Random Forest, to implement some different techniques the performances are in the image.

<img src="/home/valcilio/respos/heal_insu_class/github/technical/models_perf.png" alt="Health-Car Insuranc" style="zoom:70%;" />

After that, was made a cross validation to check the real performance of these models in this problem, check below the cross validation performances:

<img src="/home/valcilio/respos/heal_insu_class/github/technical/cross_val.png" alt="Health-Car Insuranc" style="zoom:70%;" />

Was chosed to follow with the LGBMClassifier because this model has a better performance mean between the ROC AUC Score and the Top K Score. Then, was made the fine tuning with the random search and used the cumulative gains curve to check the results from the model in the dataset of test.

<img src="/home/valcilio/respos/heal_insu_class/github/technical/cum_gains.png" alt="Health-Car Insuranc" style="zoom:70%;" />

With this plot is possible to see the maximum of this sample that need to be used to get the best result is around 58% of the sample dataset. and with the lift curve below is possible to see that the model perform aroun twice better than a mean model.

<img src="/home/valcilio/respos/heal_insu_class/github/technical/lift_curv.png" alt="Health-Car Insuranc" style="zoom:70%;" />

In final, was made the deployment of the model through the Heroku with a API created to this model and after using the google sheets to call the results from this API and put it in production.

## **Business Questions:**

***1 - Main insights about the features more relevant from clients interesteds in purchase a car insurance.***

1. people with vehicles with a age less than 2 have more chance to purchase a car insurance.
2. People with vehicles with annual premiums lower than 41.000 have more chance to purchase a car insurance.
3. People associated to the company for less than 200 days have less chance to purchase a car insurance.

***2 - What's the percentage of clients interesteds in purchase a car insurance, if the sales team will be able to just contact 10.000 customers?***

The percentage will be approximately 62% of all the interested clients.

***3 - If the capacity of the sales team growh up to 20.000 calls, which will be the percentage of clients interesteds in purchase a car insurance that the sales team will be able to contact?***

The percentage will be approximately 99% of all the interested clients.

***4 - How many call the sales team will need to do to contact 80% of the customers interests in purchase a car insurance?***

The marketing team will call 80% of the interested customers if they call 13772 people.

***5. What's the minimum score I need to address to get the greatest return?***

The minimum score to call is 0.087 second the test dataset.

## **Business Improvement:**

***The business improvement used when implementing the insights are as follows:***

1. better organization in deciding which customers to approach.
2. savings with customers with low possibility of purchasing insurance.
3. better targeting of investments to carry out customer maintenance.
4. Improved sales team dynamics.

## **Next Steps**:

1. Arrange a meeting to explain the model's performance.
2. Set up a meeting with individual teams who will work directly with the model in production in order to instruct them on how to get the best out of it.
3. researching new features to improve the model, in addition to constantly retraining the model so that performance doesn't start to drop.

## **Conclusion:**

Finally, this model was able to properly achieve its main objective, which was to rank the customers and indicate what's the percentage of samples that need to be used to archive the greatest financial return in the sales team.

## Learnings:

In this project, I was able to learn about Ranking metrics like Top K Score and also general ranking metrics like ROC AUC Score, besides also learning a new functionality of the models which is "predict_proba" and also learning on the cumulative gain and lift curves. I feel this project was very enriching for me.