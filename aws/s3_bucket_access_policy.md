### AWS S3 access policy

```
{
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