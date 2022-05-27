# Working with AWS DynamoDB

Task:
1. Create a Table
2. Write Data to a Table Using the Console or AWS CLI
3. Read Data from a Table
4. Update Data in a Table
5. Query Data in a Table
6. Create a Global Secondary Index
7. Query the Global Secondary Index
8. Clean Up actions

# Create a Table
![image](https://user-images.githubusercontent.com/94347897/170791836-19e31cf7-195c-4bd3-9399-f0a7137ab8da.png)

# Write Data to a Table Using the Console
![image](https://user-images.githubusercontent.com/94347897/170792427-32571050-f289-4920-a3b8-557a02ca59a7.png)

# Read Data from a Table
![image](https://user-images.githubusercontent.com/94347897/170792562-bb9e14f0-34a9-44e8-a35d-c0d365eae96f.png)

# Update Data in a Table
![image](https://user-images.githubusercontent.com/94347897/170794099-9052481b-544e-4d4f-8bd8-1ce0d3d64785.png)


# Query Data in a Table
![image](https://user-images.githubusercontent.com/94347897/170793524-27da69e1-d8c8-4656-8438-fd21bda9efeb.png)
![image](https://user-images.githubusercontent.com/94347897/170793540-36d77baa-48e6-4f9a-8ac6-945cf5b3a2ef.png)


# Create a Global Secondary Index using cli
aws dynamodb update-table \
    --table-name schull \
    --attribute-definitions AttributeName=location,AttributeType=S \
    --global-secondary-index-updates \
        "[{\"Create\":{\"IndexName\": \"AlbumTitle-index\",\"KeySchema\":[{\"AttributeName\":\"AlbumTitle\",\"KeyType\":\"HASH\"}], \
        \"ProvisionedThroughput\": {\"ReadCapacityUnits\": 10, \"WriteCapacityUnits\": 5      },\"Projection\":{\"ProjectionType\":\"ALL\"}}}]"




Guide:
https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GettingStartedDynamoDB.html
