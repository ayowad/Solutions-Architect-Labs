# Working with EC2 instance using the AWS CLI / Programmable access

Tasks:

1. Using your default vpc, find the public subnet
2. Create a security group
3. Launch an instance with a web server with termination protection enabled
4. Monitor Your EC2 instance; view the types of metrics that are collected for an EC2 instance
5. Modify the security group that your web server is using to allow HTTP access
6. Resize your Amazon EC2 instance to scale


Guide
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/terminating-instances.html


https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-resize.html

# Using default VPC, created a security group

aws ec2 create-security-group
--group-name ayowad
--description "Secure group for Wadtech"
--vpc-id vpc-06d93b8d93dba8093

# output
{
    "GroupId": "sg-08a16aea2460554cb"
}

# Add rule to all ssh
aws ec2 authorize-security-group-ingress
--group-id sg-08a16aea2460554cb
--protocol tcp --port 22 --cidr 0.0.0.0/0

# output

{
    "Return": true,
    "SecurityGroupRules": [
        {
            "SecurityGroupRuleId": "sg-08a16aea2460554cb",
            "GroupId": "sg-0395cd9e64df97adc",
            "GroupOwnerId": "p	084338663469",
            "IsEgress": false,
            "IpProtocol": "tcp",
            "FromPort": 22,
            "ToPort": 22,
            "CidrIpv4": "0.0.0.0/0"
        }
    ]
}


# Enabled termination protection
aws ec2 run-instances 
--image-id i-00f3f065d653358a7 
--count 1 --instance-type t2.micro 
--security-group-id sg-08a16aea2460554cb 
--subnet-id subnet-0893dbbdbec76d63f
