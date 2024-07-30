# MySQL

MySQL is an opensource sequel database to store data inside a structured table. 

```
 Where to chose sequest or no-sequel database depends on the type of data, application and the useCase. It's purely developer driven.
 Version of the MySQL to be installed is also an input from the developer.
```

#### Install MySQL Server  ( Version 8.0.x : As per Developer's choice )

```
    # dnf install mysql-server -y

```

#### Restart Nginx Service to load the changes of the configuration.

```
    # systemctl enable mysqld 
    # systemctl start  mysqld           
```

#### Next, We need to change the default root password in order to start using the database service. Use password ExpenseApp@1 or any other as per your choice.

```
    # mysql_secure_installation --set-root-pass ExpenseApp@1

```

#### You can check the new password working or not using the following command in MySQL.

```
    # mysql -uroot -pExpenseApp@1

```


This installs and configured the backend.

!!!! It's always recommended to configure and set up your Database before your application comes up. If not application looks for the Database and app will fail. 

Once you're done, proceed with the `003-backend.md`
