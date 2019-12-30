# Fail2Ban setup

Settings and other usfull information about ip blocking

Get info about jail block
```sh
# fail2ban-client status sshd
```
List all jails:
```sh
fail2ban-client status | grep "Jail list:" | sed "s/ //g" | awk '{split($2,a,",");for(i in a) system("fail2ban-client status " a[i])}' | grep "Status\|IP list"
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

https://www.ctrl.blog/entry/fail2ban-http403.html

https://serverfault.com/questions/640873/how-to-ban-syn-flood-attacks-using-fail2ban


[postfix-sasl]

```code
[postfix-sasl]
enabled  = true
findtime  = 10800
bantime = 7200
port     = smtp,465,submission,imap2,imap3,imaps,pop3,pop3s
filter   = postfix-sasl
action   = iptables-multiport[name=postfix-sasl, port="http,https,smtp,submission,465,pop3,pop3s,imap,imaps,sieve", protocol=tcp]
##logpath  = %(postfix_log)s
logpath  = /var/log/mail.log
backend  = %(postfix_backend)s
maxretry = 2
```

vim /etc/fail2ban/jail.conf
sudo fail2ban-client status
fail2ban-client status ssh
sudo iptables -L -n | awk '$1=="REJECT" && $4!="0.0.0.0/0"'
sudo iptables -L -n | awk '$1=="REJECT" && $4!="0.0.0.0/0" {print $4}'
fail2ban-client status sshd
fail2ban-client status ssh
vim /etc/fail2ban/jail.conf
fail2ban-client status ssh-iptables
vim /etc/fail2ban/jail.conf
fail2ban-client status | grep "Jail list" | sed -E 's/^[^:]+:[ \t]+//' | sed 's/,//g'
fail2ban-client status
sudo systemctl restart fail2ban
service fail2ban restart
vim /etc/fail2ban/jail.conf
vim /etc/fail2ban/fail2ban.conf
service fail2ban restart
fail2ban-client status | grep "Banned IP list" | sed -E 's/^[^:]+:[ \t]+//' | sed 's/,//g'
fail2ban-client status sshd
fail2ban-client status sshd | grep "Banned IP list" | sed -E 's/^[^:]+:[ \t]+//' | sed 's/,//g'


vim /bann_ip_sync.sh
fail2ban-client set sshd banip 218.65.30.156

fail2ban-client status sshs
fail2ban-client status sshd
fail2ban-client status | grep "Banned IP list"
fail2ban-client status sshd
fail2ban-client status | grep "Jail list:" | sed "s/ //g" | awk '{split($2,a,",");for(i in a) system("fail2ban-client status " a[i])}' | grep "Status\|IP list"
