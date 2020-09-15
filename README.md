# Usage

Change the folder permission to make sure that the container is able to access the directory:
```
$ sudo chmod -R 777 addons
$ sudo chmod -R 777 etc
```

Start the container:
```
$ docker-compose up
```



* Then open `localhost:8071` to access Odoo 12.0. If you want to start the server with a different port, change **8071** to another value:

```
ports:
 - "8071:8069"
```

* Log file is printed @ **etc/odoo-server.log**

To run in detached mode, execute this command:

```
$ docker-compose up -d
```

# Custom addons
 1. Lỗi OSError: inotify watch limit reached
 ```
  cat /proc/sys/fs/inotify/max_user_watches
 8192
 echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf
 sudo sysctl -p
 ```
 
 2. Lỗi virtual real time limit
 ```
 Sửa trong file config odoo
 limit-time-real=600
 ```
# Custom addons
Cài đặt 1 số thư viện trong image:
```
sandbox: cai dat tren quanly
	pip3 install xlrd
	= Cài cái này trước wheel
	pip3 install wheel
	pip3 install python-docx
	pip3 install openpyxl
	pip3 install pandas
	
	# Cài auto backup
	pip3 install paramiko
	
	#cài đặt asterisk
	pip3 install tinyrpc
	pip3 install Humanize
	
	pip3 install xlrd wheel python-docx openpyxl pandas paramiko
```
Lỗi khi in: cấu hính thêm tham số hệ thống: http://0.0.0.0:8069 = report.url
The **addons** folder contains custom addons. Just put your custom addons if you have any.

# Odoo configuration

To change Odoo configuration, edit file: **etc/odoo.conf**.

# docker-compose.yml

* odoo:12.0
* postgres:9.5

# Odoo 12 screenshots

![odoo-12-welcome-docker](screenshots/odoo-12-welcome-screenshot.png)

![odoo-12-apps-docker](screenshots/odoo-12-apps-screenshot.png)

![odoo-12-sales](screenshots/odoo-12-sales-screen.png)
