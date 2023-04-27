 
 LeonSheff  ~  cd /etc/apt/sources.list.d/
 LeonSheff  sources.list.d  ll
total 44
drwxr-xr-x 2 root root 4096 дек  9 22:13 ./
drwxr-xr-x 7 root root 4096 дек  9 22:09 ../
-rw-r--r-- 1 root root  130 дек  9 22:10 deadsnakes-ubuntu-ppa-focal.list
-rw-r--r-- 1 root root  130 дек  9 22:10 deadsnakes-ubuntu-ppa-focal.list.save
-rw-r--r-- 1 root root  142 дек  9 22:10 fish-shell-ubuntu-release-3-focal.list
-rw-r--r-- 1 root root  142 дек  9 22:10 fish-shell-ubuntu-release-3-focal.list.save
-rw-r--r-- 1 root root  136 дек  9 22:10 neovim-ppa-ubuntu-stable-focal.list
-rw-r--r-- 1 root root  136 дек  9 22:10 neovim-ppa-ubuntu-stable-focal.list.save
-rw-r--r-- 1 root root  140 дек  9 22:10 neovim-ppa-ubuntu-unstable-focal.list
-rw-r--r-- 1 root root  140 дек  9 22:10 neovim-ppa-ubuntu-unstable-focal.list.save
-rw-r--r-- 1 root root  203 дек  9 22:13 vscode.list
 LeonSheff  sources.list.d  sudo su
Welcome to fish, the friendly interactive shell
Type help for instructions on how to use fish
root@LeonS /e/a/sources.list.d#
root@LeonS /e/a/sources.list.d#
root@LeonS /e/a/sources.list.d#
root@LeonS /e/a/sources.list.d# cat > nginx.list
deb https://nginx.org/packages/ubuntu/ focal nginx
deb-src https://nginx.org/packages/ubuntu/ focal nginx⏎
root@LeonS /e/a/sources.list.d# cat nginx.list
deb https://nginx.org/packages/ubuntu/ focal nginx
deb-src https://nginx.org/packages/ubuntu/ focal nginx⏎
root@LeonS /e/a/sources.list.d# # Все добавилось в список
root@LeonS /e/a/sources.list.d# apt update
Пол:1 http://packages.microsoft.com/repos/code stable InRelease [3 569 B]
...
Пол:10 https://nginx.org/packages/ubuntu focal InRelease [3 596 B]
...
Пол:28 http://archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 c-n-f Metadata [592 B]
Чтение списков пакетов… Готово
Построение дерева зависимостей
Чтение информации о состоянии… Готово
Может быть обновлено 2 пакета. Запустите «apt list --upgradable» для их показа.
root@LeonS /e/a/sources.list.d# apt install nginx
Чтение списков пакетов… Готово
Построение дерева зависимостей
Чтение информации о состоянии… Готово
Следующие НОВЫЕ пакеты будут установлены:
  nginx
Обновлено 0 пакетов, установлено 1 новых пакетов, для удаления отмечено 0 пакетов, и 2 пакетов не обновлено.
Необходимо скачать 887 kB архивов.
После данной операции объём занятого дискового пространства возрастёт на 3 141 kB.
Пол:1 https://nginx.org/packages/ubuntu focal/nginx amd64 nginx amd64 1.22.1-1~focal [887 kB]
Получено 887 kB за 1с (1 126 kB/s)
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
invoke-rc.d: could not determine current runlevel
Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /lib/systemd/system/nginx.service.
Обрабатываются триггеры для man-db (2.9.1-1) …
Обрабатываются триггеры для systemd (245.4-4ubuntu3.20) …
root@LeonS /e/a/sources.list.d#
root@LeonS /e/a/sources.list.d#
root@LeonS /e/a/sources.list.d#
root@LeonS /e/a/sources.list.d# dpkg -P nginx
(Чтение базы данных … на данный момент установлено 80824 файла и каталога.)
Удаляется nginx (1.22.1-1~focal) …
invoke-rc.d: could not determine current runlevel
Вычищаются файлы настройки пакета nginx (1.22.1-1~focal) …
Обрабатываются триггеры для man-db (2.9.1-1) …
Обрабатываются триггеры для systemd (245.4-4ubuntu3.20) …
root@LeonS /e/a/sources.list.d#
root@LeonS /e/a/sources.list.d#
root@LeonS /e/a/sources.list.d#
root@LeonS /e/a/sources.list.d# snap install fromscratch
error: cannot communicate with server: Post http://localhost/v2/snaps/fromscratch: dial unix /run/snapd.socket: connect: no such file or directory
root@LeonS /e/a/sources.list.d [1]# systemctl status snapd.service
System has not been booted with systemd as init system (PID 1). Can`t operate.
Failed to connect to bus: Host is down
root@LeonS /e/a/sources.list.d [1]# # Так как у меня WSL надо подправить конфиги, чтобы она запускалась с systemd
root@LeonS /e/a/sources.list.d [1]# ~
root@LeonS ~# vim /etc/wsl.conf
root@LeonS ~# exit
 LeonSheff  root  exit
  ~  wsl --shutdown
  ~  wsl

 LeonSheff  fraps 
 LeonSheff  fraps  systemctl list-unit-files --type=service
UNIT FILE                                  STATE           VENDOR PRESET
accounts-daemon.service                    enabled         enabled
apparmor.service                           enabled         enabled
...
systemd-ask-password-console.service       static          enabled
systemd-ask-password-plymouth.service      static          enabled
systemd-ask-password-wall.service          static          enabled
systemd-backlight@.service                 static          enabled
systemd-binfmt.service                     static          enabled
systemd-bless-boot.service                 static          enabled
systemd-boot-check-no-failures.service     disabled        enabled
systemd-boot-system-token.service          static          enabled
systemd-exit.service                       static          enabled
systemd-fsck-root.service                  enabled-runtime enabled
systemd-fsck@.service                      static          enabled
systemd-fsckd.service                      static          enabled
systemd-halt.service                       static          enabled
systemd-hibernate-resume@.service          static          enabled
systemd-hibernate.service                  static          enabled
systemd-hostnamed.service                  static          enabled
systemd-hwdb-update.service                static          enabled
systemd-hybrid-sleep.service               static          enabled
...
xfs_scrub_all.service                      static          enabled
xfs_scrub_fail@.service                    static          enabled

235 unit files listed.
 LeonSheff  fraps 
 LeonSheff  fraps 
 LeonSheff  fraps 
 LeonSheff  fraps  # Теперь все хорошо, и можно пользоваться snap
 LeonSheff  fraps  sudo snap install fromscratch
[sudo] password for Leon:
fromscratch 1.4.3 from Kilian Valkhof (kilian) installed
 LeonSheff  fraps  ~
 LeonSheff  ~  cd main
 LeonSheff  main  vi test.txt
 LeonSheff  main  crontab -e
no crontab for Leon - using an empty one
crontab: installing new crontab
 LeonSheff  main  # Добавил новую строку
 LeonSheff  main  # */10 * * * * cp /home/Leon/main/test.txt /home/Leon/main/test.txt.bak
 LeonSheff  main  crontab -l
# Edit this file to introduce tasks to be run by cron.
#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').
#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command
*/10 * * * * cp /home/Leon/main/test.txt /home/Leon/main/test.txt.bak
 LeonSheff  main 
 LeonSheff  main 
 LeonSheff  main 
 LeonSheff  main  ll
total 12
drwxr-xr-x  2 Leon www-data 4096 апр 10 18:37 ./
drwxr-xr-x 15 Leon Leon   4096 апр 10 18:14 ../
-rw-rw-r--  1 Leon www-data    0 апр  5 17:57 file1
-rw-------  1 Leon www-data    0 апр  5 17:57 file2
-rw-r--r--  1 Leon Leon     22 апр 10 18:37 test.txt
 LeonSheff  main  # Время 18:44
 LeonSheff  main  ll
total 16
drwxr-xr-x  2 Leon www-data 4096 апр 10 18:50 ./
drwxr-xr-x 15 Leon Leon   4096 апр 10 18:14 ../
-rw-rw-r--  1 Leon www-data    0 апр  5 17:57 file1
-rw-------  1 Leon www-data    0 апр  5 17:57 file2
-rw-r--r--  1 Leon Leon     22 апр 10 18:37 test.txt
-rw-r--r--  1 Leon Leon     22 апр 10 18:50 test.txt.bak
 LeonSheff  main  # Время 18:56