### Installing MySQL
1. Download mysql from https://dev.mysql.com/downloads/mysql/
2. Open the .dmg file and run the installer
3. create /usr/local/mysql/etc directory and put my.cnf into this directory
### Removing SQL install 
1. Execute the following commands that remove the installation files
```
cd /usr/local/bin
rm -r mysql-<version>
rm mysql
cd /Library/Receipts
rm mysql-<version>pkg
```
2. Go to  `/Library/Receipts` and edit `InstallationHistory.plist`. Remove `<dict> </dict>` block that contains SQL `<version>`.
3. Go to `/private/var/db/receipts`
```
rm com.mysql.*
```
3. Optionally /usr/local/mysql/bin from $PATH in .bash_profile

### Install Python COnnector
```
(env)$ pip install mysql-connector-python
```

### Run SQL
1. Connect to MySQL
```
$ mysql -u <user> -p
```
2. Set Up a database
```
### Create a database
mysql>create database <db name>;

### create an user
mysql> create user <user>@localhost identified by '<password>'

### Grant all rights to user
mysql> grant all privileges on `ibovespa`.* to 'maxi'@'localhost';

### create a table
### RptDt;TckrSymb;UpdActn;GrssTradAmt;TradQty;NtryTm;TradId;TradgSsnId;TradDt
mysql> use ibovespa
mysql> mysql> create table intraday
    (RptDt Date,
    Tckr varchar(255),
    Actn char(1),
    Price float,
    Vol int,
    Time char(9),
    TradId int,
    SsnId char(1),
    TradDt Date);

mysql> load data infile 'tmp.txt' into table intraday fields terminated by ';';


### Connecting to MySQL from R

 ```
 install.package(RMariaDB)
 # maybe re-install Rcpp 
# install.package('RCpp')
> library(DBI)
> library(MariaDB)
> con = dbConnect(MariaDB,user=user, dbame=db name, password=passowrd, host=host)

# Reading all records of query
> dbGetQuery(con,query)
```