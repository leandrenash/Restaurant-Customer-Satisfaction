This is a Kaggle Dataset

Restaurant Customer Satisfaction 

Overview Of Data
This dataset provides comprehensive information on customer visits to restaurants, 
including demographic details, visit-specific metrics, and customer satisfaction ratings. 
It is designed to facilitate predictive modeling and analytics in the hospitality industry, 
focusing on factors that drive customer satisfaction.

Features Of Data 

Demographic Information

 •	CustomerID: Unique identifier for each customer.

 •	Age: Age of the customer.

 •	Gender: Gender of the customer (Male/Female).

 •	Income: Annual income of the customer in USD.

Visit-specific Variables

 •	VisitFrequency: How often the customer visits the restaurant (Daily, Weekly, Monthly, Rarely).
 •	AverageSpend: Average amount spent by the customer per visit in USD.
 •	PreferredCuisine: The type of cuisine preferred by the customer (Italian, Chinese, Indian, Mexican, American).
 •	TimeOfVisit: The time of day the customer usually visits (Breakfast, Lunch, Dinner).
 •	GroupSize: Number of people in the customer's group during the visit.
 •	DiningOccasion: The occasion for dining (Casual, Business, Celebration).
 •	MealType: Type of meal (Dine-in, Takeaway).
 •	OnlineReservation: Whether the customer made an online reservation (0: No, 1: Yes).
 •	DeliveryOrder: Whether the customer ordered delivery (0: No, 1: Yes).
 •	LoyaltyProgramMember: Whether the customer is a member of the restaurant's loyalty program (0: No, 1: Yes).
 •	WaitTime: Average wait time for the customer in minutes.

Satisfaction Ratings

 •	ServiceRating: Customer's rating of the service (1 to 5).
 •	FoodRating: Customer's rating of the food (1 to 5).
 •	AmbianceRating: Customer's rating of the restaurant ambiance (1 to 5).

Target Variable

 •	HighSatisfaction: Binary variable indicating whether the customer is highly satisfied (1) or not (0). 

Potential Applications

 •	Predictive modeling of customer satisfaction.
 •	Analyzing factors that drive customer loyalty and satisfaction.
 •	Identifying key areas for improvement in service, food, and ambiance.
 •	Optimizing marketing strategies to attract and retain satisfied customers.
Usage

This dataset is ideal for data scientists and hospitality analysts looking to explore and model customer satisfaction in the restaurant industry. 
It can be used for machine learning projects, customer segmentation, and strategic planning.

The Goal 
The Aim of this process I took for this project was a simple approach I loaded and prepared the data. 
Then I performed some exploratory data analysis (EDA) to gain insights into the data. 
Then I started by checking for any missing values and then proceed with some basic statistical summaries and visualizations.

![image 1 ](https://github.com/leandrenash/Restaurant-Customer-Satisfaction/assets/73446394/92a5ab34-a38a-4166-9f3d-1d3b76aaeab7)


![image 2 ](https://github.com/leandrenash/Restaurant-Customer-Satisfaction/assets/73446394/14795689-b6a1-414b-af79-4a40090569a1)


 
I then proceeded with predictive modeling to predict customer satisfaction. I started  by preparing the data for modeling, 
including encoding categorical variables and splitting the data into training and testing sets.

Then I proceeded with the following steps for predictive modeling:

Data Preparation:

 •	Encoded categorical variables.
 •	Split the data into training and testing sets.

Model Training:

 •	Trained a machine learning model to predict customer satisfaction.

Model Evaluation:

 •	Evaluated the model's performance on the test set.



Data Preparation 

Basic preparations that included encode categorical variables, defined features and target variable and split the data into training and testing sets. 

The next step I looked at was training a machine learning model to predict customer satisfaction. Then I used a random forest classifier for this task.



Model Training 

I Achieve a model training and evaluation completed an accuracy : 86 
(0.8666666666666667)

Classification Report 

precision    recall  f1-score   support

           0       0.88      0.98      0.93       259
           1       0.56      0.12      0.20        41

    accuracy                           0.87       300
   macro avg       0.72      0.55      0.56       300
weighted avg       0.83      0.87      0.83       300



Classification Report 

precision    recall  f1-score   support

   0       0.88      0.98      0.93       259
   1       0.56      0.12      0.20        41

Accuracy: The model achieved an accuracy of approximately 86.67%.

Classification Report: The precision, recall, and F1-score for each class are provided in the classification report.


The model performs well in predicting customers who are not highly satisfied (class 0) but struggles with predicting highly satisfied customers (class 1). 
This could be due to class imbalance in the dataset.

To address the class imbalance and potentially improve the model’s performance, we can try the following approaches such as – 

Resampling Techniques:

   - Oversampling the minority class (e.g., using SMOTE).
   - Under sampling the majority class.

Adjusting Class Weights:

-	Modify the class weights in the Random Forest classifier to give more importance to the minority class.

So I applied SMOTE (Synthetic Minority Over-sampling Technique) to balance the classes and then retrain the model. 

After applying the SMOTE to balance the classes, I then retrained the RANDOM Forest classifier using the balanced dataset and evaluate its performance.

Model retraining and evaluation with SMOTE completed.
Accuracy: 0.7966666666666666
Classification Report:
              precision    recall  f1-score   support

           0       0.89      0.88      0.88       259
           1       0.27      0.29      0.28        41

    accuracy                           0.80       300
   macro avg       0.58      0.58      0.58       300
weighted avg       0.80      0.80      0.80       300

the model retaining and evaluation with SMOTE was completed and the accuracy resulted in 0.7966666666666666

after a rerun 

      precision    recall  f1-score   support

   0       0.89      0.88      0.88       259
   1       0.27      0.29      0.28        41

accuracy 0.80 300
macro avg 0.58 0.58 0.58 300
weighted avg 0.80 0.80 0.80 300

Accuracy: 
-	The model achieved an accuracy of approximately 79.67%.

Classification Report: 
-	The precision, recall, and F1-score for each class are provided in the classification report.

The model’s performance on the minority class (class 1) has improved in terms of recall and F1- Score. But  the overall accuracy has decreased slightly. 




The feature importance in the retrained Random Forest Model

The feature importance from the retrained Random Forest Model:

I create a Data-Frame for better visualization, sorted the data-frame by importance 

Feature Importance’s :

10              MealType    0.136687
0             CustomerID    0.123550
5           AverageSpend    0.107347
14              WaitTime    0.102012
3                 Income    0.086680
1                    Age    0.065489
7            TimeOfVisit    0.061664
8              GroupSize    0.061527
6       PreferredCuisine    0.046748
17        AmbianceRating    0.037726
16            FoodRating    0.035678
15         ServiceRating    0.033223
4         VisitFrequency    0.025120
9         DiningOccasion    0.020705
2                 Gender    0.018243
11     OnlineReservation    0.014469
12         DeliveryOrder    0.011634
13  LoyaltyProgramMember    0.011499

So the most Important features in predicting customer satisfaction are:

MealType
CustomerID
AverageSpend
WaitTime
Income

These features has the highest importance scores in the model.




Visualization in a bar chart - 

 ![image 3 ](https://github.com/leandrenash/Restaurant-Customer-Satisfaction/assets/73446394/2dc23ce9-99de-4359-ab3d-d5ba65745112)


This chart shows the relative importance of each feature in predicting customer satisfaction.
