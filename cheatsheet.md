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

# Git

# UML
UML:
1. Associations
2. Inheritance
3. Composition

# Design Pattern - when/why/how
## Observer
- when: If there is some change which you would want to broadcast to the rest of the program
- why: It decouples subjects and observers, they are only loosely acquainted. More separation of concerns.
- how: Observable(class) class maintain a list of Observers(interface). When an Observable object is updated, it invokes the update() method of each of its Observers to notify that, it is changed.
## Decorator
- when: require dynamic functionality
- why: Decorator pattern achieves a single objective of dynamically adding responsibilities to any object.
- how: delegation - coffee example
## Command
- when:
- why: Encapsulate a request on an object
- how: Invoker(RemoteControl): setCommand() -> Command(interface) -> ConcreteCommand(LightOn, LightOff): receiver.action -> Receiver(Light)
## Adapter
- when: there is an interface, but it isn't quite what you need and you cant change it
- why: make something old look like something new
- how: Target - adapter(implements target) - has an adaptee
## Facade
- when: Provide a unified interface to a set of interfaces in a subsystem
- why: defines a higher-level interface that makes the subsystem easier to use
- how:
## Factories
- when: method creating objects rather than directly invoking new
- why: could be parametric and provide abstraction
## Proxy
- when: a placeholder for another object to control access to it.
- why: skip time consuming methods.
- how: Virtual Proxy Example: only new Image() when show() is called
## Template Method
- when: subclasses have methods that are similar but also have different bits so it cannot be directly lifted to superclass
- why: avoid code duplication
- how: final method(algorithm) use some methods which subclass would implement
## Iterator
- why: it hides the underling kind of collection since its irrelevant to users just iterating over it.
## Composite
- why: print() - an individual item just prints itself, and the composite prints all of its components
- how: menu and submenu
## State - Strategy
- why: get rid of switch/if
- how: define state/strategy class to delegate method in main class and setState() method in main class
## Singleton
- when: a class with only one member
- why: multiple instances can't be created
- how: make constructor private and class holds a static final instance with a getInstance() or enum class
