# Working with placement Groups using AWS CLI

Tasks:
1. Create a placement group
2. Tag a placement group
3. Launch instances in a placement group
4. Describe instances in a placement group
5. Change the placement group for an instance
6. Delete a placement group

# Created a placement group named wad-grp and using the cluster placement strategy, it applies with a tag key of Purpose and value Production 
aws ec2 create-placement-group 
--group-name wad-grp 
--strategy cluster 
--tag-specifications 'ResourceType=placement-group,Tags={Key=purpose,Value=production}'

# Output
![image](https://user-images.githubusercontent.com/94347897/169662880-bfb9293b-cfdf-4464-80ec-0228b83d7b0f.png)
# Tag the created placement group
aws ec2 create-tags 
--resources pg-06f3f6c49625237e5 
--tags Key=True-Light,Value=l-123

# Launched instances in a placement group
aws ec2 run-instances 
--placement "GroupName = wad-grp"

# Describe instances in a placement group
aws ec2 describe-placement-groups \
--group-name wad-grp

# output
![image](https://user-images.githubusercontent.com/94347897/169667280-4a884a06-fbcd-4628-974e-5cab8b7de57e.png)

# Change the placement group for an instance(Instance stopped first)
aws ec2 modify-instance-placement 
--instance-id i-0123a456700123456 
--group-name MySpreadGroup

# Delete a placement group
aws ec2 delete-placement-group 
--group-name wad-grp


Guide:
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html#using-placement-groups
