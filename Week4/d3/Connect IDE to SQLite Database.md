We are going to guide you through the first steps of working with databases on your PC using VSCode. It's a powerful IDE that leverages different extensions to support many types of databases.

### SQLite

We will start with [SQLite](https://www.sqlite.org/index.html). **SQLite** is a great database for educational purposes because it is completely stored in one file on our local machine.

Instruction

Download the [sample SQLite databse](https://drive.google.com/file/d/0Bz9_0VdXvv9bWUtqM0NBYzhKZ3c/view?usp=sharing&resourcekey=0-7zGUhDz0APEfX58SA8UKog).

Our database consists of the following tables:

- Artists
- Albums
- Tracks
- Invoice_items
- Invoices
- Customers
- And some more...

We can see them in the database schema below:

![](https://i.imgur.com/KZhRhgk.jpg)

Now, we have everything ready to set up the connection. Let's start by installing SQLite extension in VSCode

1. Click on **Extensions Icon** in the left panel.  
    
2. Select the SQLite package from `alexcvzz`.  
    ![](https://i.postimg.cc/yxk3YnrY/Screenshot-2021-02-17-at-11-06-18.png)  
    
3. Open the folder where you downloaded the **chinook.db** database.  
    
4. Right-click on the db file and select `Open Database`. Note that your screen may not change at all after doing this, but you can still proceed.  
    ![](https://i.postimg.cc/HWVqXKRW/Screenshot-2021-02-25-at-09-28-34.png)  
    
5. Open a new empty file.  
    
6. You can see the type of the file in the bottom right corner. It should be `Plain Text` by default. Click on it in order to change it.  
    
7. Select `SQLite` and the type of the file will change.  
    ![](https://i.postimg.cc/VN7YLtrK/Screenshot-2021-02-25-at-09-30-45.png)  
    
8. In the bottom right corner, click on `SQLite: No database` to choose the database you want to work with.  
    
9. Choose `chinook.db`.  
    ![](https://i.postimg.cc/Wz0LrqzL/Screenshot-2021-02-25-at-09-30-58.png)  
    

Instruction

Test your connection by querying artists.

Note

In VSCode, the code is executed by right-clicking the query and choosing `Run Query`. However, we can easily change the shortcut we want to use to execute queries by following [this guide](https://code.visualstudio.com/docs/getstarted/keybindings).