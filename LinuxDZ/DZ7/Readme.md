LeonSheff  fraps  # Я уже активно пользуюсь Docker в Windows и Linux. Ломать ничего не хочу, много потеряю
 LeonSheff  fraps  # Хотя у меня WSL, у Docker есть интеграция с WSL2
 LeonSheff  fraps  # Поэтому вместо первых двух заданий, я сделаю дополнительное
 LeonSheff  fraps  docker pull ubuntu
Using default tag: latest
latest: Pulling from library/ubuntu
2ab09b027e7f: Pull complete
Digest: sha256:67211c14fa74f070d27cc59d69a7fa9aeff8e28ea118ef3babc295a0428a6d21
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest
 LeonSheff  fraps  docker run -it ubuntu
root@d46b105513db:/# whoami
root
root@d46b105513db:/# uname -a
Linux d46b105513db 5.15.90.1-microsoft-standard-WSL2 #1 SMP Fri Jan 27 02:56:13 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
root@d46b105513db:/# apt list
Listing... Done
adduser/now 3.118ubuntu5 all [installed,local]
apt/now 2.4.8 amd64 [installed,local]
base-files/now 12ubuntu4.3 amd64 [installed,local]
...
procps/now 2:3.3.17-6ubuntu2 amd64 [installed,local]
sed/now 4.8-1ubuntu2 amd64 [installed,local]
sensible-utils/now 0.0.17 all [installed,local]
sysvinit-utils/now 3.01-1ubuntu1 amd64 [installed,local]
tar/now 1.34+dfsg-1ubuntu0.1.22.04.1 amd64 [installed,local]
ubuntu-keyring/now 2021.03.26 all [installed,local]
usrmerge/now 25ubuntu2 all [installed,local]
util-linux/now 2.37.2-4ubuntu3 amd64 [installed,local]
zlib1g/now 1:1.2.11.dfsg-2ubuntu9.2 amd64 [installed,local]
root@d46b105513db:/# exit
exit
 LeonSheff  fraps 
 LeonSheff  fraps 
 LeonSheff  fraps 
 LeonSheff  fraps  ~
 LeonSheff  ~  cd main
 LeonSheff  main  ll
total 20
drwxr-xr-x  2 disbro www-data 4096 апр 21 16:09 ./
drwxr-xr-x 15 disbro disbro   4096 апр 17 20:34 ../
-rwxrwxr-x  1 disbro www-data   80 апр 21 16:09 file1*
-rw-------  1 disbro www-data    0 апр  5 17:57 file2
-rw-r--r--  1 disbro disbro     22 апр 10 18:37 test.txt
-rw-r--r--  1 disbro disbro     22 апр 21 17:30 test.txt.bak
 LeonSheff  main  vi Dockerfile
 LeonSheff  main  cat Dockerfile
FROM ubuntu:20.04

MAINTAINER disbro

ENV TZ=Europe/Moscow

RUN apt update
RUN apt install nginx -y
RUN apt install php-fpm -y
RUN mkdir /run/php-fpm

VOLUME "/var/ww/html"

EXPOSE 80

CMD /usr/sbin/nginx -g "daemon off;"; php-fpm -D
 LeonSheff  ~  # Выбрал версию 20.04, так как latest при установке php-fpm
 LeonSheff  ~  # просит интерактивный ответ при билде
 LeonSheff  main  sudo docker build -t php-fpm .
[+] Building 79.6s (9/9) FINISHED
 => [internal] load build definition from Dockerfile                                                                                                                                   0.0s
 => => transferring dockerfile: 279B                                                                                                                                                   0.0s
 => [internal] load .dockerignore                                                                                                                                                      0.0s
 => => transferring context: 2B                                                                                                                                                        0.0s
 => [internal] load metadata for docker.io/library/ubuntu:20.04                                                                                                                        2.6s
 => [1/5] FROM docker.io/library/ubuntu:20.04@sha256:db8bf6f4fb351aa7a26e27ba2686cf35a6a409f65603e59d4c203e58387dc6b3                                                                  4.7s
 => => resolve docker.io/library/ubuntu:20.04@sha256:db8bf6f4fb351aa7a26e27ba2686cf35a6a409f65603e59d4c203e58387dc6b3                                                                  0.0s
 => => sha256:b795f8e0caaaacad9859a9a38fe1c78154f8301fdaf0872eaf1520d66d9c0b98 424B / 424B                                                                                             0.0s
 => => sha256:88bd6891718934e63638d9ca0ecee018e69b638270fe04990a310e5c78ab4a92 2.30kB / 2.30kB                                                                                         0.0s
 => => sha256:ca1778b6935686ad781c27472c4668fc61ec3aeb85494f72deb1921892b9d39e 27.50MB / 27.50MB                                                                                       2.6s
 => => sha256:db8bf6f4fb351aa7a26e27ba2686cf35a6a409f65603e59d4c203e58387dc6b3 1.13kB / 1.13kB                                                                                         0.0s
 => => extracting sha256:ca1778b6935686ad781c27472c4668fc61ec3aeb85494f72deb1921892b9d39e                                                                                              1.9s
 => [2/5] RUN apt update                                                                                                                                                               9.6s
 => [3/5] RUN apt install nginx -y                                                                                                                                                    21.1s
 => [4/5] RUN apt install php-fpm -y                                                                                                                                                  39.1s
 => [5/5] RUN mkdir /run/php-fpm                                                                                                                                                       0.7s
 => exporting to image                                                                                                                                                                 1.6s
 => => exporting layers                                                                                                                                                                1.6s
 => => writing image sha256:a77e7d7396a23a1c1cb08a2380e82016ab5786e6ba6065ebfa53014758606ad5                                                                                           0.0s
 => => naming to docker.io/library/php-fpm                                                                                                                                             0.0s

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
 LeonSheff  main  docker images --filter "reference=php*"
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
php-fpm      latest    a77e7d7396a2   44 seconds ago   255MB
 LeonSheff  main  # Не хочу показывать остальные образы, их очень много, поэтому отфильтровал по названию