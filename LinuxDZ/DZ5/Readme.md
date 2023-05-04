LeonSheff  ~  sudo iptables -L
[sudo] password for LeonS:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
 LeonSheff  ~  # Все пусто, никаких правил нет
 LeonSheff  ~  sudo iptables -P INPUT DROP
 LeonSheff  ~  sudo iptables -A INPUT -i eth0 -p tcp --dport 80 -j ACCEPT
 LeonSheff  ~  sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -j ACCEPT
 LeonSheff  ~  sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
 LeonSheff  ~  # Политика поменялась на DROP, добавились два правила
 LeonSheff  ~ 
 LeonSheff  ~ 
 LeonSheff  ~ 
  LeonSheff  ~  sudo iptables -t nat -I PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8080
 LeonSheff  ~  sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
 LeonSheff  ~  sudo iptables -L -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
REDIRECT   tcp  --  anywhere             anywhere             tcp dpt:http redir ports 8080

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
 LeonSheff  ~  # Правило применилось и пробрасывает на правильный порт
 LeonSheff  ~ 
 LeonSheff  ~ 
 LeonSheff  ~ 
 LeonSheff  ~  sudo iptables -A INPUT -p tcp -s 3.4.5.6 -j DROP
 LeonSheff  ~  sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
DROP       tcp  --  3.4.5.6              anywhere

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
 LeonSheff  ~  # Правило применилось и отображается в списке
 LeonSheff  ~ 
 LeonSheff  ~ 
 LeonSheff  ~ 
 LeonSheff  ~  mc
 LeonSheff  ~  ps aux | tail
root         585  0.0  0.1   5756  4240 pts/1    Ss   17:52   0:00 /bin/login -f
LeonS       774  0.0  0.3  19108  9680 ?        Ss   17:52   0:00 /lib/systemd/systemd --user
LeonS       776  0.0  0.1 171732  3760 ?        S    17:52   0:00 (sd-pam)
LeonS       788  0.0  0.4 278076 14136 ?        Ssl  17:52   0:00 /usr/bin/pulseaudio --daemonize=no --log-target=journal
LeonS       789  0.0  0.3 766860  9708 pts/1    S+   17:52   0:00 -fish
LeonS       839  0.0  0.1   7116  4008 ?        Ss   17:52   0:00 /usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
LeonS      1611  0.0  0.3  20076  8944 pts/0    S+   18:02   0:00 mc
LeonS      1613  1.3  0.2 308360  8552 pts/2    Ssl  18:02   0:01 /usr/bin/fish
LeonS      1698  0.0  0.1   9208  3192 pts/2    R+   18:03   0:00 ps aux
LeonS      1699  0.0  0.0   5832   584 pts/2    S+   18:03   0:00 tail
 LeonSheff  ~  ps aux | grep mc
LeonS      1611  0.0  0.3  20076  8944 pts/0    S+   18:02   0:00 mc
LeonS      1723  0.0  0.0   6620   720 pts/2    S+   18:04   0:00 grep --color=auto mc
 LeonSheff  ~  kill -s 9 1611
fish: Job 1, 'mc' terminated by signal SIGKILL (Forced quit)
                                                            ⏎
 ✘  LeonSheff  ~  ps aux | grep mc
LeonS      1820  0.0  0.0   6620   712 pts/0    S+   18:05   0:00 grep --color=auto mc
 LeonSheff  ~  # Теперь процесса mc нет в списке (выше был показан только grep)