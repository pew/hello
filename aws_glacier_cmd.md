# aws glacier cmd

## list current jobs
    glacier-cmd --aws-access-key "HERE" --aws-secret-key "HERE" --region us-east-1 listjobs homer
    
## start inventory
    glacier-cmd --aws-access-key "here" --aws-secret-key "here"  --region us-east-1 inventory homer

## get archive
    glacier-cmd --aws-access-key "here" --aws-secret-key "here"  --region us-east-1 getarchive homer Archive_ID
    
## download
    glacier-cmd --aws-access-key "here" --aws-secret-key "here"  --region us-east-1 download homer Archive_ID