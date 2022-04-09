# Application Overview
Datapreparer is an application written in Java Spring and Python. This page gives a basic introduction to the application and project structure. And a guide to the key components and packages of the application.

## Application Directories
If you look at the application repository, you will be greeted with many directories, each containing individual projects which might seem confusing to you. 

![directories](https://i.imgur.com/k7hrQm2.png)

Although it might be overwhelming, these directories are the key components that makes up the datapreparer application. Here is a brief explaination of what each component does. Let's start with `app` directory, as it is the main directory for the application.

### app
The **app** directory contains the main code for the application, which is a Java Spring project. 

This project uses `proguard`, which is an open source command-line tool that shrinks, optimizes and obfuscates Java code. It is able to optimize bytecode as well as detect and remove unused instructions.

You should also see the `src` directory. If you open this folder, you should see two subdirectories:

- *main* - which contains the source code for the application
- *tests* - which contains the test code for the spring application.

If you navigate further into main, you will see two folders: 
`java` and `resources`. Java contains source code
for the application and resources contain all the static files and scripts required.

#### Package overview

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

### D3L
The **D3L** directory contains a python machine learning project used for the data wrangling, it is heavily used in multiple of the transducers so beware when changing files in this directory.

### Metanome 
The `Metanome project` is a joint project between the Hasso-Plattner-Institut (HPI) and the Qatar Computing Research Institute (QCRI). Metanome provides a fresh view on data profiling by developing and integrating efficient algorithms into a common tool, expanding on the functionality of data profiling, and addressing performance and scalability issues for Big Data. 

In short, this directory contains a data profiling tool written in Java. More about this project can be found [here](https://hpi.de/naumann/projects/data-profiling-and-analytics/metanome-data-profiling.html).

### metanome-algorithms
This directory contains another Java project containing several data profiling algorithms for the Metanome platform. The algorithms have been implemented by students of the information systems group at the Hasso-Plattner-Institut (HPI) in the context of the Metanome project.

### sindy
SINDY is a `Scalable INclusion DependencY` algorithm based on Apache Flink described in a BTW'15 paper.
In contrast to the original algorithm in the publication, this directory contains derivatives of SINDY that support n-ary IND discovery and approximate/partial IND discovery.

In short, this directory contains code used for the inclusion dependencies in the **profile transducer**.

### synthEdit
The **synthEdit** directory contains machine learning code for the **transformation transducer**.

### examplesGenerator
The **examplesGenerator** directory contains code used for the **match transducer**.

### saasfront
The **saasfront** directory contains a simple frontend, but the it is not used in the application.