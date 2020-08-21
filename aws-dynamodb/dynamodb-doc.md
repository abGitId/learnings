#### <u>dynamodb cheat sheet</u>

**reference url**
https://docs.aws.amazon.com/cli/latest/reference/dynamodb/create-table.html
https://viastudio.com/creating-an-aws-dynamodb-table-from-the-command-line/

https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DynamoDBLocal.DownloadingAndRunning.html - 

**Starting dynamodb locally** 

```
$ java -Djava.library.path=./DynamoDBLocal_lib -jar DynamoDBLocal.jar -sharedDb
```

**To stop local dynamodb** 

```
clt+c
```

**command to create dynamodb  table using json file locally**
aws dynamodb create-table --cli-input-json file://items-table.json --endpoint-url http://localhost:8000

**command to create dynamodb using json file**

```
$ aws dynamodb create-table --cli-input-json file://items-table.json
```



```
output:
{
    "TableDescription": {
        "AttributeDefinitions": [
            {
                "AttributeName": "Deleted",
                "AttributeType": "S"
            },
            {
                "AttributeName": "Id",
                "AttributeType": "S"
            }
        ],
        "TableName": "Items",
        "KeySchema": [
            {
                "AttributeName": "Id",
                "KeyType": "HASH"
            }
        ],
        "TableStatus": "CREATING",
        "CreationDateTime": "2020-08-20T21:13:45.792000+05:30",
        "ProvisionedThroughput": {
            "NumberOfDecreasesToday": 0,
            "ReadCapacityUnits": 5,
            "WriteCapacityUnits": 5
        },
        "TableSizeBytes": 0,
        "ItemCount": 0,
        "TableArn": "arn:aws:dynamodb:ap-south-1:309212966347:table/Items",
        "TableId": "4d27f30f-9cc2-4e23-ba6e-56ea2adafcc4",
        "GlobalSecondaryIndexes": [
            {
                "IndexName": "Deleted-index",
                "KeySchema": [
                    {
                        "AttributeName": "Deleted",
                        "KeyType": "HASH"
                    }
                ],
                "Projection": {
                    "ProjectionType": "ALL"
                },
                "IndexStatus": "CREATING",
                "ProvisionedThroughput": {
                    "NumberOfDecreasesToday": 0,
                    "ReadCapacityUnits": 5,
                    "WriteCapacityUnits": 5
                },
                "IndexSizeBytes": 0,
                "ItemCount": 0,
                "IndexArn": "arn:aws:dynamodb:ap-south-1:309212966347:table/Items/index/Deleted-index"
            }
        ]
    }
}
```

**#TO fetch list of table for local dynamodb**

```
$ aws dynamodb list-tables --endpoint-url http://localhost:8000
```



```
output:
{
    "TableNames": [items]
}


```

**delete table**

```
$ aws dynamodb delete-table --table-name Items
```

```
output:
{
    "TableDescription": {
        "TableName": "Items",
        "TableStatus": "DELETING",
        "ProvisionedThroughput": {
            "NumberOfDecreasesToday": 0,
            "ReadCapacityUnits": 5,
            "WriteCapacityUnits": 5
        },
        "TableSizeBytes": 0,
        "ItemCount": 0,
        "TableArn": "arn:aws:dynamodb:ap-south-1:309212966347:table/Items",
        "TableId": "4d27f30f-9cc2-4e23-ba6e-56ea2adafcc4"
    }
}
```


