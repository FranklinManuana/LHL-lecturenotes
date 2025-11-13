Read these two articles to explore Pandas vs. SQL

- [Pandas vs SQL - Compared with Examples](https://drive.google.com/file/d/15SAnOeWiQlPFcKgb-ZkaE8PQwWN0T-4m/view?usp=drive_link) by Towards Data Science
    
- [Pandas vs. SQL – Tools that Data Scientists use most often](https://www.dasca.org/world-of-big-data/article/pandas-vs-sql-tools-that-data-scientists-use-most-often) by Data Science Council of America
    

### Key Takeaways

- SQL is very efficient in handling large amounts of data. Pandas, on the other hand, can lag under large volumes.
- SQL works on a relational model which makes linking tables via keys much easier and regulates the entry of data in other tables in case of a foreign key constraint. Pandas JOIN function also helps us to join the data on the index and the MERGE function works like SQL which enables us to join on a particular column present in both the dataframes.
- Pandas has a lot more functionality to explore, clean and transform the data efficiently. Data wrangling and transformation using purely SQL is not as easy. In addition, with Python’s data visualization modules such as `matplotlib`, `seaborn`, `plotly`, etc., performing data visualizations in conjunction with EDA is easily done. With SQL, however, data visualization usually needs to be done by connecting to an external dashboard (such as Google’s Data Studio) or by using some BI tool (such as Tableau).

## Conclusion

Whether you should use Pandas or SQL in your work often depends on what you will be doing with the data once you have finished transforming it. Are you just doing a quick exploration of the data? Does the workload end in building a dashboard? If so, SQL might be the best tool to use if you are already reading the source data from a table in a database.

However, if your workflow will not stop there, and you will need to continue building a statistical or machine learning model, then Python (using Pandas) is the obvious choice.