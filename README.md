
## Introduction

This project is about implementing a REST API in python using Flask as backend for a restaurant system. It provides two interfaces i.e Employee and Customer.

## How to run locally via REST API:

Clone this repository and run the server.py file.

```
>> python server.py

Connecting to sqlite:///fos2.db

```

Now open a new terminal window and run the following command to add the food category dessert.

```
curl -H "Content-Type: application/json" -X POST -d "{\"name\":\"dessert\"}" "localhost:8080/employees/add-food-category"

{"category_id": 1, "category_name": "dessert"}

```

You will see below message.
```
Added successfully

```

Similarly, there are APIs for customer login, customer sign up, view menu etc that have been shown in comments provided in the the server.py file. This app runs with the Endpoint localhost (my computer) that has an IP address '0.0.0.0' (which maps to my computer) and a port 8080.

## Files:

### models.py

Models contains the SQLiteBackend class which holds the engine, session and bootstrap. 

It also contains the Food Category, Food Details, Customer Details, Customer Order Selection, Customer Order Status and Delivery Person classes for the purpose of record keeping. 

It also has the Employee and Customer class that have methods to carry out the processes.

Models also has one function for the session which rollback (in case the commit fails) and close (when the process is complete).  

### core.py

Core contains the controller class which inherites from the SQLiteBackend class and composites from the Employee and Customer classes.

The controller class also includes all the methods from the Employee and Customer classes.

The purpose of the controller class is to mainly connect to the SQLiteBackend class and use the session as well as link the Employee and Customer classes to perform the functions.

### server.py

Server contains the controllor object which connects to the DB through bootstrapping. It is also responsible for creating and running the server.

The employee and customer routes are mapped to their respective functions and the functions call the methods from the Controller class.

The functions in server.py perform a GET, POST, PUT and DELETE requests over HTTP REST and returns results in JSON format.

## Possible improvements

1) Stronger authentication: Authentication is done using customer id which is prone to security issues. We can improve by using a password and encryption techniques.
2) Recommendations: We can analyse a customer's order history and build a recommendation engine.
