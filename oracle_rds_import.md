# oracle (aws rds) data pump import

# metadata
for example:

RDS DB: `abc-defgd2.us-east-1.rds.amazonaws.com:1521`
EC2 IP Addr with Oracle DB: `172.30.1.228`

# create database link

```
# login to rds db
sqlplus user/password@abc-defgd2.us-east-1.rds.amazonaws.com:1521/schema

# create database link between rds and ec2 instance
SQL> create database link ec2 connect to system identified by system using '172.30.1.234:1521/XE';

# create tablespaces if needed
SQL> create tablespace abc;

# import from ec2 instance
impdp user/password@abc-defgd2.us-east-1.rds.amazonaws.com:1521/schema network_link=ec2 flashback_scn=$(echo -e "select to_char(current_scn) from v\$database;" | sqlplus -s / as sysdba 2>/dev/null| grep [0-9]) schemas=SCHEMA-here
```
