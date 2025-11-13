In this activity, you will download and set up a Postgres database on your local machine. You are advised to revisit this activity once you feel comfortable with running complex SQL queries in Postgres DB in a cloud.

Note

This is quite a technical topic. Most of the time, you work with data that are already in a database that was created by someone else, and you are not required to set up your own database. However, it might come in handy to know a bit more about the installation process and some basic rules of how to set it up. This activity will lead you through that process.

### Step 1: Download PostgreSQL

#### For Windows Users Only

Instruction

Follow the instructions in [**this article**](https://www.postgresqltutorial.com/postgresql-getting-started/install-postgresql/) to install Postgres on your machine. It is recommended to choose the newest version that is available for your OS.

Warning

You need to carefully select the right version for your OS. In the article, they selected the version for 32-bit Windows even though, nowadays, most of the Windows OS is 64-bit.

#### For MacOS and Linux Users Only

Instruction

Follow the instructions in [**this article**](https://www.postgresqltutorial.com/postgresql-getting-started/install-postgresql-macos/) to install Postgres on your machine. It is recommended to choose the newest version that is available for your OS.

Note

In the download process, you will have installed pgAdmin. This is a RDBMS for PostgreSQL and will be using it in several activities throughout this course.

### Step 2: Testing Postgres Installation and Setting Up User

Open the SQL Shell application downloaded in Step 1. Once you do that, you should see the following:

![initial shell](https://i.imgur.com/9bKzQUs.png)

Press ENTER to accept the default server. You should now see the following:

![accepting default servier](https://i.imgur.com/qHrruLf.png)

Press ENTER to accept the default database. You should now see the following:

![accepting default database](https://i.imgur.com/vSZB5yt.png)

Press ENTER to accept the default port. You should now see the following:

![accepting default port](https://i.imgur.com/1JT9Cmo.png)

Press ENTER to accept the default username. You should now see the following:

![accepting default username](https://i.imgur.com/cMaVFN4.png)

Press ENTER to accept the default password for the default user, or you can specify a password for the default user.

At the end of the process, your screen should look something like this:

![final screeen](https://i.imgur.com/AZlh4ZY.png)

### Step 3: Create Northwind Database on Your Machine

You are finally able to create the well-known sample database, the Northwind database. Northwind is a well-known sample database which you will use throughout this course. To do this, first download the [database zip file](https://drive.google.com/file/d/1TxFI9zTKM5L7XNfrEQ9LB2kgLChjAeAj/view?usp=sharing).

Then, follow the instructions in this video to build the Northwind database on your machine using pgAdmin:

## Conclusion

Now that you have installed the Northwind database on your machine, you will use it throughout the course to practice a variety of SQL queries.

---