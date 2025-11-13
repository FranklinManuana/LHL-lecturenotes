## Normalization of Relational Database

When developing a relational database, the real-world information needs to be represented in a model that captures the information such that it can be modified and reused. A relational model allows for exactly that.

Here is the process to go through when building a relational model:

|**Steps**|**Expected Output**|
|---|---|
|Step 1: Capture the needs|Problem statement|
|Step 2: Elaboration of the conceptual model|Description of functional dependencies and relationships|
|Step 3: Design of the logical model|Data structure diagram|
|Step 4: Elaboration of the physical model|Physical model ready for implementation|

Consider the following scenario:

Last week you attended an out of town professional development event designed for data professionals. You attended several workshops and got to meet with the presenters and fellow attendees.

Back in your hotel room, you notice you’ve collected a nice stack of business cards, including ones from the following conference attendees:

- Dennis Iverson, Data Engineer at Geek Tech
- Lei Jen, Sr. Data Scientist at Cyber Scene
- Milena Gerasimova, CEO at Northeast Data
- Dawit Tesfay, CTO Mass Analysis
- Cindy Pham, Jr. Data Analyst SunValley Food
- Giselle Tirado, Data Scientist, Cyber Scene

To avoid losing the cards and the possible networking opportunities, you decide to transcribe all the information collected in an Excel file.

In fact, you need to set up a relational model that captures the valuable information in the business cards. You will now walk through the steps of this process as defined above.

### Step 1: Capture the Needs

In this first step, you need to capture the valuable information in the business cards. The information on each business card is quite standard so you define a contact entity:

#### The Problem

This modelling (conception, design, data model) has some shortcomings:

- There is redundancy
- There are **anomalies of bad design** (insertion, modification, deletion)

Now take a closer look at these shortcomings.

##### Redundancy

Since you collected cards from two employees of Cyber Scene, the company and its address will be captured more than one time (this is a duplicate). The implications of duplication include:

- Disk space is used inefficiently (for a database of several million records, this will be problematic).
- Confusion can quickly arise if ever the two Cyber Scene addresses diverge. What would be the truth?
- Since data redundancy quickly becomes a disaster, you can lose confidence in the data.

##### Anomalies of Bad Design

###### Insert Anomaly

An insertion anomaly happens when certain entities cannot be added to a database without including other entities. For example, suppose you came across a business card in your stack that only had the company information and not the individual’s information. You might want to capture this company’s phone number and email address to connect with their HR department, but you cannot since your current entity setup requires contact information.

In general, to avoid insertion anomalies, you need to:

- Create entities without the constraints of other entities.
- Create information correctly (i.e., an email address without the @ would be an insertion anomaly).
- Be consistent in the defined values of the same attribute (i.e., US, USA, United States of America is not consistent).
- Avoid missing values or values in the wrong format.

###### Modification Anomaly

A modification anomaly occurs when changing a single value of an attribute involves modifying multiple records. For example, Lei Jen informs us that Cyber Scene is changing addresses. You could update the address for Lei Jen, but then you would also have to update the address for Giselle Tirado. It would be better if you could make this update in a single place and have it flow through to the relevant entities.

###### Deletion Anomaly

A deletion anomaly occurs when deleting a record to reflect the disappearance of an entity and may involve the loss of information from another entity. For example, suppose one of the companies in your database goes bankrupt. You could delete all of the contacts who work at that company or you could go through every contact, one by one, and delete the company information. Neither scenario is ideal.

#### The Solution

To avoid redundancy and anomalies of bad design, you will need to define a set of relationships that correctly represents the domain without losing information and in an optimal way (without duplicating the information).

The idea is to **normalize** the huge entity by breaking it down into several small entities that contain the same information to prevent update anomalies and data inconsistencies.

There are tools that can be used to apply a solution:

- Functional dependencies (A → B)
- Normal forms

### Step 2: Elaboration of the Conceptual Model

What you need to produce in this step are **functional dependencies**.

Functional dependencies express the relationship **between** attributes. It is based on the real-world data that’s being captured. There is a functional dependency of single-valued attribute A towards attribute B. In other words, A determines B so B depends on A.

Functional dependencies only exist when the information involved has **unique and singular identifiers**. For example, suppose a contact’s address is a single-valued fact because a contact has only one address. If you don’t provide unique identifiers for contacts, then there won’t be a functional dependency in the data.

|Contact|Contact Address|
|---|---|
|Lei Jen|123 Main St., New York|
|Lei Jen|321 Center St., San Fransisco|

Although each contact has a unique address, a given contact could have several different addresses. Hence, you would not have a functional dependency corresponding to the single-valued fact.

Similarly, the address has to be written identically in each occurrence in order to have a functional dependency. The following example prevents you from having a functional dependency.

|Contact|Contact Address|
|---|---|
|Lei Jen|123 Main St., New York|
|Lei Jen|123 Main Street, NYC|

Consider the following contact list: Contact( Contact Name, Company Name, Contact Position, Company Address, Contact Email, Contact Phone, Contact Phone Mobile Company Phone, Company Fax, Company Website )

Consider the following possible relationships:

- {Contact Name} → {Contact Position}
    - This is a good functional dependency because the contact name will tell you the contact’s position, but having the position won’t tell you the contact’s name as there could be many people in your database with the same position.
- {Company Address} → {Company Name}
    - This is a good functional dependency because the company address will only map to a single company name.
- {Company Address} → {Contact Name}
    - This cannot be a functional dependency because the contact name is not dependent on the company address.

Once you have set up your functional dependencies, you can synthesize relations (tables) such that they have normalized relationships, or in other words, are in normal form.

Tables are in normal form when they satisfy a set of criteria and rules which are expressed, among other things, using functional dependencies. They represent guidelines for **record design**.

A normalized relationship will have the advantage of not having anomalies. There are several levels of normalization and each higher level has a lower level as a prerequisite. The 3NF provides an acceptable design in most cases.

![Normal Forms](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/1.+Databases+and+their+Language/normal_forms.PNG)

Review the different levels of normalization outlined in the above diagram.

##### 1NF - “The key, …”

**Definition**: there is a **key** and any attribute must contain **only atomic values** (i.e., values that cannot be broken down into parts). In other words, you can uniquely identify records and not put more than one piece of information in a given attribute record. To satisfy 1NF, you need a key that uniquely identifies each record with only atomic values. For example, make sure to have only one phone number in the same attribute by record.

The key in the Contact entity is defined by: {Contact Name, Company Name}.

Steps to take to get atomic values:

- Split the Contact Name attribute into _ContactFirstName_ and _ContactLastName_
- Split the Company Name attribute into _Address_, _ZipCode_, _City_, _Region_, and _Country_

![1NF](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/1.+Databases+and+their+Language/1NF.PNG)

Once in 1NF, for any record, it is possible to retrieve all values of non-key attributes from the key {Contact FirstName, Contact LastName, Company Name}. Also, all values are now **atomic**. Despite that, the problems of anomalies persist in 1NF.

##### 2NF - “The key, the whole key…”

**Definition**: must be in 1NF. 2NF is violated when a non-key attribute is a fact of a subset of the key. There can only be 2NF when the key is made up of several attributes. To satisfy 2NF, since there will necessarily be more than one entity in the relationship, it will therefore be a question of creating another relation containing the subset of the key and the attributes which depend on this subset of the key.

The key in the Contact entity is defined by: {Contact FirstName, Contact LastName, Company Name}

The attributes Company Address, Company City, Company Region, Company ZipCode, Company Country, Company Phone, Company Fax, Company Website would depend on **the subset** {Company Name} and the **key** {Contact FirstName, Contact LastName, Company Name}.

To obtain 2NF, it will therefore be necessary to create a Company entity containing this information.

![2NF](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/1.+Databases+and+their+Language/2NF.PNG)

There is now one entity related to the contact and one related to the company. The detailed information related to the company is now in the Company entity, so it is not necessary to have information about the company linked to the contact in the Contact entity. Therefore, there is a **reduction of redundancy**.

#### 3NF - “The key, the whole key, and nothing but the key.”

**Definition**: must be in 2NF. 3NF is violated when a non-key attribute is a fact of another non-key attribute. To satisfy 3NF, you must create a relationship for this attribute (or set of attributes) and a **key to make the link**. In other words, you must evaluate if an attribute (or set of attributes) not considered as a **primary key** has functional dependencies with other attributes which are not keys. If a functional dependency exists, you need to split the entity to isolate the attributes by creating another entity.

The Contact entity is already in 3NF because there aren’t functional dependencies. The Company entity contains functional dependencies so it is in 2NF but not in 3NF yet.

- Company Name → City → Region: If the company is located in a city and that city is located in a region, then the company is located in that region.
- Company Name → Region → Country: If the company is located in a region and that region is located in a country, then the company is located in that country.

To obtain 3NF for the Company entity, it will be necessary to create Region and Country entities.

![3NF](https://learningimages.lighthouselabs.ca/Data+BC/Transforming+and+Analyzing+Data+with+SQL/1.+Databases+and+their+Language/3NF.PNG)

## Conclusion

It is important to always keep in mind that the model will evolve, so you should build it with maximum flexibility at the start with respect to third normal form as the standard. The normalized design enhances the integrity of the data, by minimizing redundancy and inconsistency.

---