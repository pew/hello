# aws cli queries

## query for instance name, ID, private and public IP

```
aws ec2 describe-instances --output text --query 'Reservations[*].Instances[*].[Tags[?Key==`Name`].Value|[0], InstanceId, PublicIpAddress, PrivateIpAddress]'
```

## query rds instances: multi-az, engine, endpoint address

```
aws rds describe-db-instances --region eu-west-1 --output text --query 'DBInstances[*].[MultiAZ,Engine,Endpoint.Address]'
```
