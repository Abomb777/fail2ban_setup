# Fail2Ban setup

Settings and other usfull information about ip blocking

Get info about jail block
```sh
# fail2ban-client status sshd
```
View auth.log at real time:
```sh
# tail -f /var/log/auth.log
```
List all input rules:
```sh
# sudo iptables -L INPUT -v -n
```
To view only the IP address:
```sh
sudo iptables -L -n | awk '$1=="REJECT" && $4!="0.0.0.0/0" {print $4}'
```
