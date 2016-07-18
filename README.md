# rasberypi-server-setup
Documentation on how to setup a Raspberry Pi 3 Web Server

First thing you should do is follow the basic directions on setting up the Raspberry Pi that come with the box. The only thing I recommend doing is changing the keyboard to English. This is under Mouse and keyboard settings.

Installing Apache

run this

```sudo apt-get update```

This may take a few seconds

To install Apache simply type

```sudo apt-get install apache2 -y```

Automatically, Apache puts a HTML in the web folder.

Type

“http://localhost in the Pi’s browser or the IP address from another computer on the network.

To find the IP address of the pi Type

```Hostname –I```

If the page above appears in the localhost then you have installed apache correctly.

Become the Html root by typing:

```cd /var/www```

Next we need to take down the default page:

```cd html```

```sudo chown pi: index.html``` (allows you to edit)

```sudo rm index.html``` (removes the file)

```sudo nano index.html``` 

Type in whatever you want and then save it (control + x and then click y)

Refresh your local host page and whatever you type should appear

PHP

Type cd

To Install PHP enter this command:

```sudo apt-get install php5 libapache2-mod-php5 -y``` (If u get an error run apt update and then retype the command from above)

Now remove the index.html

```cd /var/www```

```cd html```

```sudo nano index.php```

When the configuration page opens type a simple

```<?php echo “hello world” ; ?>```

```sudo rm index.html```

Refresh the Page

MySqL

While still in the var/www/html

Install MySql :

```sudo apt-get install mysql-server php5-mysql –y```

Enter a Password that you will remember.

```mysql –uroot –p```(password you created)

The Screen underneath should appear
![example2](https://cloud.githubusercontent.com/assets/20311571/16925360/d442c6d8-4cf1-11e6-92d5-c390f7636e5d.png)


```create database mydata;```

control + d to exit
`
Varnish

First open your apache configuration file

```sudo nano /etc/apache2/ports.conf```

Hit Control +x and then y to exit

Change these lines so Apache listens on port 8080

NameVirtualHost *:8080

Listen 8080

Change the virtual host to 8080 in this file as well

```sudo nano /etc/apache2/sites-enabled/000-default.conf```

Next install Varnish

```sudo apt-get update```

```sudo apt-get install varnish –y```

```sudo mkdir -p /etc/systemd/system/varnish.service.d```

```sudo nano /etc/systemd/system/varnish.service.d/local.conf```

And then paste these lines in the configuration

```[Service]

ExecStart=

ExecStart=/usr/sbin/varnishd -a :80 -T localhost:6082 -f /etc/varnish/default.vcl -S /etc/varnish/secret -s malloc,256m```
```
Reload and restart


```sudo systemctl daemon-reload```

```sudo systemctl enable varnish```

```sudo service apache2 restart```

```sudo service varnish restart```

To see if varnish is working type 

```curl –I http://localhost```

And the screen should resemble the one below
![example3](https://cloud.githubusercontent.com/assets/20311571/16925437/345e2fc6-4cf2-11e6-8e3d-4b24c0205983.png)


