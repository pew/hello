# oracle xe hostname conf
## environment
```
[oracle@localhost ~]$
echo "test -f ~/product/11.2.0/xe/bin/oracle_env.sh && source ~/product/11.2.0/xe/bin/oracle_env.sh" > ~/.bash_profile
```

## hostname independent configuration

```
rm ~oracle/product/11.2.0/xe/network/admin/listener.ora
vi ~oracle/product/11.2.0/xe/network/admin/tnsnames.ora
```


```
XE=(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=127.0.0.1)(PORT=1521))(CONNECT_DATA=(SERVER=DEDICATED)(SERVICE_NAME=XE)))
```

## disable password expiring

```
sqlplus / as sysdba
SQL > ALTER profile DEFAULT LIMIT PASSWORD_LIFE_TIME unlimited;
SQL > ALTER profile DEFAULT LIMIT PASSWORD_GRACE_TIME unlimited;
```
