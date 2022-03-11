# Application structure

Datapreparer is a [spring](https://spring.io) application written in Java. This page gives a basic introduction to the project and
application structure. And a guide to the key components and packages of the application.

## Overview of the application

After cloning the project and setting up the project in your IDE of choice (see here if you haven't done this), you
should see an `app` directory. This is the root directory for the project. You should then see the `src` directory. If
you open this folder, you should open this and see two subdirectories:

- *main* - which contains the source code for the application
- *tests* - which contains the test code for the spring application.

If you navigate into main, you will see two folders: `java` and `resources`. Java contains source code
for the application and resources contain all the static files and scripts required.

## Package overview

Now that you have a general idea of the project structure, the next question is what do all the packages inside *java*
do? Here is a general overview of each package and its function.

| Package     | Function                                                                                                                                       | 
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| app         | Contains the main configuration for spring and application entry point.                                                                        |
| client      |                                                                                                                                                |
| persistence | Contains entities and repositories to handle data persistence and database connections.                                                        |
| transducers | Contains all of the transducers (see what is a transducer?).                                                                                   |
| WebUI       | Web interface for datapreparer.                                                                                                                |
| component   | Contains a series of core components that manage application settings, connection pools, and other shared components.                          |
| service     | Contains all of the services the application uses. In this context, a service is a spring service (essentially a container for business logic) |

## Spring component diagram
_the spring application diagram will go here, will show the data tiers and from there we will give a more complete description_ 

## Data persistence
- connect with Hibernate which is an implementation of JPA
- connection is by JDBC connections string to a H2SQL database
- this can cause means the database is **_in memory_** so all data will be lost once the application is shut down
- This means there is no way to save analysis of data preparation that are in progress.
- Also explain where the properties are to handle the data sources