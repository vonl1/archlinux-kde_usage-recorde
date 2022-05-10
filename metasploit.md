# metasploit
## ahead
```shell
sudo pacman -S metasploit postgresql
```
## config
---
### postgres
```shell
sudo su - postgres
initdb --locale en_US.UTF-8 -D /var/lib/postgres/data
exit
systemctl start postgresql
sudo systemctl status postgresql

sudo su - postgres
psql        
CREATE DATABASE msf;
\l    #confirm created database
CREATE USER msfuser WITH ENCRYPTED PASSWORD 'MyPassword';
GRANT ALL PRIVILEGES ON DATABASE msf to msfuser;
#ctrl + d exit the postgresql and back to your user home
```
---

### metasploit 
```
cd .msf4/

vim database.yml

# copy below code into your database.yml 
production:
   adapter: postgresql
   database: msf
   username: msfuser
   password: MyPassword
   host: localhost
   port: 5432
   pool: 5
   timeout: 5

msfconsole  # start msf

db_connect msfuser@msf
db_save
```
---
## conclude
now everytime you open the msf,you can automatic connect the database.


>https://techviewleo.com/install-metasploit-framework-on-arch-manjaro-garuda-linux/

>https://techviewleo.com/install-postgresql-on-arch-manjaro-garuda-linux/

