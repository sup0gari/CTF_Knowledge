# MySQL
MySQL is a popular relational database management system (RDBMS).

## Port
3306, 33060

## Connecting
```bash
mysql -h <IP> -P <Port> -u <Username> -p<Password> # no space between -p and <Password>
mysql -h <IP> -P <Port> -u <Username> -p # After pressing Enter, it will ask you to type the password.
mysql -h <IP> -P <Port> -u <Username> -p <DB> # It will ask for the password, then open the database <DB> directly.
```
A one-liner to execute a command at the same time as connecting.
```bash
mysql -u <Username> -p<Password> -e '<Command>;'
```

## Basic Commands
```bash
show databases; # Displays all databases on the MySQL.
use <DB>; # Switches the current session to the specified database.
show tables # Shows all tables in the current database.
```
## Reference
[MySQL Cheat Sheet](https://gist.github.com/bradtraversy/c831baaad44343cc945e76c2e30927b3)
