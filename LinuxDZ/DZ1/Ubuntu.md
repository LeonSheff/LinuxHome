// Это powerline-символы, поэтому prompt некрасиво выглядит // Две кавычки (''s), чтобы нормально отображалось в сноске   

  ~    ssh -p 2022 disbro@localhost
LeonSheff@localhost''s password:
Welcome to Ubuntu 20.04.6 LTS (GNU/Linux 5.15.90.1-microsoft-standard-WSL2 x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Пн 16 апр 2023 15:53:07 MSK

  System load:  0.08               Processes:             11
  Usage of /:   2.0% of 850.92GB   Users logged in:       0
  Memory usage: 14%                IPv4 address for eth0: 178.25.18.94
  Swap usage:   0%


Расширенное поддержание безопасности (ESM) для Applications выключено.

0 обновлений может быть применено немедленно.

Включите ESM Apps для получения дополнительных будущих обновлений безопасности.
Смотрите https://ubuntu.com/esm или выполните: sudo pro status

New release '22.04.2 LTS' available.
Run 'do-release-upgrade' to upgrade to it.


Last login: Mon APR 16 15:45:52 2023 from 127.0.0.1
 LeonSheff  ~  sudo apt update; sudo apt upgrade
[sudo] password for leonshef:
Пол:1 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Сущ:2 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu focal InRelease
Сущ:3 http://archive.ubuntu.com/ubuntu focal InRelease
Сущ:4 http://ppa.launchpad.net/fish-shell/release-3/ubuntu focal InRelease
Сущ:5 http://packages.microsoft.com/repos/code stable InRelease
Пол:6 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Сущ:7 http://ppa.launchpad.net/neovim-ppa/stable/ubuntu focal InRelease
Сущ:8 https://packages.microsoft.com/repos/vscode stable InRelease
Сущ:9 http://ppa.launchpad.net/neovim-ppa/unstable/ubuntu focal InRelease
Пол:10 http://archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]
Получено 386 kB за 2с (216 kB/s)
Чтение списков пакетов… Готово
Построение дерева зависимостей
Чтение информации о состоянии… Готово
Все пакеты имеют последние версии.
Чтение списков пакетов… Готово
Построение дерева зависимостей
Чтение информации о состоянии… Готово
Расчёт обновлений… Готово
Обновлено 0 пакетов, установлено 0 новых пакетов, для удаления отмечено 0 пакетов, и 0 пакетов не обновлено.
 LeonSheff  ~  uname -a
Linux Leon-Shef 5.15.90.1-microsoft-standard-WSL2 #1 SMP Fri Jan 27 02:56:13 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
 LeonSheff  ~  lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.6 LTS
Release:        20.04
Codename:       focal
 LeonSheff  ~  sudo apt install mc
Чтение списков пакетов… Готово
Построение дерева зависимостей
Чтение информации о состоянии… Готово
Уже установлен пакет mc самой новой версии (3:4.8.24-2ubuntu1).
Обновлено 0 пакетов, установлено 0 новых пакетов, для удаления отмечено 0 пакетов, и 0 пакетов не обновлено

/////////////