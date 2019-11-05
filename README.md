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
