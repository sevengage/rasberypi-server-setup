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

```sudo nano /etc/php5/fpm/php.ini```
 
Find the line, cgi.fix_pathinfo=1, and change the 1 to 0.

Restart PHP

```sudo service php5-fpm restart```

Next we need to make some changes in the nginx configuration 

```sudo nano /etc/nginx/sites-available/default```

Keep everything the same but add/or change the things in the screenshot 

![screen shot 2016-08-29 at 10 28 31 pm](https://cloud.githubusercontent.com/assets/20311571/18074313/b3659ea4-6e39-11e6-93c5-a4229185c782.png)

![screen shot 2016-08-29 at 10 29 36 pm](https://cloud.githubusercontent.com/assets/20311571/18074455/b839f1d6-6e3a-11e6-93ac-4562039c2baa.png)

Heres the specifc lines that you should change or edit


[...]
server {
        listen   80;
     

        root /usr/share/nginx/www;
        index index.php index.html index.htm;

        server_name example.com;

        location / {
                try_files $uri $uri/ /index.html;
        }

        error_page 404 /404.html;

        error_page 500 502 503 504 /50x.html;
        location = /50x.html {
              root /usr/share/nginx/www;
        }

        # pass the PHP scripts to FastCGI server listening on the php-fpm socket
        location ~ \.php$ {
                try_files $uri =404;
                fastcgi_pass unix:/var/run/php5-fpm.sock;
                fastcgi_index index.php;
                fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
                include fastcgi_params;
                
        }```
        
## VARNISH 

First install Varnish 

```sudo apt-get install varnish```

Next go here

```sudo nano /etc/default/varnish```

and scroll down to daeman ops 2 and change the port to 80

```DAEMON_OPTS="-a :80 \```


  








 
 












 



