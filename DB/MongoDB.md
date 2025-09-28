# MongoDB
MongoDB is a NoSQL database that stores data in documents (like JSON objects) instead of tables and rows like a traditional SQL database.

## Notes
If commands are not found or do not work, you may need to install or update it
The commands and tools used here were tested on Kali Linux (Rolling Edition)

## Port
27017

## Default Database
ace

## Connecting
```bash
mongo <IP>:<Port>
# Connects to the MongoDB server at the specified IP address and port without authentication.
mongo -p -u <Username> <DB>
# Connects to the local MongoDB server, authenticates to <DBname> as <Username>, and prompts for the password.
```

## Basic Commands
```bash
show dbs # Displays all databases on the MongoDB server.
use <DB> # Switches the current session to the specified database.
show collections # Shows all collections in the current database.
db.<Collection>.find().forEach(printjson) # Prints all documents in the specified collection in JSON format.
db.<Collection>.insert({"<Key>":"<Value>"}) # Inserts a new document with the given key-value pair into the specified collection.
```
A one-liner to execute a command at the same time as connecting.
```bash
mongo --port <Port> <DB> --eval "db.<Collection>.find().forEach(printjson)";
# Prints all documents in the specified collection in JSON format.
mongo --port <Port> <DB> --eval 'db.<Collection>.update({"_id": ObjectId("<ObjectID>")}, {$set: {"<Key>": "<Value>"}})'
# Updates the document with the specified _id in the collection, setting <Key> to <Value>.
```
