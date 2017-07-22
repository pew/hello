# ec2 AWS IAM policy

Allow to Start, Stop and Creating of new instances for a user if a instance is tagged with `Servicegroup = dev-*`. Everything with `dev-*` is allowed.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "ec2:DescribeInstances",
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "ec2:RunInstances",
                "ec2:StopInstances",
                "ec2:StartInstances"
            ],
            "Resource": [
                "arn:aws:ec2:us-east-1:123456789012:instance/*"
            ],
            "Condition": {
                "StringLike": {
                    "ec2:ResourceTag/Servicegroup": "dev-*"
                }
            }
        }
    ]
}
```

Now the same but only for resources with the exact `development` tag.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "ec2:DescribeInstances",
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "ec2:RunInstances",
                "ec2:StopInstances",
                "ec2:StartInstances"
            ],
            "Resource": [
                "arn:aws:ec2:us-east-1:123456789012:instance/*"
            ],
            "Condition": {
                "StringEquals": {
                    "ec2:ResourceTag/Servicegroup": "development"
                }
            }
        }
    ]
}
```
