# aws cli queries

## query for instance name, ID, private and public IP

```
aws ec2 describe-instances --output text --query 'Reservations[*].Instances[*].[Tags[?Key==`Name`].Value|[0], InstanceId, PublicIpAddress, PrivateIpAddress]'
```

## query rds instances: multi-az, engine, endpoint address

```
aws rds describe-db-instances --region eu-west-1 --output text --query 'DBInstances[*].[MultiAZ,Engine,Endpoint.Address]'
```

... sort based on endpoint name:

```
aws rds describe-db-instances --region eu-west-1 --output text --query 'DBInstances[*].[MultiAZ,Engine,Endpoint.Address]'|sort -k 3,3
```

## query rds instance: identifier, multi-az, engine, endpoint (sort by identifier)

```
aws rds describe-db-instances --region eu-west-1 --output text --query 'DBInstances[*].[DBInstanceIdentifier,MultiAZ,Engine,Endpoint.Address]'|sort -h|column -t
```
