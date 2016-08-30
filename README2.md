# LEMP
## Step one
Install MYSQL 

``` sudo apt-get install mysql-server php5-mysql```
Set the root password and make sure you remember it.
Next type in this 

```sudo /usr/bin/mysql_secure_installation```
Say yes to all the options that appear
Next install nginx

```sudo apt-get update```

```sudo apt-get install nginx```

start nginx 

```sudo service nginx start```

Check your localhost page and you should see this page 
