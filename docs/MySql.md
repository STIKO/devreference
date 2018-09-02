##sql_mode
**Error**

`"sql_mode = ONLY_FULL_GROUP_BY" mysql error`

**Solution**

* sequelPro
```sql
set sql_mode = ''
```

* `my.cnf`<br>
remove `sql_mode = ONLY_FULL_GROUP_BY` from `my.cnf`

* mySql
```sql
SET GLOBAL sql_mode=(SELECT REPLACE(@@sql_mode,'ONLY_FULL_GROUP_BY',''));
```
* Docker Container<br>
ssh into `mysql` container then run one of the commands above.</br>
Or in one command
```bash
docker exec -ti $(docker ps -aqf "name=<container_name>”) mysql -uroot -proot -e "SET GLOBAL sql_mode=(SELECT REPLACE(@@sql_mode,'ONLY_FULL_GROUP_BY',''))"
```

##Enable mysql `local-infile`
insert this in `/etc/mysql/my.cnf` or `/etc/my.cnf`
```text
[mysqld]
local-infile

[mysql]
local-infile
```