# MongoDB_Lab

This is a simple lab for developing and learning with MongoDB database.

## Install MongoDB

To install MongoDB on Ubuntu, you can use the following command:

```
$ sudo apt-get install mongodb
```
After installation, you can start the MongoDB server using the following command:
```
$ sudo systemctl start mongod
```
## Install MongoDB tools
In this lab, we will be using the following MongoDB tools:

* MongoDB Shell: Used to interact with MongoDB from the command line.
* MongoDB Compass: A GUI tool for visualizing and interacting with MongoDB data.
* MongoDB mongosh: A modern CLI for MongoDB with syntax highlighting and autocompletion.

To install these tools, follow the steps below:
1. Download the required .deb package from the MongoDB website or use the following commands:
```
$ sudo dpkg -i mongodb-org-shell_5.0.15_amd64.deb 
$ sudo dpkg -i mongodb-compass_1.36.1_amd64.deb
$ sudo dpkg -i mongodb-mongosh_1.8.0_amd64.deb
```
2. Once installed, you can start using these tools to interact with MongoDB data.

## Using MongoDB Shell
To activate the MongoDB Shell, open a terminal and enter the following command:
```
$ mongo
```
This will start the MongoDB Shell and connect to the MongoDB server. From here, you can use various commands to interact with the MongoDB database, such as **`show dbs`** to display all available databases, **`use <database_name>`** to select a database to work with, show collections to display all collections in the current database, and **`db.<collection_name>.find()`** to search for all documents in a collection.

Before using these commands, ensure that the MongoDB server is running. If you encounter any issues, refer to the MongoDB documentation for more information and troubleshooting tips.



