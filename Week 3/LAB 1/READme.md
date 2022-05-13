Working with IAM management console

Tasks

1. Login to your root account
2. Create an IAM group with S3 read only acess (S3 support).
3. Create an IAM group with EC2 read only acess (EC2 support)
4. Create an IAM group with EC2 full access (EC2 admin)
5. Create 3 IAM users and add to the each group above as descibe below:


user      group          permissions
user1     EC2 support     Read-Only access to Amazon EC2
user2     S3 support      Read-Only access to Amazon S3
user3     EC2 admin       Full access to Amazon EC2 instances

6. Test your design

7. Perform clean up operations


Replicate the process above for  Schulltech organization descrcibed below:


user               group                       permissions
adminstaff         EC2 support          Read-Only access to Amazon EC2
Techstaff          S3 support           Full access to S3
ITexpert           EC2/SDK admin        full access to EC2 and SDK
financialmanager     billingcontrol      Billing Full Access  
financeuser          billinguser          Billing view access


# Created an IAM group with S3 read only acess (S3 support)
![image](https://user-images.githubusercontent.com/94347897/168376424-b1e54dbd-4138-487f-852f-d8ad36de22ff.png)


![image](https://user-images.githubusercontent.com/94347897/168380340-85eb0de3-1aaf-4d87-8ab2-1dff4ce16b41.png)



![image](https://user-images.githubusercontent.com/94347897/168381850-55962752-2669-4e7a-9b4e-01eaaf2ea13c.png)


![image](https://user-images.githubusercontent.com/94347897/168389326-a7a9c945-839a-4856-9f34-9a9288ca2d13.png)

# Clean up performed



https://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_users-self-manage-mfa-and-creds.html


