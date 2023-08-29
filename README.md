# Customer Churning Analysis and Prediction

• Customer churn is a major problem faced by companies in the telecom industry, where customers have the freedom to switch to other companies to cater to their communication and internet needs.<br/>
• The churn rate, which represents the number of customers that cancel or do not renew their subscription with the company, directly affects the company's revenue. Therefore, it is crucial for companies to analyze and understand the factors that contribute to customer churn and build strategies to improve customer retention.<br/>
• In this study, we aim to classify potential churn customers based on numerical and categorical features using machine learning algorithms.<br/>
• We explore the use of K-means clustering for customer segmentation and logistic regression for churn prediction.We also perform data preprocessing techniques such as normalization, standardization, and data balancing to improve the performance of our models. We discuss our results and provide recommendations for companies to improve their customer retention strategies.<br/>

# Exploratory Data Analysis

## A. Dataset
The dataset used for this study is from IBM, published 5 years ago on Kaggle. The data attributes are as follows –
• customerID : Customer ID
• gender : Whether the customer is a male or a female
• SeniorCitizen : Whether the customer is a senior citizen or not (1, 0)
• Partner : Whether the customer has a partner or not (Yes, No)
• Dependents : Whether the customer has dependents or not (Yes, No)
• tenure : Number of months the customer has stayed with the company
• PhoneService : Whether the customer has a phone service or not (Yes, No)
• MultipleLines : Whether the customer has multiple lines or not (Yes, No, No phone service)
• InternetService : Customer’s internet service provider (DSL, Fiber optic, No)
• OnlineSecurity : Whether the customer has online security or not (Yes, No, No internet service)
• OnlineBackup : Whether the customer has online backup or not (Yes, No, No internet service)
• DeviceProtection : Whether the customer has device protection or not (Yes, No, No internet service)
• TechSupport : Whether the customer has tech support or not (Yes, No, No internet service)
• StreamingTV : Whether the customer has streaming TV or not (Yes, No, No internet service)
• StreamingMovies : Whether the customer has streaming movies or not (Yes, No, No internet service)
• Contract : The contract term of the customer (Month-to-month, One year, Two year)
• PaperlessBilling : Whether the customer has paperless billing or not (Yes, No)
• PaymentMethod : The customer’s payment method (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic))
• MonthlyCharges : The amount charged to the customer monthly
• TotalCharges : The total amount charged to the customer
• Churn : Whether the customer churned or not (Yes or No)
