# Working with Elastic Load balancing

Tasks: Using AWS CLI,

1. Create an Application Load Balancer
2. Create a Network Load Balancer
3. Create a Gateway Load Balancer
4. Create a Classic Load Balancer
5. Perform clean up operations


NB: You need to launch at least two instances to do this. 

# Create an Application Load Balancer(specified 2 subnets from different availability zones)
aws elbv2 create-load-balancer --name wad-load-balancer 
--subnets subnet-06bd2ce919a8faac6 subnet-00f6accb67c81ba7e 
--security-groups sg-03abd8a568acb5f2e

# output
![image](https://user-images.githubusercontent.com/94347897/169716719-879cd3f3-6080-428e-acb5-bfe8183434c7.png)

# Create a Network Load Balancer
aws elbv2 create-load-balancer 
--name wadnet-load-balancer 
--type network --subnets subnet-00f6accb67c81ba7e

# Output
![image](https://user-images.githubusercontent.com/94347897/169779833-a76aa00e-9a8d-4490-bcab-5a647afdcc83.png)

# Create a Gateway Load Balancer

aws elbv2 create-load-balancer 
--name wadgate-load-balancer 
--type gateway 
--subnets subnet-00f6accb67c81ba7e
# Output
![image](https://user-images.githubusercontent.com/94347897/169782152-1427220c-1482-410d-baaf-7cea3b14a145.png)



Guide
https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/load-balancer-getting-started.html

