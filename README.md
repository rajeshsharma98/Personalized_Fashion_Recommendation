# H\&M Personalized Fashion Recommendation  
[Project Report](https://open.substack.com/pub/rajeshsharma98/p/h-and-m-personalized-fashion-recommendation?r=319f8m&utm_campaign=post&utm_medium=web)  

### Code Files:  
- Articles (articles-data.ipynb)  
- Customers (customer-data.ipynb)  
- Transaction (transcation-data-eda.ipynb)  
- Aprori recommendation (recommendation.ipynb)  
- Clustering recommendation (clustering.ipynb)    
All code file are Ipython files and can be opened in jupyter environment or kaggle/colab environments.  

### [Dataset](https://www.kaggle.com/competitions/h-and-m-personalized-fashion-recommendations/data)  

## Abstract  
The H&M Group is a collection of brands and companies with about 4,850 physical stores and 53 online marketplaces. Online retailers provide customers with a wide range of products to browse. With too many alternatives, buyers might not immediately locate what they want or what intrigues them, which might discourage them from making a purchase. To enhance the purchasing experience, product recommendations are crucial. More significantly, helping customers make wise decisions improves sustainability because doing so reduces costs and, consequently, emissions associated with transportation. Based on information from historical transactions, as well as from customer and product meta data, we aim to offer our customers personalized fashion recommendations tailored specifically to their preferences.  

## Introduction  
H&M is a very popular Swedish clothing company with headquarters in Stockholm. The company was founded in 1947 and was originally named Hennes. In 1968, they acquired the hunting from this point, it operated under Hennes & Maurtiz or simply H&M. In 2000, they entered the US market. As of 2022 it operates shops in 74 countries:  

Our work aims to provide H&M's customers with unique fashion recommendations based on their purchase history from 2018-2020, along with supporting metadata. We were motivated to work on this project because it would provide each customer with a personalized suggestion to enhance their shopping experience, reduce shopping time, and increase business sales. We attempted to suggest articles to customers using the findings of our analysis, rules for associations between articles, and data clustering based on age groups.  
 
## Data Description and Pre-Processing  
The datasets used are from one of the kaggle competitions[1]. The dataset is divided into three sub-parts: articles metadata, customers metadata and transaction data. The article's metadata consists of 25 features and 105k rows. This dataset is further divided into categories based on color, product type, gender etc.On examining the datatype of each column, 11 features contain numerical data and 14 features contain categorical data. On further scrutinizing the data based on the columns, we figured that the numerical columns could also be expressed as categorical types but with numeric labels and using which we can claim the data duplicacy in the columns. Data duplicacy is removed by dropping the columns and new preprocessed data has only 18 columns. The customer's metadata consists of 7 features and 1.3M rows and contains information about their club membership status, postal codes, age, etc., which helps us analyze buyer’s purchasing behavior. Based on the age range of the customers we tried to create groups using unsupervised algorithms. The transaction dataset was one of the biggest dataset with 31M rows and 5 columns. First, in order to load the data into the Kaggle kernel we had to use the Kaggle’s P500 GPU along with the cudf library which uses GPU clusters in order to load the chunks of dataset into memory. In addition we have to perform the following preprocessing steps in order to reduce the disk space occupied: Converting article_id & customer_id into int32 type from char type, by defining appropriate types pandas reduces the space occupied by the columns. Filtering out the year 2020 from the rest of the data as taking the most recent year for analysis would have a higher impact on the results. Converting the dataset file from .csv to .parquet which takes smaller disk space and the read-time is lesser for parquet files.
