summary: Clean Architecture
id: understand-the-clean-architecture
categories:configuration
tags: clean-architecture
status: Published 
authors: LJ Group


# Clean Architecture


## Overview 
Duration: 1

### In this tutorial you’ll learn the basics of Clean Architecture, including: 

![alt-text-here](assets/clean-architecture/Clean-Architecture-graph.jpg)

- What Clean Architecture is
-The Dependency Rule
- Entities
- Use Cases
- Interface Adapters
- Frameworks and Drivers
- How do the layers interact?
- Conclusion


## What Clean Architecture is
Duration: 1

Clean architecture is a mode of organization and architecture that emphasizes the separation of responsibilities and the decoupling of business functionalities from tools such as frameworks and databases.

The objectives of clean architecture are as follows:

   - Make code independent of frameworks
   - Make the code testable
   - Make the code independent of the user interface
   - Make the code independent of the database
   - Make the code independent of external services


## The dependency rule
Duration: 2

The rule that governs clean architecture is the dependency rule. The dependency rule states that a lower layer must not know anything about an upper layer. Classes, functions, variables of an upper layer must not be mentioned in a lower layer. There can only be a dependency from an upper layer to a lower layer. This is the direction of the arrow in the figure.

The objective here is simple. To ensure that changes to the upper layers do not have any impact on the lower layers. We can therefore change the framework, the database, without having to touch the business functionalities.



## The Entities
Duration: 2

Entities encapsulate Enterprise wide business rules. An entity can be an object with methods, or it can be a set of data structures and functions. It doesn’t matter so long as the entities could be used by many different applications in the enterprise.

If you don’t have an enterprise, and are just writing a single application, then these entities are the business objects of the application. They encapsulate the most general and high-level rules. They are the least likely to change when something external changes. For example, you would not expect these objects to be affected by a change to page navigation, or security. No operational change to any particular application should affect the entity layer.


## Uses Cases
Duration: 2

The software in this layer contains application specific business rules. It encapsulates and implements all of the use cases of the system. These use cases orchestrate the flow of data to and from the entities, and direct those entities to use their enterprise wide business rules to achieve the goals of the use case.

We do not expect changes in this layer to affect the entities. We also do not expect this layer to be affected by changes to externalities such as the database, the UI, or any of the common frameworks. This layer is isolated from such concerns.

We do, however, expect that changes to the operation of the application will affect the use-cases and therefore the software in this layer. If the details of a use-case change, then some code in this layer will certainly be affected.



## Interface Adapters
Duration: 3

The software in this layer is a set of adapters that convert data from the format most convenient for the use cases and entities, to the format most convenient for some external agency such as the Database or the Web. It is this layer, for example, that will wholly contain the MVC architecture of a GUI. The Presenters, Views, and Controllers all belong in here. The models are likely just data structures that are passed from the controllers to the use cases, and then back from the use cases to the presenters and views.

Similarly, data is converted, in this layer, from the form most convenient for entities and use cases, into the form most convenient for whatever persistence framework is being used. i.e. The Database. No code inward of this circle should know anything at all about the database. If the database is a SQL database, then all the SQL should be restricted to this layer, and in particular to the parts of this layer that have to do with the database.

Also in this layer is any other adapter necessary to convert data from some external form, such as an external service, to the internal form used by the use cases and entities.


## Frameworks and Drivers
Duration: 2

The outermost layer is generally composed of frameworks and tools such as the Database, the Web Framework, etc. Generally you don’t write much code in this layer other than glue code that communicates to the next circle inwards.

This layer is where all the details go. The Web is a detail. The database is a detail. We keep these things on the outside where they can do little harm.



## How do the layers interact?
Duration : 2
The most observant among you will have noticed the small diagram at the bottom right of the figure. It explains, as an example, the interaction between an Interface adapters layer controller (Interface adapters) and a use case.
![alt-text-here](assets/clean-architecture/clean-architecture-flow-of-control.png)

Recall the master rule that says that an upper layer can have dependencies in the lower layers, but not the other way around. For example, a controller can have a use case as a dependency, but not the other way around.

In the case where a lower layer needs an upper layer to perform a task, a use case that for example needs to store something in the database, an interface is defined in the lower layer (use case), which will be implemented by the upper layer (the one in the database). This avoids creating a dependency with the upper layer. 

This is illustrated by the diagram at the bottom right of the figure. The controller depends on the use case, through the Use Case Input Port interface. This interface is implemented by Use Case Interactor, which implements the functionality. The Interactor also needs the presenter that belongs to the top layer. So an interface is created in the Use Case Output Port layer, on which the interactor will depend. The Use Case Output Port interface will be implemented by the presenter in the Interface adapters layer. The presenter will be injected later in the interactor when the interactor is instantiated.


## Conclusion 
Duration: 2

The clean architecture makes it possible to build well-structured applications, each part having a well-defined perimeter and role. The code is decoupled from details such as frameworks and databases. It is not mandatory to implement all the layers of the figure. However, a layer for business functionalities (use cases) and a layer for interface adapters (interface adapters) are required. Tools such as the framework used or the database are details. They are located in an upper layer. The upper layers can have dependencies in the lower layers, but the lower layers must not have dependencies, references in the upper layers. 


### Contact Us

We assure you that you will not find any issue with this Clean Architecture tutorial. But if there is any mistake or error, please contact us.

[LJ Group - Our site](https://www.ljgroup.fr)
