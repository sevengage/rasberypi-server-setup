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

Check your localhost page and you should see this page, or type in the raspbery's pi ip in your browser
Next install PHP

```sudo apt-get install php5-fpm```

Next we need to make a change in some configuration 

sudo nano /etc/php5/fpm/php.ini
 
Find the line, cgi.fix_pathinfo=1, and change the 1 to 0.

Restart PHP

Next we need to make some changes in the nginx configuration 

sudo nano /etc/nginx/sites-available/default

Keep everything the same but add/or change the things in the screenshot 





```sudo service php5-fpm restart```


 



