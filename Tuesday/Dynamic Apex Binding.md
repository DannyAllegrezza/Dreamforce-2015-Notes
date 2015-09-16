## Dynamic Apex Binding:
Presentation from Fronde

##Part 1 Design Patterns
# Factory Pattern
 3 Categories
  
- Creational - object creation
- Structural - relationships between objects
- Behavioral - communication between objects

Factory Pattern
Creational
Logic Isolation
Centralize Object creation logic
- interface
- class hierarchy

/DFDemo1/v1/*

##What is a custom setting?
- Thin object
- configurable in real time
- no need to query
- promotes testing

Kust vs Hierarchy Custom settings

### List Type
- store key value pair
- application/code settings
- list/map containers
- .getAll() method

### Hierarchy Type 
- User/Profile based
- Global settings
- One set of results
- .getInstance() method

## Key benefits
- Manage the change quickly, because you are giving some of the control to the administrators. You can use it for feature toggles. Promotes code reuse.

### Schema namespace
- runtime metadata query
- useful for dynamic apex
- get object configuration info
- special accessor methods.


##Demo 2 of custom settings
You can use something like 
```Access_settings__c.getInstance().getAccount__c
```
##What is Dynamic Binding?
- Compile-time vs Runtime
- Tightly coupled vs Loosely coupled
- Classes vs Interfaces
- Types vs Objects

System.Type Class

//TODO: Grab the rest of this chat from GitHub/Salesforce. Needed to jump into Docker session.
