# oracle xe hostname conf
## environment
```
[oracle@localhost ~]$
echo "test -f ~/product/11.2.0/xe/bin/oracle_env.sh && source ~/product/11.2.0/xe/bin/oracle_env.sh" > ~/.bash_profile
```

## hostname independent configuration
```
rm ~oracle/product/11.2.0/xe/network/admin/tnsnames.ora
vi ~oracle/product/11.2.0/xe/network/admin/listener.ora
```

replace **HOST** hostname with *localhost*
e.G.:

```
# listener.ora Network Configuration File:

SID_LIST_LISTENER =
  (SID_LIST =
    (SID_DESC =
      (SID_NAME = PLSExtProc)
      (ORACLE_HOME = /u01/app/oracle/product/11.2.0/xe)
      (PROGRAM = extproc)
    )
  )

LISTENER =
  (DESCRIPTION_LIST =
    (DESCRIPTION =
      (ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC_FOR_XE))
      (ADDRESS = (PROTOCOL = TCP)(HOST = localhost)(PORT = 1521))
    )
  )

DEFAULT_SERVICE_LISTENER = (XE)
```

## disable password expiring

```
sqlplus / as sysdba
SQL > ALTER profile DEFAULT LIMIT PASSWORD_LIFE_TIME unlimited;
SQL > ALTER profile DEFAULT LIMIT PASSWORD_GRACE_TIME unlimited;
```
