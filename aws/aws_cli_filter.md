# aws cli filter
## filter name
finds all `*sup*` instances

```
aws ec2 describe-instances --filters Name=tag:Name,Values=*sup*
```
