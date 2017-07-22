# AWS lambda CodeCommit function, build latest commit

takes the latest commit ID as `sourceVersion`. Just edit `yourCodeCommitRepo` to your own repo name. gg.

```
""" trigger aws codebuild build """
import boto3

client = boto3.client('codebuild')

def lambda_handler(event, context):
    commitid = event['Records'][0]['codecommit']['references'][0]['commit']
    try:
        build = client.start_build(
            projectName='yourCodeCommitRepo',
            sourceVersion=commitid,
            artifactsOverride={
                'type': 'NO_ARTIFACTS'
            }
        )
        return True
    except Exception:
        return False
```