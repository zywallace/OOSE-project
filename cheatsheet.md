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

# Design Principle
## Encapsulate What Varies
- when: for example, encapsulate how you calculate tax
- why: more maintainable code
- how: encapsulate code that may change

## The Data-centric Design / God Class Anti-Pattern
- when: one really fat class doing all the operations and other tiny classes just hold data
- how: push methods from the big class in the center out to the data classes

## The Open-Closed Principle (OCP)
- when: in the use of inheritance 
- why: more reliable
- how: Make code which is open for extending, but closed for modifying. (1) all final and composition (2) only not final those need to be overridden

## Don't Repeat Yourself (DRY)
- why: avoid duplicate code which is hard to maintain

## The Single Responsibility Principle (SRP)
- when: god class
- why: have its focus

## The Liskov Substitution Principle (LSP)
- when: invariant constraint may fail for example:  setHeight should not change weight
- why: A is-a B doesn't indicate A is a subclass of B
- how: make a superclass of A and B 

## The Interface Segregation Principle (ISP)
- when: lots of methods in interface is not useful
- why:  methods are not allocated precisely enough
- how:  turn one interface into many

## Design by Contract and Defensive Programming
Defensive: slow(at runtime) but robust
contract: fast(at compile) but something bad may happen in runtime

# Implementation and Testing
## Implementation
Iteration planning - Prioritizing features, Planning your iterations

Releases and release terminology
version X.Y.Z (e.g. 10.8.3) means major version X, minor version Y, patch version Z.

Implementation Principles
1. Practice Collective Code Ownership
2. Communicate
3. Continuous Integration (CI)
4. Have a coding standard
5. Program in pairs
6. Version Control

## Testing
### Unit Testing - test coverage
### Acceptance testing - BDD
### Integration Testing - CI

# Refactoring
## Methods
1. Extract/Inline Method/class - for too big/small method/class
2. Move Method/Field - wrong place
3. Temp: Inline []- perform cal in place, replace [] with query - get rid of temp, split [] - one var for one purpose
4. Replace Method With Method Object
5. Collapse Hierarchy — combine under-utilized subclass !may violate LSP: Car becomes superclass(Transport) of Plane
6. Replace Inheritance <-> Delegation — I->D(Vector <- Stack) if violate LSP. inheritance is more expressive, delegation is more flexible. D->I(Person<-employee)
7. Encapsulate Field — use getters and setters 
8. Replace Conditional With Polymorphism — replace switch on your own data with dynamic dispatch (Bird interface with implementor)
9. Replace Type Code with State/Strategy - design pattern
10. Introduce Assertion — one tool to help program defensively
11. Replace Parameter With Method Call — don't pass things the callee can get on their own
12. Introduce Parameter Object — If a certain group of parameters is always being passed together, make an object in their own right
13. Form Template Method — Template design pattern
## Anti-pattern
1. Analysis Paralysis — going round and round on planning (overthinking it) without building anything.
2. Bike Shedding — wasting too much time on trivial aspects of an important project
3. Big Ball of Mud — code with poor separation of concerns
4. Input Kludge — input check!
5. BaseBean — don't inherit when relation is not is-a, delegate instead. Related to LSP and replace inheritance with delegation above.
6. Call Super — don't require subclass overrider to call super method, its a bad interface boundary. Note this one is contentious, its a trade-off.
7. Circle-Ellipse Problem — LSP problem
8. Sequential Coupling — methods with an implicit constraint on which one must be called first.
## Fix
1. Duplicated Code - extract method/class
2. Long method - extract methods
3. Long Parameter List - replace parameter with method/introduce parameter object
4. Divergent Change (SRP violation) - extract class
5. Shotgun Surgery: add a new feature needs copy/paste to lots of place - move method/class
6. Feature Envy: Method in one class uses lots of pieces from another class -  Move method
7. Data Clumps: Data that's always hanging with each other (e.g. name/street/zip) - Extract a data class
8. Switch (case) statements - Use inheritance and polymorphism
9. Lazy Class: class does nothing - collapse hierarchy or inline class
10. Speculative generality: Think too much - like 9
11. Message chains - hide delegate
12. Inappropriate Intimacy/Object orgy: directly getting in and munging with the internals of another class - move method
13. Data Class / god class / Data-centric design  - extract method and move
14. Comments — extract method.

# Idioms
1. Consider using static factory methods in place of class constructors
- why: flexibility
- how: use static method and newInstance()
2. Implementing the Singleton Pattern in Java
- why: encapsulation and singleton behavior
3. Minimize Accessibility
Start out with things private and loosen up as needed
- why: encapsulation
4. Be Immutable Whenever Possible
- why:  immutable objects can be shared freely without risk.. Thus they are always thread-safe.
- how:  initialize the object in the constructor and use as many final as possible
5. When Using Inheritance be Clear and Robust or ... Don't Inherit
- why: Inheritance breaks the normal class encapsulation boundary - you are mucking with the superclass' code when you override methods
6. Favor Composition Over Inheritance
- why: a whole-object holding on to (in a field) a part-object. By delegating some methods sent to the whole to the part (forwarding them) we achieve something similar to inheritance minus ability of overriding to change part's behavior. It doesn't violate class encapsulation -- it obeys the OCP
7. Avoid switch whenever possible
- why: this is data-centric design
- how: Let the object do the work instead, as a method. Use some refactoring methods

8. Overriding equals: instance be transitive, reflexive, symmetric, and have a faithful hashCode implemented for it.
9. Use enums instead of int constants
10. Minimize the scope of local variables.
11. Use checked exceptions for things the caller can recover from and unchecked exceptions for things they can't recover from.
12. Reuse existing exceptions built into Java whenever possible.
13. Throw exceptions understandable by the caller only
14. Don't just catch and ignore exceptions

# Design Pattern
## Observer - Loose Coupling
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
## Facade - Least knowledge
- when: Provide a unified interface to a set of interfaces in a subsystem
- why: defines a higher-level interface that makes the subsystem easier to use
- how:
## Factories - Dependency Inversion Principle
- when: method creating objects rather than directly invoking new
- why: could be parametric and provide abstraction/encapsulation
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
