it
### Frontend 

Expense App Frontend or UI is developed by using React and has to be deployed by using a web-server `Nginx`


#### Who decides the type of Web-Server to be used ?
```
    In our case, we selected to use nginx and it's also the suggested entity from Developer.
    Nginx is also one of the highly used Web-Server 

```

Nginx will have the webframe for the web application. 

Our application servers static content and we need a web server to perform the same:

#### Install Nging On The Top Of The Server-01

```
    # dnf install nginx -y  

    [ Hint : dnf is the package manager on RHEL9 ]
```

#### Start & Enable Nginx service 

```
    # systemctl enable nginx       [ Enabling the service will keep the service to be started automatically when server goes for a boot ]
    # systemctl start nginx 
```

!!! Try to access the service once over the browser and ensure you get some default content.

```
    1) Open your browser 
    2) IP Address 
    3) You should be able to see some default content and thus proves your nginx is working 
```

#### Remove the default content as we have our content developed and shared to us by the frontend developer 

```
    # rm -rf /usr/share/nginx/html/*          [ Nginx path where web content is stored ]

```


#### Download the web-content for frontend

```
    # curl -o /tmp/frontend.zip https://expense-web-app.s3.amazonaws.com/frontend.zip
```

#### Extract the frontend content.

```
    # cd /usr/share/nginx/html 
    # unzip /tmp/frontend.zip
```

!!! Try to access the nginx service once more over the browser and ensure you get expense content.


#### Create Nginx Reverse Proxy Configuration.

```
    # vim /etc/nginx/default.d/expense.conf   ( empty the file if any and add the below content )

proxy_http_version 1.1;

location /api/ { proxy_pass http://localhost:8080/; }

location /health {
stub_status on;
access_log off;
}
```

Above reverse proxy config plays a critical role and you'll get this more when detailing with backend.

!!! NOTE : Replace the localhost with the private ip address of your backend server. Word localhost is just used to avoid the failures on the Nginx Server.

### Restart Nginx Service to load the changes of the configuration.

```
    # systemctl restart nginx 
    # systemctl status nginx           ( service should show up as running, if not, you'd have made some mistakes above )
```


proceed with `002-mysql`
