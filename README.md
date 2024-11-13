## Running MongoDB in a Docker Container

### Pull the MongoDB image

```shell
docker pull mongo
```
### Start the MongoDB container

```shell
docker run -d --name mongodb-container -p 27017:27017 mongo
```

### Stop the container

```shell
docker stop mongodb-container
```

### Delete the container and image

```shell
docker rm mongodb-container
docker rmi mongo
```

## Access the MongoDB Shell

### Open a bash shell inside the running MongoDB container

```shell
docker exec -it mongodb-container bash
```

### Start the MongoDB shell

```shell
mongosh
```

## Connect MongoDB to Python

To connect to MongoDB from Python, you need to install the `pymongo` package, as it's not included by default.

### Install pymongo

```shell
pip install pymongo
```

### Connect to MongoDB

```py
import pymongo

# Establish a connection to MongoDB server
client = MongoClient("mongodb://localhost:27017/")

# Create or connect to the database
db = client["hello"]  # If the database doesn't exist, it will be created automatically

# Create or connect to a collection 
collection = db["employees"]
```

## CRUD Operations

### Insert Documents

```py
# Insert a single document
collection.insert_one({})

# Insert multiple documents
collection.insert_many([{}, {}])
```

### Count Documents

```py
count = collection.count_documents({})
print(f"Total documents: {count}")
```

### Retrieve Documents

```py
# Find one document
employee = collection.find_one()
print(employee)

# Find all documents
employees = collection.find()

for employee in employees:
    print(employee)
```

### Update Documents

```py
# Update a single document
collection.update_one()

# Update multiple documents
collection.update_many()

# Replace a document
collection.replace_one()
```

### Delete Documents

```py
# Delete a single document
collection.delete_one()

# Delete multiple documents
collection.delete_many()
```

### Additional Operations

```py
# Find and update a document
collection.find_one_and_update()

# Find and replace a document
collection.find_one_and_replace()

# Find and delete a document
collection.find_one_and_delete()
```

## Closing the MongoDB Connection

```py
client.close()
```











