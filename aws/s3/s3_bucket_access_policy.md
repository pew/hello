### AWS S3 access policy

for a single bucket:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListBucket",
                "s3:GetBucketLocation",
                "s3:ListBucketMultipartUploads"
            ],
            "Resource": "arn:aws:s3:::bucketNameHere",
            "Condition": {}
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:*"
            ],
            "Resource": "arn:aws:s3:::bucketNameHere/*",
            "Condition": {}
        },
        {
            "Effect": "Allow",
            "Action": "s3:ListAllMyBuckets",
            "Resource": "*",
            "Condition": {}
        }
    ]
}
```

for multiple buckets:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListBucket",
                "s3:GetBucketLocation",
                "s3:ListBucketMultipartUploads"
            ],
            "Resource": ["arn:aws:s3:::bucketName1",
            			 "arn:aws:s3:::bucketName2",
            			 "arn:aws:s3:::bucketName3"
            			],
            "Condition": {}
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:*"
            ],
            "Resource": ["arn:aws:s3:::bucketName1/*",
            			 "arn:aws:s3:::bucketName2/*",
            			 "arn:aws:s3:::bucketName3/*"
						],
            "Condition": {}
        },
        {
            "Effect": "Allow",
            "Action": "s3:ListAllMyBuckets",
            "Resource": "*",
            "Condition": {}
        }
    ]
}
```