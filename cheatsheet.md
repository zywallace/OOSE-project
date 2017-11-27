# RESTFUL
## Definition
RESTful Web Services: the browser/server interface
The (http) web server performs all the necessarily central actions
The JavaScript in the browser
1. renders the data pulled from the server and
2. accepts user input which may prompt it to make a request to server
Server is "at rest" until a request comes in from the browser JavaScript

Basic properties:
There is a precise request/response data interface format - JSON for today
Stateless - server knows nothing about state
    
## Terminology
1. a resource is a particular data item to be accessed by REST (e.g. to do entries).
2. a route is a URL suffix to address the resource needed, e.g. /todos/5 to refer to the 5th todo object
3. an endpoint is a route plus an HTTP method (GET/PUT/DELETE/...)

Method:POST/PUT/GET/DELETE....
URL:
Body:JSON Can be any string, but JSON is today's standard
response:Code: Body:JSON 

## Data Mapping
The JSON - Java object: GSON
The Java object - database:
1. "ORM" (Object relational mapping) - framework
2. "POJO" (Plain old Java Object) - manually

## Front End
1. XMLHttpRequest lets JavaScript code itself make HTTP GET/POST/etc requests
2. DOM is the tree representing the HTML of the webpage
3. JavaScript DOM API in the browser lets JavaScript programs manipulate the DOM

## Maven - modern way to build a Java project
declare dependencies - just put in the name/version in the pom.xml 
Key to projects: share a Maven build file to use identical versions of libraries etc - minimize platform-specific bugs.

# UML
