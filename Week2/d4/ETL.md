## ETL (Extract, Transform, Load)

ETL, which stands for extract, transform and load, is a data integration process that combines data from multiple data sources into a single, consistent data store that is loaded into a data warehouse or another target system. You can read more about data warehouses in [this article](https://www.ibm.com/cloud/learn/data-warehouse) by IBM.

As databases grew in popularity in the 1970s, ETL was introduced as a process for integrating and loading data for computation and analysis, eventually becoming the primary method to process data for data warehousing projects.

ETL provides the foundation for data analytics workstreams. The workflow could depend on the industry you’re working in, as well as the ideal state you need the data to be in and how far the data is from that ideal state. To enforce the workflow required, a set of business rules are created and through this series of rules, ETL cleanses and organizes data in a way which addresses specific business intelligence needs, like monthly reporting. However, it can also be used to tackle more advanced analytics, which can improve back-end processes or end-user experiences. ETL is often used by an organization to:

- Extract data from legacy systems
- Cleanse the data to improve data quality and establish consistency
- Load data into a target database

It may be helpful to visualize this process as follows:

|![Diagram showing the different source files that data can be extracted formed, then transformed and then loaded into a data warehouse](https://i.imgur.com/crUuOns.png)|
|---|
|**Image Credits - [https://www.edureka.co/blog/videos/informatica-capabilities-as-an-etl-tool/](https://www.edureka.co/blog/videos/informatica-capabilities-as-an-etl-tool/)**|

The easiest way to understand how ETL works is to understand what happens in each step of the process.

### Extract

During data extraction, raw data is copied or exported from source locations to a staging area. Data management teams can extract data from a variety of data sources, which can be structured or unstructured. Those sources include but are not limited to:

- SQL or [NoSQL](https://www.ibm.com/cloud/learn/nosql-databases) servers
- CRM and ERP systems
- Flat files
- Email
- Web pages

### Transform

In the staging area, the raw data undergoes data processing. Here, the data is transformed and consolidated for its intended analytical use case. This phase can involve the following tasks:

- Filtering, cleansing, de-duplicating, validating, and authenticating the data
- Performing calculations, translations, or summarizing based on the raw data. This can include changing row and column headers for consistency, converting currencies or other units of measurement, editing text strings, and more.
- Conducting audits to ensure data quality and compliance
- Removing, encrypting, or protecting data governed by industry or governmental regulators
- Formatting the data into tables or joined tables to match the schema of the target data warehouse

### Load

In this last step, the transformed data is moved from the staging area into a target data warehouse. Typically, this involves an initial loading of all data, followed by periodic loading of incremental data changes and, less often, full refreshes to erase and replace data in the warehouse. For most organizations that use ETL, the process is automated, well-defined, continuous and batch-driven. Typically, ETL takes place during off-hours when traffic on the source systems and the data warehouse is at its lowest.

You can read more about the ETL process in [this piece by Microsoft](https://docs.microsoft.com/en-us/azure/architecture/data-guide/relational-data/etl).