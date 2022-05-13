Task: Create a nondefault VPC using AWS CLI

1. Open your CLI and run a configuration setting
2. Lauch a VPC 
3. Create two subnets (a public and a private subnet)
4. Make your subnet public by creating and attaching an internet gateway
5. Create a security group and add a SSH access from anywhere
6. Lauch an instance into your subnet 
7. Clean Up

# Using the command line interface to configure and lunch a VPC
![image](https://user-images.githubusercontent.com/94347897/168174496-1111ff56-4eab-4172-90c5-6217a8f8c0b1.png)
# Output returned
# vpc-0d5ec364042a829cb

# Created a subnet with the 
aws ec2 create-subnet 
--vpc-id vpc-0d5ec364042a829cb 
--cidr-block 10.0.1.0/24

# Created a second subnet
aws ec2 create-subnet 
--vpc-id vpc-0d5ec364042a829cb
--cidr-block 10.0.0.0/24

# Made the subnet public by creating an internet gateway
aws ec2 create-internet-gateway 
--query InternetGateway.InternetGatewayId 
--output text

# output returned 
igw-1ff7b06a

# Attached the internet gateway to the VPC with the command

aws ec2 attach-internet-gateway 
--vpc-id vpc-0d5ec364042a829cb 
--internet-gateway-id igw-1ff7b06a

# connect to the instance in the public subnet
aws ec2 create-key-pair 
--key-name MyKeyPair 
--query "KeyMaterial" 
--output text > MyKeyPair.pem

aws ec2 create-security-group 
--group-name SSHAccess 
--description "Security group for SSH access" 
--vpc-id vpc-0d5ec364042a829cb
# clean up done

https://docs.aws.amazon.com/vpc/latest/userguide/vpc-subnets-commands-example.html

https://docs.aws.amazon.com/vpc/latest/userguide/vpc-subnets-commands-example-ipv6.html

https://docs.aws.amazon.com/vpc/index.html
