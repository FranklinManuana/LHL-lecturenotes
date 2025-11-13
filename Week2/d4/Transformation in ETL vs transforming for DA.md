Data transformation is a fundamentally important part of data analytics and you will perform various operations on data at almost every step of the way through any data analytics process. However, it's important to make the distinction between transforming data in ETL compared to transforming data during the data analysis process.

![etl_analysis](https://kajabi-storefronts-production.kajabi-cdn.com/kajabi-storefronts-production/blogs/2147485434/images/KCJGCytbRdukHeO1Ngla_ETL_2_.png "etl_analysis")

Source: [Amazon S3: Object storage built to retrieve any amount of data from anywhere](https://aws.amazon.com/s3/)

In the diagram above we can see the "transform" component of the ETL process as well as the "analytics" component at the end. Analytics itself could be made up of a huge number of processes, calculations, modelling, etc., as can be seen in the example image of a dashboard below.

![analytics](https://www.datapine.com/blog/wp-content/uploads/2020/10/big-data-in-healthcare-patient-dashboard.png "analytics")

Source: [ARE YOU READY TO UNLOCK THE FULL POTENTIAL OF YOUR DATA?](https://www.datapine.com/)

When we talk about transformation for ETL, we are referring to processes that are being performed to clean and format data so that it can be appropriately combined for loading into the data warehouse. Data extracted from each source may have different properties or formats that need to be resolved. For example, different units of measure may be used for concentration of a particular element in geoscience data (i.e., parts-per-million vs. grams per kilogram), or dates and times may be specified with different formats (i.e., 2023-03-29 vs. 03-29-2023). These types of transformations are being performed so that we have one continuous database with an expected format that we can then use for data analytics.

On the other hand, when we look at transformation in data analytics we are talking about the actual analysis of patterns, trends, prediction models, forecasting, etc. In that case we would be performing aggregation operations such as grouping and averaging, computing regression lines, extrapolating, building sophisticated machine learning models, and more. For example, we may want to look at the correlation between blood pressure and body mass index, or apply deep learning to predict stock prices next week.