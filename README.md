# Solutions-Architect-Labs
# opened the aws CLI
# created the s3 bucket with the below command
aws s3 mb s3://wad-buck
# confirmed the bucket was successfully done with the below command
aws s3 ls
# check to see the bucket content with the below command
aws s3 ls s3://wad-buck
![image](https://user-images.githubusercontent.com/94347897/161334700-3a53242a-0d56-49cf-94c0-3886dba6f16f.png)
to download Object from your S3 bucket the following code was run
aws s3 cp demo s3://wad-buck/wad-buck/newdemo

# Delete object in bucket
asw s3 rb s3://wad-buck/demo
# Removed bucket by the following command
aws s3 rb s3://wad-buck
# Check that the bucket was deleted with the below command
aws s3 ls
