LeonSheff  ~  sudo apt install nginx --yes
[sudo] password for LeonS:
Чтение списков пакетов… Готово
Построение дерева зависимостей
Чтение информации о состоянии… Готово
Следующие НОВЫЕ пакеты будут установлены:
  nginx
Обновлено 0 пакетов, установлено 1 новых пакетов, для удаления отмечено 0 пакетов, и 2 пакетов не обновлено.
Необходимо скачать 887 kB архивов.
После данной операции объём занятого дискового пространства возрастёт на 3 141 kB.
Пол:1 https://nginx.org/packages/ubuntu focal/nginx amd64 nginx amd64 1.22.1-1~focal [887 kB]
Получено 887 kB за 1с (608 kB/s)
Выбор ранее не выбранного пакета nginx.
(Чтение базы данных … на данный момент установлено 80790 файлов и каталогов.)
Подготовка к распаковке …/nginx_1.22.1-1~focal_amd64.deb …
----------------------------------------------------------------------

Thanks for using nginx!

Please find the official documentation for nginx here:
* https://nginx.org/en/docs/

Please subscribe to nginx-announce mailing list to get
the most important news about nginx:
* https://nginx.org/en/support.html

Commercial subscriptions for nginx are available on:
* https://nginx.com/products/

----------------------------------------------------------------------
Распаковывается nginx (1.22.1-1~focal) …
Настраивается пакет nginx (1.22.1-1~focal) …
Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /lib/systemd/system/nginx.service.
Обрабатываются триггеры для man-db (2.9.1-1) …
Обрабатываются триггеры для systemd (245.4-4ubuntu3.20) …
 LeonSheff  ~  systemctl status nginx
● nginx.service - nginx - high performance web server
     Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
     Active: inactive (dead)
       Docs: https://nginx.org/en/docs/
 ✘  LeonSheff  ~  # Так как у меня WSL, нужно запускать ручками
 ✘  LeonSheff  ~  sudo /etc/init.d/nginx start
Starting nginx (via systemctl): nginx.service.
 LeonSheff  ~  systemctl status nginx
● nginx.service - nginx - high performance web server
     Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2023-04-17 18:18:40 MSK; 17s ago
       Docs: https://nginx.org/en/docs/
    Process: 1224 ExecStart=/usr/sbin/nginx -c /etc/nginx/nginx.conf (code=exited, status=0/SUCCESS)
   Main PID: 1225 (nginx)
      Tasks: 5 (limit: 3451)
     Memory: 3.9M
        CPU: 14ms
     CGroup: /system.slice/nginx.service
             ├─1225 nginx: master process /usr/sbin/nginx -c /etc/nginx/nginx.conf
             ├─1226 nginx: worker process
             ├─1227 nginx: worker process
             ├─1228 nginx: worker process
             └─1229 nginx: worker process

апр 17 18:18:40 Leon systemd[1]: Starting nginx - high performance web server...
апр 17 18:18:40 Leon systemd[1]: Started nginx - high performance web server.
 LeonSheff  ~  # Теперь nginx работает
 LeonSheff  ~  # Проверим порты
 LeonSheff  ~  sudo ss -ntlp
State  Recv-Q Send-Q Local Address:Port  Peer Address:Port Process
LISTEN 0      511          0.0.0.0:80         0.0.0.0:*     users:(("nginx",pid=1229,fd=6),("nginx",pid=1228,fd=6),("nginx",pid=1227,fd=6),("nginx",pid=1226,fd=6),("nginx",pid=1225,fd=6))
LISTEN 0      4096   127.0.0.53%lo:53         0.0.0.0:*     users:(("systemd-resolve",pid=272,fd=13))
 LeonSheff  ~  # Видно, что 80 порт занят nginx
 LeonSheff  ~  
 LeonSheff  ~  
 LeonSheff  ~  
 LeonSheff  ~  sudo apt install apache2 --yes
...
Enabling conf serve-cgi-bin.
Enabling site 000-default.
Created symlink /etc/systemd/system/multi-user.target.wants/apache2.service → /lib/systemd/system/apache2.service.
Created symlink /etc/systemd/system/multi-user.target.wants/apache-htcacheclean.service → /lib/systemd/system/apache-htcacheclean.service.
Job for apache2.service failed because the control process exited with error code.
See "systemctl status apache2.service" and "journalctl -xe" for details.
invoke-rc.d: initscript apache2, action "start" failed.
● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Mon 2023-04-17 18:37:48 MSK; 9ms ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 2095 ExecStart=/usr/sbin/apachectl start (code=exited, status=1/FAILURE)
        CPU: 37ms

апр 17 18:37:48 Leon systemd[1]: Starting The Apache HTTP Server...
апр 17 18:37:48 Leon apachectl[2105]: (98)Address already in use: AH00072: make_sock: could not bind to address [::]:80
апр 17 18:37:48 Leon apachectl[2105]: (98)Address already in use: AH00072: make_sock: could not bind to address 0.0.0.0:80
апр 17 18:37:48 Leon apachectl[2105]: no listening sockets available, shutting down
апр 17 18:37:48 Leon apachectl[2105]: AH00015: Unable to open logs
апр 17 18:37:48 Leon apachectl[2095]: Action 'start' failed.
апр 17 18:37:48 Leon apachectl[2095]: The Apache error log may have more information.
апр 17 18:37:48 Leon systemd[1]: apache2.service: Control process exited, code=exited, status=1/FAILURE
апр 17 18:37:48 Leon systemd[1]: apache2.service: Failed with result 'exit-code'.
апр 17 18:37:48 Leon systemd[1]: Failed to start The Apache HTTP Server.
Обрабатываются триггеры для ufw (0.36-6ubuntu1) …
Обрабатываются триггеры для systemd (245.4-4ubuntu3.20) …
Обрабатываются триггеры для man-db (2.9.1-1) …
Обрабатываются триггеры для libc-bin (2.31-0ubuntu9.9) …
 LeonSheff  ~  # Выскочила ошибка, так как Apache хочет занять тот же порт, что и nginx
 LeonSheff  ~ 
 LeonSheff  ~ 
 LeonSheff  ~  sudo nvim /etc/apache2/apache2.conf
 LeonSheff  ~  # Поменял порт с 80 на 8000, теперь можно запустить Apache и все проверить
 LeonSheff  ~  sudo systemctl start apache2
 LeonSheff  ~  systemctl status apache2
● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2023-04-17 18:44:05 MSK; 59s ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 2926 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/SUCCESS)
   Main PID: 2930 (apache2)
      Tasks: 55 (limit: 3451)
     Memory: 21.1M
        CPU: 92ms
     CGroup: /system.slice/apache2.service
             ├─2930 /usr/sbin/apache2 -k start
             ├─2934 /usr/sbin/apache2 -k start
             └─2935 /usr/sbin/apache2 -k start

апр 17 18:44:05 Leon systemd[1]: Starting The Apache HTTP Server...
апр 17 18:44:05 Leon systemd[1]: Started The Apache HTTP Server.
 LeonSheff  ~  # Теперь все отлично и все работает вместе
 LeonSheff  ~ 
 LeonSheff  ~ 
 LeonSheff  ~ 
 LeonSheff  ~  sudo nvim sites-available/default
 LeonSheff  ~  sudo nvim /etc/nginx/sites-available/default
 LeonSheff  ~  sudo nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
 LeonSheff  ~  sudo systemctl reload nginx
 LeonSheff  ~  # Теперь для nginx настроена схема обратного прокси
 LeonSheff  ~ 
 LeonSheff  ~ 
 LeonSheff  ~ 
 LeonSheff  ~  LeonSheff  ~  sudo apt install libapache2-mod-php php  --yes
...
Creating config file /etc/php/7.4/apache2/php.ini with new version
Module mpm_event disabled.
Enabling module mpm_prefork.
apache2_switch_mpm Switch to prefork
apache2_invoke: Enable module php7.4
Настраивается пакет php7.4 (7.4.3-4ubuntu2.18) …
Настраивается пакет libapache2-mod-php (2:7.4+75) …
Настраивается пакет php (2:7.4+75) …
Обрабатываются триггеры для man-db (2.9.1-1) …
Обрабатываются триггеры для php7.4-cli (7.4.3-4ubuntu2.18) …
Обрабатываются триггеры для libapache2-mod-php7.4 (7.4.3-4ubuntu2.18) …
 LeonSheff  ~  
 LeonSheff  ~  
 LeonSheff  ~  
 LeonSheff  ~  # Решил сразу установить MysSQL Server
 LeonSheff  ~  sudo apt install mysql-server php-fpm php-mysql
...
done!
update-alternatives: используется /var/lib/mecab/dic/ipadic-utf8 для предоставления /var/lib/mecab/dic/debian (mecab-dictionary) в автоматическом режиме
Настраивается пакет mysql-server-8.0 (8.0.32-0ubuntu0.20.04.2) …
update-alternatives: используется /etc/mysql/mysql.cnf для предоставления /etc/mysql/my.cnf (my.cnf) в автоматическом режиме
Renaming removed key_buffer and myisam-recover options (if present)
mysqld will log errors to /var/log/mysql/error.log
mysqld is running as pid 13760
Created symlink /etc/systemd/system/multi-user.target.wants/mysql.service → /lib/systemd/system/mysql.service.
Настраивается пакет mysql-server (8.0.32-0ubuntu0.20.04.2) …
Обрабатываются триггеры для libc-bin (2.31-0ubuntu9.9) …
Обрабатываются триггеры для systemd (245.4-4ubuntu3.20) …
Обрабатываются триггеры для man-db (2.9.1-1) …
Обрабатываются триггеры для libapache2-mod-php7.4 (7.4.3-4ubuntu2.18) …
Обрабатываются триггеры для php7.4-cli (7.4.3-4ubuntu2.18) …
Обрабатываются триггеры для php7.4-fpm (7.4.3-4ubuntu2.18) …
NOTICE: Not enabling PHP 7.4 FPM by default.
NOTICE: To enable PHP 7.4 FPM in Apache2 do:
NOTICE: a2enmod proxy_fcgi setenvif
NOTICE: a2enconf php7.4-fpm
NOTICE: You are seeing this message because you have apache2 package installed.
 LeonSheff  ~  
 LeonSheff  ~  
 LeonSheff  ~  
 LeonSheff  ~  sudo a2enmod proxy_fcgi setenvif
Considering dependency proxy for proxy_fcgi:
Enabling module proxy.
Enabling module proxy_fcgi.
Module setenvif already enabled
To activate the new configuration, you need to run:
  systemctl restart apache2
 LeonSheff  ~  sudo a2enconf php7.4-fpm
Enabling conf php7.4-fpm.
To activate the new configuration, you need to run:
  systemctl reload apache2
 LeonSheff  ~  # Теперь Apache может работать с PHP-FPM
 LeonSheff  ~  sudo /etc/init.d/php7.4-fpm start
Starting php7.4-fpm (via systemctl): php7.4-fpm.service.
 LeonSheff  ~  # Теперь служба PHP-FPM заработала
 LeonSheff  ~  sudo nvim /etc/nginx/sites-available/default
 LeonSheff  ~  sudo systemctl reload nginx
 LeonSheff  ~  # Теперь nginx может работать с PHP-FPM
 LeonSheff  ~  
 LeonSheff  ~  
 LeonSheff  ~  
 LeonSheff  ~  # Настроим MySQL
 LeonSheff  ~  sudo /etc/init.d/mysql start
Starting mysql (via systemctl): mysql.service.
 LeonSheff  ~  sudo mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 18
Server version: 8.0.32-0ubuntu0.20.04.2 (Ubuntu)

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0,07 sec)

mysql> create database test_db;
Query OK, 1 row affected (0,03 sec)

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
| test_db            |
+--------------------+
5 rows in set (0,01 sec)

mysql> use test_db;
Database changed
mysql> create table records(id INT, name VARCHAR(200));
Query OK, 0 rows affected (0,13 sec)

mysql> insert into records values (1, 'Test record'), (2, 'Test record 2');
Query OK, 2 rows affected (0,10 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> select * from records;
+------+---------------+
| id   | name          |
+------+---------------+
|    1 | Test record   |
|    2 | Test record 2 |
+------+---------------+
2 rows in set (0,01 sec)

mysql> exit
Bye
 LeonSheff  ~  sudo apt install php libapache2-mod-php php-common php-mysql php-gmp php-curl php-intl php7.4-mbstring php-xmlrpc php-gd php-xml php-cli php-zip --yes
...
Creating config file /etc/php/7.4/mods-available/zip.ini with new version
Настраивается пакет php-gmp (2:7.4+75) …
Настраивается пакет php-cli (2:7.4+75) …
Настраивается пакет php-zip (2:7.4+75) …
Настраивается пакет php7.4-gd (7.4.3-4ubuntu2.18) …

Creating config file /etc/php/7.4/mods-available/gd.ini with new version
Настраивается пакет php-xml (2:7.4+75) …
Настраивается пакет php-curl (2:7.4+75) …
Настраивается пакет php7.4-xmlrpc (7.4.3-4ubuntu2.18) …

Creating config file /etc/php/7.4/mods-available/xmlrpc.ini with new version
Настраивается пакет php-xmlrpc (2:7.4+75) …
Настраивается пакет php-gd (2:7.4+75) …
Обрабатываются триггеры для php7.4-fpm (7.4.3-4ubuntu2.18) …
NOTICE: Not enabling PHP 7.4 FPM by default.
NOTICE: To enable PHP 7.4 FPM in Apache2 do:
NOTICE: a2enmod proxy_fcgi setenvif
NOTICE: a2enconf php7.4-fpm
NOTICE: You are seeing this message because you have apache2 package installed.
Обрабатываются триггеры для libc-bin (2.31-0ubuntu9.9) …
Обрабатываются триггеры для libapache2-mod-php7.4 (7.4.3-4ubuntu2.18) …
Обрабатываются триггеры для php7.4-cli (7.4.3-4ubuntu2.18) …
LeonSheff  ~  sudo apt install phpmyadmin
...
Creating config file /etc/dbconfig-common/phpmyadmin.conf with new version

Creating config file /etc/phpmyadmin/config-db.php with new version
checking privileges on database phpmyadmin for phpmyadmin@localhost: user creation needed.
granting access to database phpmyadmin for phpmyadmin@localhost: success.
verifying access for phpmyadmin@localhost: success.
creating database phpmyadmin: success.
verifying database phpmyadmin exists: success.
populating database via sql...  done.
dbconfig-common: flushing administrative password
Обрабатываются триггеры для hicolor-icon-theme (0.17-2) …
 LeonSheff  ~  sudo nano /etc/apache2/apache2.conf
 LeonSheff  ~  sudo service apache2 restart
 LeonSheff  ~  # Добавил новую строку, для использования phpMyAdmin, теперь все работает