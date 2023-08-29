# Customer Churning Analysis and Prediction

• Customer churn is a major problem faced by companies in the telecom industry, where customers have the freedom to switch to other companies to cater to their communication and internet needs.<br/>
• The churn rate, which represents the number of customers that cancel or do not renew their subscription with the company, directly affects the company's revenue. Therefore, it is crucial for companies to analyze and understand the factors that contribute to customer churn and build strategies to improve customer retention.<br/>
• In this study, we aim to classify potential churn customers based on numerical and categorical features using machine learning algorithms.<br/>
• We explore the use of K-means clustering for customer segmentation and logistic regression for churn prediction.We also perform data preprocessing techniques such as normalization, standardization, and data balancing to improve the performance of our models. We discuss our results and provide recommendations for companies to improve their customer retention strategies.<br/>

# EXPLORATORY DATA ANALYSIS

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

## H. Summary of EDA (exploratory data analysis)
exploratory data analysis (EDA) is an approach of analyzing data sets to summarize their main characteristics, often using statistical graphics and other data visualization methods.<br/>

### Order / Values of features for customer churn cases:

#### 1. Categorical Features (Order):
• gender : Male = Female<br/>
• SeniorCitizen : No SeniorCitizen > SeniorCitizen<br/>
• Partner : No Partner > Partner<br/>
• Dependents : No Dependent > Dependent<br/>
• PhoneService : PhoneService > No PhoneService<br/>
• MultipleLines : MultipleLines > No MultipleLines > No PhoneService<br/>
• InternetService : Fiber Optic > DSL > No InternetService<br/>
• OnlineSecurity : Absent > Present > No InternetService<br/>
• OnlineBackup : Absent > Present > No InternetService<br/>
• DeviceProtection : Absent > Present > No InternetService<br/>
• TechSupport : Absent > Present > No InternetService<br/>
• StreamingTV : Absent > Present > No InternetService<br/>
• StreamingMovies : Absent > Present > No InternetService<br/>
• Contract : Month-to-Month > One year > Two year<br/>
• PaperlessBilling : Present > Absent<br/>
• PaymentMethod : Electronic check > Mailed check > Bank Transfer (automatic) > Credit Card (automatic)<br/>

#### 2. Numerical Features (Range):
• tenure : 1 - 5 months<br/>
• MonthlyCharges : 65 - 105<br/>
• TotalCharges : 0 – 1000<br/>

# FEATURE ENGINEERING

## A. Data Transformation and Scaling
Since the numerical features are not distributed normally, we tried using many techniques to make them normal but only box-cox transformation has shown promising results only for TotalCharges. So, TotalCharges is transformed using the same and StandardScaler is used for standardizing the numerical features. <br/>
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/7ab595e5-e606-46df-a133-3448485f0149)

## B. Correlation Matrix
There’s no collinearity between the features observed. MultipleLines, PhoneService, gender, StreamingTV, StreamingMovies, and InternetService do not display any kind of correlation. Dropping the features with a correlation coefficient between (-0.1,0.1). Rest displays a significant positive or negative correlation.<br/>
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/48a40878-2f73-4eef-8e6d-d90034f8c5d6)

# MODELING & ANALYSIS OF RESULTS

## A. Linear Regression
• Linear regression assumes a linear relationship between the independent variables and the dependent variable, and the residual errors should be normally distributed with constant variance.<br/>
• However, in the given dataset, there are categorical variables, and the relationship between the independent variables and the dependent variable is not necessarily linear. Therefore, linear regression is not suitable for modeling this data.<br/>

## B. Logistic Regression
• Logistic regression can be used to predict the probability of churn for customers based on various features such as their tenure, monthly charges, and among others. Logistic regression is a binary classification algorithm that is used to model the relationship between a set of features and a binary target variable, in this case, whether a customer will churn or not.<br/>
• The logistic regression model will estimate the probability of churn based on the input features and output a binary value of 1 (churn) or 0 (not churn) for each customer. By setting a probability threshold, businesses can use the logistic regression model to identify the customers who are at high risk of churning and take proactive measures to retain them.Since the dataset is imbalanced in a 3:1 ratio for Not-Churn:Churn customers, the model may tend to predict the majority class more often and ignore the minority class. Class weights assign a higher weight to the minority class and a lower weight to the majority class, allowing the model to give more importance to the minority class during training. This can lead to a better performance of the model in predicting the minority class.<br/>
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/208b947d-f26d-402c-b39c-c14653d3c5e1)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/e5d06f6e-7b3f-4ec4-a7b4-45b6d19066e5)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/a22d7c67-e02e-4bce-9c25-4a254f79b671)
• Our Logistic Regression model has an accuracy of 0.74, a precision of 0.5 for the positive class, a recall of 0.78 for the positive class, and an F1-score of 0.61 for the positive class. These metrics indicate that the model is able to identify a high percentage of the churned customers, but it also misclassifies a significant number of non-churned customers as churned.However, the area under the ROC curve is 0.83, which indicates that the model performs well in terms of distinguishing between the positive and negative classes.<br/>

## C. K-Means Clustering
• K-means clustering is an unsupervised machine learning algorithm used to group similar data points together in a dataset. It tries to identify natural groupings in the data by minimizing the sum of squared distances between data points and their assigned cluster centroid. The algorithm works by randomly initializing k centroids, assigning data points to the nearest centroid, computing the new centroids based on the mean of the assigned data points, and repeating the process until convergence. The optimal number of clusters is typically determined through trial and error or using a statistical method.<br/>
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/0626a2cd-cbca-4315-9996-339999a103b9)
• From the graph, 4 is the optimal number of clusters for our data. After fitting the data for our 4 clusters, we obtained a similar number of data points in each cluster. Also, we can observe that 0 and 2 had a higher churn rate compared to Clusters 1 and 3.<br/>
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/8acf9feb-68f7-4e25-a362-a34ee587e5c0)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/e5fc9f0a-55df-4d99-9c75-dd0552824b1a)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/b553b991-c777-4939-8c06-a89a86825ef9)
![image](https://github.com/nayandeep20028840/Customer-Churning-Analysis-and-Prediction/assets/97220336/b2c9733b-71e4-43e8-84ac-ecc66fa0f12d)

We found out that customers in 0&2 are typically –<br/>
• Having shorter tenure than in other clusters<br/>
• In the Month-to-Month contract<br/>
• More Likely to be not elderly<br/>
• Uses Fiber Optic (cluster 2 customers also use DSL)<br/>
• Doesn’t have Online Security<br/>

Cluster analysis is helpful for placing customers into segments using data, which allows businesses to decide which segment(s) to target from distinct marketing mixes that will satisfy the needs and wants of each targeted Cluster. If we have a new customer we can easily determine which cluster he falls in and this can be used to customize plans for the customers. We can also use the clustering algorithm to cluster the data at different time intervals, and then compare the clusters to see if any customers have moved from one cluster to another.<br/>


# MEASURES FOR REDUCING CUSTOMER CHURN & INCREASE REVENUE

• 3 types of customers should be targeted : SeniorCitizen, Living with a Partner, living all alone.<br/>
• The number of SeniorCitizen customers is low but their lower-limit of MonthlyCharges is higher than the other customers. Thus, SeniorCitizen customers are ready to pay more money but they need to be catered with that level of service.<br/>
• In order to create a strong foundation of customers, Telco Company needs to create an easy and affordable entry point for their services. For the tenure of 1st 6 months, it needs to focus extensively on OnlineSecurity,OnlineBackup,DeviceProtection & TechSupport as this period is the most critical and uncertain for the customers.<br/>
• Once they build a solid support services for customers, they need to push the usage of MultipleLines & Fiber Optic cables for the PhoneService & InternetService respectively. Try to decrease the entry point at least after which prices can be increased.<br/>
• StreamingTV and StreamingMovies need to be made affordable. The content of these services should be targeting all types of customers. This needs to be followed up with an easy and hassle-freePaymentMethod.<br/>
• Put an end to the Electronic check for payment purposes due to it's high churn and focus entirely on Bank Transfer (automatic) & Credit Card (automatic)<br/>
• Once the MonthlyCharges for any single service hits the 70 mark, customers become very conscious about their MonthlyCharges. Make it low by providing offers for a certain period of time.<br/>

# CONCLUSION
• This is a great dataset that gives an opportunity to peak into the real-world business problem and can be dealt with the Data Science techniques.<br/>
• Insights gained from the Data Analysis are very valuable for understanding the effectiveness of the existing systems that are in place. They also assist in drawing up plans & measures to counter the problems or be in an infinite loop for improvement.<br/>
• We have successfully developed multiple models which help us in predicting the probability of customer churning (which helps telecom in acting) and by determining which cluster our customer falls in the 4 clusters formed which helps in the type of action plan required to prevent churning.<br/>







