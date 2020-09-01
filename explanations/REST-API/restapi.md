# APIs
An API is an Application Programming Interface. It is a way to let software components talk to each other. It's like a menu in a restaurant that states what you can order (what data you can access).

REST stands for Respresentional State Transfer. It is a certain way you can use HTTP protocol. You can create api endpoints (URIS) which are the pages where the user can communicate with the database. Your application can send and receive JSON data to these endpoints to query, modify and create content on your site. 

REST answers 2 questions:

1. Method information is specified in the HTTP verb.

Restful: `DELETE api/users/:id`

Not restful `GET api/users/delete/:id`

2. Scoping information should go in the URI.

DELETE api/users/**:id**

## How REST API works

- Using HTTP methods to send a request. (GET for getting data, POST for creating, PUT for updating, and DELETE for deleting).
- Scoping data will go in the parameter part of the URI.
- It uses common data formats (usually JSON)
