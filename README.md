# Customer Churning Analysis and Prediction

• Customer churn is a major problem faced by companies in the telecom industry, where customers have the freedom to switch to other companies to cater to their communication and internet needs.<br/>
• The churn rate, which represents the number of customers that cancel or do not renew their subscription with the company, directly affects the company's revenue. Therefore, it is crucial for companies to analyze and understand the factors that contribute to customer churn and build strategies to improve customer retention.<br/>
• In this study, we aim to classify potential churn customers based on numerical and categorical features using machine learning algorithms.<br/>
• We explore the use of K-means clustering for customer segmentation and logistic regression for churn prediction.We also perform data preprocessing techniques such as normalization, standardization, and data balancing to improve the performance of our models. We discuss our results and provide recommendations for companies to improve their customer retention strategies.<br/>

# Exploratory Data Analysis

## A. Dataset
The dataset used for this study is from IBM, published 5 years ago on Kaggle. The data attributes are as follows –
• customerID : Customer ID.<br/>
• gender : Whether the customer is a male or a female.<br/>
• SeniorCitizen : Whether the customer is a senior citizen or not (1, 0).<br/>
• Partner : Whether the customer has a partner or not (Yes, No).<br/>
• Dependents : Whether the customer has dependents or not (Yes, No).<br/>
• tenure : Number of months the customer has stayed with the company.<br/>
• PhoneService : Whether the customer has a phone service or not (Yes, No).<br/>
• MultipleLines : Whether the customer has multiple lines or not (Yes, No, No phone service).<br/>
• InternetService : Customer’s internet service provider (DSL, Fiber optic, No).<br/>
• OnlineSecurity : Whether the customer has online security or not (Yes, No, No internet service).<br/>
• OnlineBackup : Whether the customer has online backup or not (Yes, No, No internet service).<br/>
• DeviceProtection : Whether the customer has device protection or not (Yes, No, No internet service).<br/>
• TechSupport : Whether the customer has tech support or not (Yes, No, No internet service).<br/>
• StreamingTV : Whether the customer has streaming TV or not (Yes, No, No internet service).<br/>
• StreamingMovies : Whether the customer has streaming movies or not (Yes, No, No internet service).<br/>
• Contract : The contract term of the customer (Month-to-month, One year, Two year).<br/>
• PaperlessBilling : Whether the customer has paperless billing or not (Yes, No).<br/>
• PaymentMethod : The customer’s payment method (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic)).<br/>
• MonthlyCharges : The amount charged to the customer monthly.<br/>
• TotalCharges : The total amount charged to the customer.<br/>
• Churn : Whether the customer churned or not (Yes or No).<br/>

The dataset consists of 7043 records. Out of the 21 attributes present, customerID is dropped since it has no real use for this study. Only three numerical columns namely tenure, MonthlyCharges, TotalCharges are present. The rest of the data attributes are categorical. TotalCharges has 11 missing values and these records were dropped. The categorical values are transformed into numerical values using LabelEncoder from sklearn.preprocessing.<br/>

For visualization purposes, we have divided the features into 3 groups.<br/>
• Customer Information – gender, Senior Citizen, Partner, Dependents.<br/>
• Services Signed up for – PhoneService, MultipleLines, InternetService, StreamingTV, StreamingMovies, OnlineSecurity, OnlineBackup, DeviceProtection, TechSupport.<br/>
• Payment Information – PaymentMethod, Contract, PaperlessBilling.<br/>

## B. Target Variable Visualization (Churn)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/e1f23830-1704-4523-9371-fb852706e043)
The target variable is “Churn” which takes 0 & 1 which  results in a binary classification problem and the dataset is unbalanced in a near about 3 : 1 ratio for Not-Churn: Churn customers.<br/>

## C. Categorical Features vs Target Variable (Churn)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/2a838ad8-cbe6-4083-ad7a-c33e4eaccc0a)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/09f04ed9-d9f9-4174-9f1d-9623d3700dfc)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/81dabcf9-a864-45b7-91d2-c676ee315c17)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/73e7fbde-95fe-4678-a489-bcc846763cd2)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/bb9bc32e-4d52-4525-9631-356c8d13be3b)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/d79c53e8-63fc-4e6f-8245-5dbdd9e65ea8)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/020b670e-1fe7-4bb8-9a67-79e562623b02)

Some of the Inferences Obtained –<br/>
• Customer churning for male & female customers is very similar to each other<br/>
• Similarly, number of SeniorCitizen customers is pretty low! Out of that, nearly about 40% of churn are SeniorCitizen customers.<br/>
• Customers who are housing with a Partner churned less as compared to those not living with a Partner.<br/>
• Similarly, churning is high for customers that don't have Dependents with them.<br/>
• For PhoneService, despite having no phone service, more customers were retained as compared to the number of customers who dropped the services.<br/>
• A high number of customers have displayed their resistance towards the use of Fiber optic cables for providing the InternetService. On the contrary, from the above graph, customers prefer using DSL for their InternetService!<br/>
• StreamingTV and StreamingMovies display an identical graph. Irrespective of being subscribed to StreamingTV & StreamingMovies, a lot of customers have been churned.<br/>

## D. Categorical Features vs Positive Target Variable
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/c231fce6-8905-42a8-939b-1865722b23a3)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/639eebf6-5fa7-4d47-9f21-a762b097277e)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/91d0871a-2b98-49fd-a9f7-27afacaa6b81)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/5ce24a04-0a5b-4e72-bdcb-a1e6b71cc223)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/915e03d4-23a6-41a4-9292-5cc3fcb46f22)

Some of the Inferences obtained –<br/>
• We can observe a clear-cut 50% - 50% split between the male and female customers that have switched their services. Hence, the reason for switching is something related to the service or some process to which the customers reacted badly.<br/>
• 75% of the churned customers are not SeniorCitizen.<br/>
• Customers living by themselves have cut off the services. From Partners & Dependents data, an average of 73.4% of customers churned out were living by themselves.<br/>
• Despite providing PhoneService, a high percentage of customers have switched.<br/>
• Similarly, the availability of MultipleLines did not matter, as customer unsubscription was carried out regardless.<br/>
• Customers did not like the approach of Fiber Optic cables for providing InternetService with 70% opting out of the services.<br/>
• For StreamingTV & StreamingMovies, customers without these services definitely canceled their subscriptions, however, an average of 43.7% of customers switched despite consuming the streaming content.<br/>
• Month-to-Month Contract duration has the dominating share when it comes to churning with 88.6% of customers!<br/>
• PaperlessBilling does not seem to be liked by the customers.<br/>

## E. Numerical Features Distribution

![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/b6ff39cf-a07c-4102-bbe5-c7ea7726d874)
Tenure and MonthlyCharges create a bimodal distribution with peaks present at 0 - 70 and 20 - 80 respectively. TotalCharges displays a positively or rightly skewed distribution.<br/>

## F. Numerical Features vs Target Variable
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/0b227156-1adb-4203-b2cd-d45dfc8445f2)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/00ec1714-d989-43ce-8e6c-b36e4a65f78a)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/abf6b250-af38-479d-822e-22b0200c45f8)

Inferences obtained –<br/>
• Considering tenure, a high number of customers have left after the 1st month. This high cancellation of services continues for 4 - 5 months but the churn of customers hasreduced since the 1st month. As the tenure increases, customers dropping out decreases.<br/>
• This results in low customer churning as the tenure increases.<br/>
• For the MonthlyCharges group, the churn rate is high for the values between 65 (13x5) - 105 (21x5). This MonthlyCharges range of values caused the customers to switch.<br/>
• A very high number of customers opted out of the services for the TotalCharges below 500. This customer churning continues for a TotalCharges range of values from 0 (0x500) - 1000 (2x500).<br/>

## G. Outliers
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/b5b7ceac-e305-4c0c-99aa-1140e7b7a03f)
There are no outliers in the data.<br/>





















