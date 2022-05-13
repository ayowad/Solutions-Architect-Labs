Task :  Create a dual Stack VPC and subnets using AWS CLI

Step:
1. Launch a non-default VPC
2. Create two subnets 
3. Create an internet gateway to one of the subnets with route table 
4. Configure an egress-only private subnet
5. Modify the IPv6 addressing behavior of the subnets
6. Lauch an instance into your public subnet
7. Launch an instance into your private subnet
8. Perform clean up operations. 

# Create a non default VPC and 2 subnets
aws ec2 create-vpc 
--cidr-block 10.0.0.0/16 
--query Vpc.VpcId 
--output text

# Output
![image](https://user-images.githubusercontent.com/94347897/168242532-764167b6-7635-4a02-af38-146cb5ca5ff1.png)

# Created a subnet with the following command using the gotten VPC id
aws ec2 create-subnet --vpc-id vpc-0ff14a008a235343d --cidr-block 10.0.1.0/24
# Output
![image](https://user-images.githubusercontent.com/94347897/168244124-90edddba-d5b9-4d72-8add-1d4f8ab280b6.png)

# Created another subnet with this command 
aws ec2 create-subnet 
--vpc-id vpc-0ff14a008a235343d 
--cidr-block 10.0.0.0/24
# Output
![image](https://user-images.githubusercontent.com/94347897/168244652-50c3e999-62b1-486b-8ec8-8d6d33dd7b90.png)

# created internet gateway 
aws ec2 create-internet-gateway 
--query InternetGateway.InternetGatewayId 
--output text
# output
igw-07cf2617bc5d3b45f

#attached internet gateway to the VPC
aws ec2 attach-internet-gateway 
--vpc-id vpc-0ff14a008a235343d 
--internet-gateway-id igw-07cf2617bc5d3b45f

# Egress-only subnet configured



aws ec2 describe-subnets 
--filters "Name=vpc-id,Values=vpc-0ff14a008a235343d" 
--query "Subnets[*].{ID:SubnetId,CIDR:CidrBlock}"

aws ec2 associate-route-table  
--subnet-id subnet-0b521d9ba61d3a46b 
--route-table-id rtb-0b07a2847375d7a94
#output
![image](https://user-images.githubusercontent.com/94347897/168247337-236b6798-e1a3-4794-a4f4-402e65cfc51d.png)
![image](https://user-images.githubusercontent.com/94347897/168248044-0093e9ff-34b0-4e26-9d6e-0aec12379cd4.png)
![image](https://user-images.githubusercontent.com/94347897/168248973-b85ee4f4-c27a-4169-882c-b200a1fb69d7.png)

# Modify IPv6 addressing behavior of the subnets with the below command
aws ec2 modify-subnet-attribute 
--subnet-id subnet-0b521d9ba61d3a46b 
--map-public-ip-on-launch


# Lauch an instance into your public subnet
aws ec2 create-key-pair 
--key-name MyKeyPair 
--query "KeyMaterial" 
--output text > MyKeyPair.pem

# Launch an instance into your private subnet
aws ec2 create-security-group --group-name SSHAccess 
--description "Security group for SSH access" 
--vpc-id vpc-0ff14a008a235343d

![image](https://user-images.githubusercontent.com/94347897/168251052-1de67321-63d4-4ee9-ae75-6c4c5568662d.png)


image-id ami-a4827dc9 
--count 1 
--instance-type t2.micro 
--key-name MyKeyPair 
--security-group-ids sg-e1fb8c9a 
--subnet-id subnet-0b521d9ba61d3a46b


# Final output
![image](https://user-images.githubusercontent.com/94347897/168255840-15051a0f-bbe8-4ae0-80ab-30968b8a4347.png)


# Perform clean up operations



https://docs.aws.amazon.com/vpc/latest/userguide/vpc-subnets-commands-example.html

https://docs.aws.amazon.com/vpc/latest/userguide/vpc-subnets-commands-example-ipv6.html

https://docs.aws.amazon.com/vpc/index.html
