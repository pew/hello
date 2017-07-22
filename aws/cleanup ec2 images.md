# clean up ami images

saved for later, don't know which one works. I think the last one. Maybe...

```
ec2-describe-images --region eu-west-1 -o self|awk '{print $2}'|grep 'ami-'|sort > /tmp/images
ec2-describe-snapshots --region eu-west-1|awk '{print $13}'|sort > /tmp/snaps
comm -23 /tmp/images /tmp/snaps


ec2-describe-images --region us-east-1 -o self|awk '{print $2}'|grep 'ami-'|sort > /tmp/images
ec2-describe-snapshots --region us-east-1|awk '{print $13}'|sort > /tmp/snaps
comm -23 /tmp/images /tmp/snaps


ec2-describe-images --region us-east-1 -o self --hide-tags|grep BLOCKDEVICEMAPPING|grep 'snap-'|awk '{print $4}'|sort > /tmp/1
ec2-describe-snapshots --region us-east-1 --hide-tags|grep 'snap-'|awk '{print $2}'|sort > /tmp/2
comm -3 /tmp/1 /tmp/2
```
