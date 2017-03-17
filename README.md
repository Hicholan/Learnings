

BACKGROUND

What PRISM? Prism provides guidance to design and 

Build rich, 

Flexible, and 

Easy-to-maintain WPF desktop applications. 

 

Using
design patterns such as Model-View-View Model (MVVM), 

Composite View, and 

Event Aggregator that embody important 

Architectural
design principles helps you create a modular application—using loosely coupled
components that can evolve independently overtime.

Composite
applications typically feature multiple screens, rich user interaction and data
visualization.

These
applications typically interact with multiple back-end systems and services
and, using a layered architecture, may be physically deployed across multiple
tiers.

 

Why Use PRISM? Designing and building rich WPF client
applications that is flexible,

Easy to
maintain and

Evolve
overtime.

 

CLIENT APPLICATION CHALLENGES: 

Application requirement can change
overtime.New Technologies may become available.Ongoing cust feedback during Dev. cycle
may affect requirements.





 

This requires
an architecture that allows individual parts of the application to be developed
independently and tested.

 

Monolithic Style: can lead to an application that is very
difficult and inefficient to maintain (Application in which components are
tightly coupled).

 

Composite Approach: An effective solution is to partition
the application into no. of discrete, loosely coupled, semi-independent
components that can be easily integrated into an application “Shell” to form a
coherent solution.

 

 

 

 

 

 

 

 

 

 

Benefits of Composite approach:

Allows modules to be developed
individually, tested and
deployed by different individual teams.Provides a common shell composed of UI components from various modules that are loosely coupled.Provides reuse and clean separation of concerns between application 





Horizontal
capabilities (Logging and Authentication)

Vertical
Capabilities (Business Functionality)

 

Challenges not addressed by PRISM:

Occasional connectivity and data
synchronizationService and messaging infrastructure designAuthentication and AuthorizationApplication performanceApplication versioningError handling and fault tolerance











 

PREQUISITE:

XAML – Language to define and initialize UI in
WPFData
Binding – UI elements are
connected to Components and Data.Resources – Styles, Data templates and control
templates are created and managed.Commands – How User gestures and input are
connected to controls.User
Controls – Components
that provide custom behavior or custom appearance.Dependency
Properties – Extension to
CLR property, to enable property setting and monitoring in support of data
binding, commands and events.Behaviors: Are objects that encapsulate interactive
functionality that can be easily applied to controls in UI.













 




 

OVERVIEW OF PRISM

 

ARCHITECTURAL GOALS:

Create an application from modules that
can be building, assembled and deployed by independent teams using WPF.Minimize cross team dependencies.Promotes reusability across independent
teams.Increase quality of applications by
abstracting common services.Incrementally integrate new capabilities.









 

PRISM DESIGN GOALS: Is designed around the core
architectural design principles of Separation of Concerns and loose coupling.

 

REUSE: Components and services to be easily developed and tested.EXTENSIBILITY: Application can be extended by managing
component dependencies.FLEXIBILITY: By allowing the application to be easily
updated with new capabilities.TEAM DEVELOPMENT: By allowing separate teams to develop
and deploy different parts of the application independently.QUALITY: Increase the quality of application by allowing common
services and components to be fully tested.









 

TESTING:


 
  
  Name
  
  
  Description
  
 
 
  
  Acceptance Testing
  
  
  Validate the application functionality using user scenarios to
  drive the test requirements. 
  Test can be manual or Automated.
  
 
 
  
  Application Building Exercise Testing
  
  
  Team member build applications consuming the deliverable
  software
  
 
 
  
  Black Box Testing
  
  
  Manual acceptance test perform from the user point of view.
  
 
 
  
  Cross Platform Testing
  
  
  Automated tests are run on multiple platforms.
  
 
 
  
  Globalization Testing
  
  
  Automated tests are run on multiple languages.
  
 
 
  
  Performance Testing
  
  
  Measures how fast a particular aspect of a system performs
  under-load.
  
 
 
  
  Security Review Testing
  
  
  Internal Microsoft security audit standard that cover thread
  models, identifying attack factors and running the code through security
  analysis tools.
  
 
 
  
  Stress Testing
  
  
  Measures ability of the system under extreme loads. Specifically
  looking to drive out issues like memory leaks and threading issues.
  
 
 
  
  White box Testing
  
  
  In-depth source code analysis validating the code standards,
  structure and how it maps to the overall architecture.
  
 
 
  
  UI Automation Testing
  
  
  Limited range of acceptance testing. 
  Driving the application from user perspective.
  
 
 
  
  Unit Testing
  
  
  Validates the implementation of a class
  
 


 

 

 

PRSIM Key Concepts

Modules:


Modules are packages of functionality that
can be developed, tested and deployed independently.  A typical prism application is built from
multiple modules. Modules used to represent specific
business related functionality.Modules can used to encapsulate common
application infrastructure.E.g.: Profile Management, logging and
Exception management.









 

Module
Catalog:

In Composite application, modules must be
discovered and loaded at runtime by the host application.Module catalog is used to specify which
modules are to be loaded, when and in what order.Is used by Module manager and module
loaded components, which are responsible for downloading the modules if they
are at remote.Prism allows module catalog to specify in
code behind as well as XAML.We can implement custom module catalog if
needed.









 

Shell:

Shell is the host of the application, into
which modules are loaded.Shell defines the overall layout and
structure of the application, but it is unaware of the exact modules that it
will host.Shell provides the top-level window or
visual element, which will then host the different UI components provided by
the loaded modules.





 

Views:


Encapsulate the UI for a particular feature or functional area of the application.Views are used in conjunction with MVVM
pattern, which is used to provide clean separation of concern between UI,
presentation logic and data.Views are used to encapsulate UI and
define user interaction behavior.Views uses data binding to interact with
view model classes.







 

View
Models:

Encapsulate application’s presentation logic and state.It defines properties, commands and
events, to which controls in the view can data bind.



 

Model:

Encapsulate application’s business logic and data.And any associated validation and business
rules to ensure data consistency and integrity.



 

Commands:

Encapsulate application functionality in a
way them to be defined and tested.Can be defined as Command Object or
Command Method in VM.PRISM provides delegate command and
Composite command class.





 

 

 

 

Regions:

Local place holders into which views are
displayed.Allow the layout of the application’s UI
to be updated requiring changes to the application logic.Many common controls can be used as
region, allowing views to be automatically displayed within a region, such as
Content control, Items Control, List box or Tab Control.Regions can be located by other components
through the Region Manager component, which uses Region Adapter and Region
Behavior components to coordinate the display of views with specific regions.







 

Navigation:

The process by which the application coordinates
changes to its UI as a result of user’s interaction with the application or
internal application state changes.PRISM support two styles of navigation:
State-Based navigation and View-switching navigation.State based navigation: State of an
existing view is updated to implement simple navigation scenarios.View switching navigation: Uses URI based
navigation mechanism in conjunction with prims regions to allow flexible
navigation schemes to be implemented.







 

Event
Aggregator:

Components in Composite application often
need to communicate with other components and services in the application in a
loosely coupled way.To support this, prism provides Event
Aggregator component which implement Pub - sub mechanism.Allowing the components to publish events
and other components to subscribe the events without requiring reference to
other.Is often used to allow components in
different module to communicate with each other.







 

Dependency
Injection Container:

DI is used throughout Prism to allow
dependencies between components to be managed.DI allows components dependencies to be
fulfilled at runtime and supports extensibility and testability.Prism is designed to work with Unity or
MEF or with any other DI container via service locator.





 

Services:

Services are components that encapsulate
non-UI related functionality, such as logging, exception management and data
access.Services can be defined by the application
or within a module.Services are often registered with DI
container so that they can be located or constructed as required and used by
other components that depend on them.





 

Controllers:

Controllers are classed that are used to
coordinate the construction and initialization of views that are to be
displayed in a region within application UI.Controllers use prism view-switching
navigation mechanism, which provides an extensible URI-based navigation
mechanism to coordinate the construction and placement of views within regions.Application controller patter defines an
abstraction that maps to its responsibility.





Bootstrapper:

Component is used by the application to
initialize the various prism components and services.Used to initialize the DI container to
register any application-level components and services with it.



 

  Te







 

 

 

 

 

 

 

 

 

 

 

 

 

 

Kll;kj;jl;

 

