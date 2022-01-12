# metasploit
## ahead
```shell

sudo vim /etc/pacman.conf
---
+ blackarh mirror
---
sudo pacman -Syy
sudo pacman -S metasploit postgresql msfdb
```
## config
### metasploit 
```
cd .msf4/

vim database.yml
---shell
production:
   adapter: postgresql
   database: msf
   username: postgres
   password: {password}
   host: localhost
   port: 5432
   pool: 5
   timeout: 5
---
```
### postgres
```shell
sudo su - postgres
initdb --locale en_US.UTF-8 -D /var/lib/postgres/data
exit
systemctl start postgresql
sudo systemctl status postgresql
```
### msfdb-blackarch
`sudo msfdb-blackarch init`

## conclude
Now your metasploit is working well with postgresql.Remember start postgresql first,then start msfconsole.
And if you dont use balckarch remember hide blackarch in `etc/pacman.conf`

>https://techviewleo.com/install-metasploit-framework-on-arch-manjaro-garuda-linux/

>https://techviewleo.com/install-postgresql-on-arch-manjaro-garuda-linux/

>https://bbs.ichunqiu.com/thread-61343-1-1.html
