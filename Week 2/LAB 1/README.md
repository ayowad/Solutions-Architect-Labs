This task will get you acquainted on how to deploy VPC 


Task 1: Deploy VPC using Management console
1. Launch the AWS Management Console
2. Launch a VPC with one public and one private subnets.
3. Create two route table and associate  each one to each subnets
4. Attach an internet gateway to the VPC and a NAT gateway to the private subnet.
5. Lauch a Linux instance into this VPC and attach the subnet
6. Test the network connectivity
7. Perform clean up actions

# Lunched the AWS management console and created a VPC named: projectayo
![image](https://user-images.githubusercontent.com/94347897/168162010-7a5c580a-fb53-485d-b43b-bff9daf37e93.png)

# Test  for network connectivity by ssh into the instance



# Performed cleanup actions by deleting all VPCs and subnets
For guide, you are check the links below:

https://docs.aws.amazon.com/cli/latest/reference/ec2/

https://docs.aws.amazon.com/cli/latest/reference/ec2/describe-vpcs.html

