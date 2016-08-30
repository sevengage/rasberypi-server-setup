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

![screen shot 2016-08-29 at 10 28 31 pm](https://cloud.githubusercontent.com/assets/20311571/18074313/b3659ea4-6e39-11e6-93c5-a4229185c782.png)

![screen shot 2016-08-29 at 10 29 36 pm](https://cloud.githubusercontent.com/assets/20311571/18074455/b839f1d6-6e3a-11e6-93ac-4562039c2baa.png)












 



