# MySQL

MySQL is an opensource sequel database to store data inside a structured table. 

```
 Where to chose sequest or no-sequel database depends on the type of data, application and the useCase. It's purely developer driven.
 Version of the MySQL to be installed is also an input from the developer.
```

CentOS-8 Comes with MySQL 8 Version by default, However our application needs MySQL 5.7. So lets disable MySQL 8 version

```
    # dnf module disable mysql -y 
```

#### Setup the MySQL5.7 repo file

```
    # vim /etc/yum.repos.d/mysql.repo   ( and add the below repo details and this defines from where mysql has to be downloaded )

    [mysql]
    name=MySQL 5.7 Community Server
    baseurl=http://repo.mysql.com/yum/mysql-5.7-community/el/7/$basearch/
    enabled=1
    gpgcheck=0
```

#### Install MySQL Server 

```
    # dnf install mysql-community-server -y

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