# Note MySQL

Here is a short list of other common possible permissions that users can enjoy.
```
ALL PRIVILEGES- as we saw previously, this would allow a MySQL user full access to a designated database (or if no database is selected, global access across the system)
CREATE- allows them to create new tables or databases
DROP- allows them to them to delete tables or databases
DELETE- allows them to delete rows from tables
INSERT- allows them to insert rows into tables
SELECT- allows them to use the SELECT command to read through databases
UPDATE- allow them to update table rows
GRANT OPTION- allows them to grant or remove other users' privileges
```
Grant Different User Permissions
```
GRANT ALL ON <local name>.* TO <username>@<remote web node server ip address> IDENTIFIED BY '<password>';

GRANT ALL PRIVILEGES ON database_name.* TO 'username'@'%' IDENTIFIED BY '<password>';
```
For example,
```
GRANT ALL PRIVILEGES ON asterisk.* TO 'asterisk'@'%';
GRANT ALL ON magento_remote.* TO dbuser@192.0.2.50 IDENTIFIED BY 'dbuserpassword';

CREATE USER 'myuser'@'%' IDENTIFIED BY 'mypass';
```
To list users:
```
select user,host from mysql.user;
```
To show privileges:
```
show grants for 'user'@'host';
```
To change privileges, first revoke. Such as:
```
REVOKE type_of_permission ON database_name.table_name FROM ‘username’@‘localhost’;
revoke all privileges on *.* from 'user'@'host';
```
Then grant the appropriate privileges as desired:
```
grant SELECT,INSERT,UPDATE,DELETE ON `db`.* TO 'user'@'host';
```
Finally, flush:
```
flush privileges;
```
GRANT ALL PRIVILEGES ON sunfrog.* TO 'nolove'@'%' IDENTIFIED BY 'password';

Enable root remote to databaseGRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'password' WITH GRANT OPTION;

* Export 100 rows from table mysql *
```
mysqldump -u root -p database_name table_name --where="1=1 order by id desc limit 100" > /opt/tbl_name.sql
```
# To export to file (data only)
```
mysqldump -u [user] -p[pass] --no-create-info mydb > mydb.sql

# Case: Export data of only table
mysqldump -uroot -p --no-create-db --no-create-info Campaign call_event > /opt/test.sql
```
# To export to file (structure only)
```
mysqldump -u [user] -p[pass] --no-data mydb > mydb.sql
```
# To import to database
```
mysql -u [user] -p[pass] databasename < filename.sql
```
#You can use the --ignore-table option. So you could do
```
mysqldump -u USERNAME -pPASSWORD DATABASE --ignore-table=DATABASE.table1 > database.sql
```
